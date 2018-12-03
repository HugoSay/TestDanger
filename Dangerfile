# Make it more obvious that a PR is a work in progress and shouldn't be merged yet
warn("PR is classed as Work in Progress") if github.pr_title.include? "[WIP]"

# Warn when there is a big PR
warn("Big PR") if git.lines_of_code > 500

# Runs swiftlint on the project and adds comment to the PR if any rule is broken
swiftlint.config_file = '.swiftlint.yml'
swiftlint.lint_files inline_mode: true

# Adds comments to the PR if it creates any waring
xcode_summary.ignored_files = 'Pods/**'
xcode_summary.inline_mode = true
xcode_summary.report 'errors.json'

# Creates links to all jira tickets referenced in the pull request
jira.check(
  key: ["RD"],
  url: "https://finalcad.atlassian.net/browse",
  search_title: true,
  search_commits: true,
  fail_on_warning: false,
  report_missing: true,
  skippable: true
)

# Checks that the commit is complying to the commit guidelines :)
commit_lint.check warn: :all

# Only adds comments for files that are affected by the pull request
github.dismiss_out_of_range_messages
