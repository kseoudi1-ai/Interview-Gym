# Interview Gym v1.0.0 — Release Candidate Notes

Status: Release preparation only. This is not a production release.

## Baseline
- Verified source commit: 942b393d17fabd8a5f7226c3ad96af362317a6aa
- Verified Staging deployment run: GitHub Actions run #49 (user-provided screenshot)
- Diagnostic verification: HTTP 200; allowed=true; code=would_be_allowed
- End-to-end interview and Gemini evaluation: reported successful by the project owner.
- Production and Cloudflare Pages were not deployed as part of this Staging deployment.

## Included baseline
- Frontend: index.html
- Worker: cloudflare-worker/worker.js
- Worker configuration: cloudflare-worker/wrangler.jsonc
- GitHub Actions workflows and project source at the baseline commit.

## Changes validated in this preparation window
- Protected manual Staging Worker deployment workflow.
- Fixed YAML quoting in the rollback command.
- Staging Worker deployment and diagnostic smoke test passed.

## Known limitations / not yet certified
- Rollback command has not been exercised in a controlled test.
- A real Gemini evaluation was reported successful, but no API usage/cost telemetry was independently inspected.
- Cloudflare account settings, Worker secrets, environment variables, and external service configuration are not included in this Git source snapshot.
- No Production release has been approved or deployed.

## Restore procedure (source baseline)
1. Keep the current Production and Staging services unchanged while investigating an incident.
2. Identify the last known-good Git commit or backup branch.
3. Create a dedicated restore branch from that exact commit.
4. Review the diff and run the repository checks.
5. Deploy to Staging only using the protected manual workflow.
6. Verify the Worker diagnostic endpoint and a complete interview/evaluation flow.
7. Obtain explicit approval before any Production deployment.
8. Record the restored commit and create a new release entry; do not rewrite historical tags.

## Retention policy
- Retain the latest five approved, immutable release tags.
- Do not delete a tag that is the current Production version or is needed for an active rollback.
- Keep source backups separate from release tags.
- Secrets must remain in GitHub/Cloudflare secret stores and must never be committed.

## Release gate
Do not create or announce v1.0.0 as a production release until:
- a complete source/configuration backup is verified,
- rollback is validated safely,
- release checks pass,
- Production deployment is explicitly approved.
