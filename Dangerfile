# Sometimes it's a README fix, or something like that - which isn't relevant for
# including in a project's CHANGELOG for example
declared_trivial = github.pr_title.include? "#trivial"

# Make it more obvious that a PR is a work in progress and shouldn't be merged yet
warn("PR is classed as Work in Progress") if github.pr_title.include? "[WIP]"

# Warn when there is a big PR
warn("Big PR") if git.lines_of_code > 500

swiftlint.lint_files inline_mode: true

xcode_summary.ignored_files = 'Pods/**'
xcode_summary.inline_mode = true


github.dismiss_out_of_range_messages

jira.check(
  key: ["RD"],
  url: "https://myjira.atlassian.net/browse",
  search_title: true,
  search_commits: true,
  fail_on_warning: false,
  report_missing: true,
  skippable: true
)

commit_lint.check
commit_lint.check warn: :all
