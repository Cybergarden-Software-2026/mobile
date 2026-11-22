# Repository instructions for agents

## Git and production deployments

1. **Treat `main` as the production branch.** In the backend and web dashboard repositories, updates to `origin/main` trigger production deployment after checks pass. Apply the same branch and review rules here. Check the mobile release workflow for its actual deployment behavior.
2. **Never push directly to `main`.** Push your feature branch and submit changes through a pull request targeting `main`.
3. **Create a feature branch before editing.** Start new work from the latest `origin/main` on a branch named `feature/<short-kebab-case-name>`, such as `feature/update-incident-filters`. Never use `codex/` or `claude/` as a branch prefix.
4. **Review the full pull request diff before merging.** Compare the latest version of the pull request against current `main`, confirm that every change belongs to the task, and verify that the applicable checks pass. Repeat the review if the pull request changes.

## API contract and cross-repository changes

1. **Read [API.md](API.md) before editing.** Follow its routes, request and response schemas, authentication, and error behavior. Check the owning repository when implementation status is unclear. Use the shared API contract across `backend`, `frontend-web` and `mobile`. The backend owns the mobile HTTP endpoints.
2. **Keep the contract current.** When you add, change, or document an API capability, update `API.md` in the same change. Identify the owning repository and mark the capability `Implemented` or `Not implemented`. Mark it `Implemented` only when the owner has the behavior in its code and you have verified it. Label demo support separately. Keep the contract copies in affected repositories in sync for approved cross-repository changes.
3. **Get explicit approval for cross-repository API dependencies.** If the requested task needs a missing or changed API capability in another repository, tell the user which repository owns it, which routes or behaviors must change, and why the work depends on them. Ask for approval and wait for it before editing files or implementing any part of the task. While waiting, limit work to read-only investigation and a proposed plan.
