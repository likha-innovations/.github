# GitHub Free setup

## Share the templates

This checkout is the organization's `.github` repository. Its root `PULL_REQUEST_TEMPLATE.md` is a supported location for the default pull request template. The issue forms currently reside in the root `ISSUE_TEMPLATE/` folder at the team's request. GitHub requires shared issue forms and `config.yml` in `.github/ISSUE_TEMPLATE/` inside this repository, so move the three `.yml` files there before expecting them to appear. Merge the files into the default branch. The organization `.github` repository must be **public** for GitHub to use its defaults, including in private repositories. Do not put secrets in it.

Repositories with their own issue templates or issue template configuration replace the entire shared issue template folder. A repository with its own pull request template uses that template instead. To customize a repository, copy the issue forms to `.github/ISSUE_TEMPLATE/` and the pull request template to the repository root, then edit them. Enable Issues in each repository where needed. The issue forms do not require custom labels, and blank issues remain available for other work.

The older Markdown files in the root `ISSUE_TEMPLATE/` and `PR_TEMPLATE/` folders are not in the shared default issue-form and automatic pull-request-template locations.

## Protect `main` in public repositories

GitHub Free supports repository branch rulesets for public repositories, but not private repositories. Organization-wide rulesets require GitHub Team or Enterprise. Repeat these steps in each **public** repository:

1. Open the repository's **Settings → Rules → Rulesets** as a repository administrator.
2. Choose **New ruleset → Import a ruleset** and select `rulesets/protect-main.json` from this checkout.
3. Review the target (`main`), enforcement (`Active`), rules, and empty bypass list, then create it. If the default branch has another name, change the target before saving.
4. Verify that a direct push to `main` is rejected and that a pull request can merge after another person approves it and review conversations are resolved.

The ruleset requires a pull request and one approval, dismisses stale approvals after new commits, blocks force pushes and deletion, and grants no bypass. It does not enforce that the project lead specifically approves or merges: request the lead's review as a team practice. The author cannot approve their own pull request, so the lead's own changes need another reviewer. An administrator can change or disable the ruleset, so restrict admin access to trusted maintainers.

Configure required status checks separately for each repository after its CI workflows have run and the correct checks appear; check names differ across projects. Do not require a nonexistent check or merges can be blocked.

## Private repositories on Free

GitHub Free cannot enforce this ruleset on private repositories. To prevent direct pushes without paying, give contributors **Read** or **Triage** access instead of Write, Maintain, or Admin, and have them propose changes from personal-account forks if private forking is allowed. GitHub Free does not allow private forks into an organization. A trusted maintainer with write access reviews and merges pull requests; that maintainer can still push directly, so the no-direct-push rule for them is procedural. Verify organization base permissions, team grants, outside collaborators, and private-fork settings: higher grants override the base permission. If private forks are unavailable, a trusted maintainer must create branches and apply contributions, or GitHub Team is needed for enforced branch rules. Do not make a private repository public merely to enable protection without considering what its history exposes.

References: [Default community files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file), [repository rulesets](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-rulesets/managing-rulesets-for-a-repository), [organization rulesets](https://docs.github.com/en/organizations/managing-organization-settings/creating-rulesets-for-repositories-in-your-organization), and [repository roles](https://docs.github.com/en/organizations/managing-user-access-to-your-organizations-repositories/managing-repository-roles/repository-roles-for-an-organization).
