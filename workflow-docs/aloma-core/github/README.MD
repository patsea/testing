# Automated GitHub Connector Release Workflow

**Automates the end-to-end process of discovering, tagging, and releasing connector repositories in GitHub, including version calculation and connector image updates. Ideal for teams managing multiple connector repositories who want to streamline CI/CD and release management using ALOMA's automation platform.**

---

## What This Workflow Does

This workflow orchestrates the full release lifecycle for GitHub connector repositories. It automatically discovers all relevant repositories, filters for connector projects, fetches their latest tags, calculates the next semantic version, creates new tags and releases, and updates connector images. The process is fully automated and integrates directly with GitHub via API, ensuring consistent and reliable releases across multiple repositories.

---

## Workflow Steps

| Step Name                         | Trigger Condition                                                                                          | Action                                                         |
|------------------------------------|-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| find all connector repositories    | `{ "release": "connectors" }`                                                                             | Lists all organisation repositories via GitHub API             |
| filter connector repositories      | `{ "repos": { "request": Array } }`                                                                       | Filters repositories to those starting with 'connector-'       |
| fetch repository tag               | `{ "repos": Array }`                                                                                      | Fetches latest tags for each connector repository              |
| tag with new release               | `{ "repos": null, "tags": Object }`                                                                       | Creates new GitHub release tag for each repository             |
| classify commit in main            | `{ "ref": "refs/heads/main", "repository": { "name": String }, "head_commit": { "id": String }, "organization": Object }` | Determines if commit triggers a release, sets release metadata |
| get latest tag                     | `{ "release": { "latest": null } }`                                                                       | Fetches latest tag for a specific repository                   |
| calc next release version          | `{ "release": { "latest": Object, "next": null } }`                                                       | Calculates next semantic version for release                   |
| create tag                         | `{ "release": { "next": String, "tagged": null } }`                                                       | Creates new GitHub tag for the release                         |
| create release                     | `{ "release": { "tagged": { "ref": String } } }`                                                          | Publishes new GitHub release                                   |
| check release done                 | `{ "release": { "released": { "url": String } } }`                                                        | Marks release as complete                                      |
| update connector image             | `{ "build": { "type": "connector", "connectorId": String, "image": String } }`                            | Updates connector image via API                                |
| connector image update successful  | `{ "connector": { "update": { "status": 200 } } }`                                                        | Marks connector image update as successful and completes task   |
| complete                           | `{ "repository": Object }`                                                                                | Completes task on repository event expiry                      |

---

## Integrations used in example

- [GitHub API](https://docs.github.com/en/rest) (via `github.com` connector)
- [ALOMA CLI](https://docs.aloma.io/cli/installation)

---

## Setup Instructions (CLI)

<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-bash">
# 1. Clone the repository and enter the workflow directory
git clone &lt;repository-url&gt;
cd &lt;workflow-directory&gt;

# 2. Update deploy.yaml with your connector keys and secrets (see below)

# 3. Deploy the workflow
aloma deploy deploy.yaml

# 4. (If required) Complete OAuth for GitHub
aloma connector list
aloma connector oauth &lt;connector-id&gt;

# 5. Test with a sample task
aloma task new "test connector release" -f example.json

# 6. View task logs
aloma task log &lt;task-id&gt; --logs --changes
</code></pre>
</div>

---

## Configuration (connectors + secrets/env)

Edit `deploy.yaml` and update the following configuration as needed:

<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-yaml">
connectors:
  - connectorName: "github.com"

# No secrets are required by default for this workflow.
# If your GitHub connector requires a personal access token or OAuth, configure it via the ALOMA CLI.
</code></pre>
</div>

### To find these values:

- **GitHub OAuth/Token**: Create a [GitHub personal access token](https://github.com/settings/tokens) with `repo` scope, or use OAuth via `aloma connector oauth <connector-id>`.
- **Organisation Name**: Used in the workflow as `"pers3verance"`. Replace in step code if targeting a different org.

---

## Sample Task (JSON)

<div>
<button onclick="navigator.clipboard.writeText(this.nextElementSibling.innerText)">Copy</button>
<pre><code class="language-json">
{
  // Example task payload for triggering the workflow.
  // Replace with actual webhook event or manual trigger as needed.
}
</code></pre>
</div>

*Alternative: see `example.yaml` in repository.*

---

## Troubleshooting

- **Missing or invalid GitHub connector:** Ensure the `github.com` connector is configured and authenticated. Use `aloma connector list` and `aloma connector oauth <connector-id>`.
- **API permission errors:** Confirm your GitHub token or OAuth app has `repo` and `workflow` permissions.
- **No repositories found:** Check organisation name in step code (`org: 'pers3verance'`). Update to your GitHub org if needed.
- **Release/tag not created:** Ensure the repository allows releases and the workflow has push access.
- **Connector image update fails:** Verify endpoint and authentication for the connector image update API.
- **Task not progressing:** Use `aloma task log <task-id> --logs --changes` to debug step-by-step.
- **Webhook not triggering:** Confirm webhook is registered and payload matches trigger conditions.

---

## Support

If you encounter issues, check the [ALOMA documentation](https://docs.aloma.io/) or join the Community support Slack channel: alomasupport.slack.com.
