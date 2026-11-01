# quacko-status

Uptime monitor for Quacko. Every 5 minutes a GitHub Action checks each target from outside
our network; a target that fails 3 checks in a row opens a **DOWN** issue assigned to the
on-call person (GitHub emails them), and the issue closes itself with a comment when the
target recovers.

- Targets: the `MONITOR_TARGETS` repository secret, one `name|url` per line.
- On-call: `ONCALL` in [`.github/workflows/monitor.yml`](.github/workflows/monitor.yml).
  Alerts arrive at that GitHub account's notification email.
- Open issues = what is down right now. Closed issues = outage history.

GitHub's scheduler can run a few minutes late, so expect an alert 5–15 minutes after a
real outage.
