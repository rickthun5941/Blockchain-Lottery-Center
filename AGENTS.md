# Repository Guidelines

## Project Structure & Module Organization
- `contracts/` holds on-chain Solidity sources; mirror related tests in `test/unit` or `test/integration`.
- Front-end apps live under `apps/`, shared TypeScript utilities in `packages/`, automation scripts in `scripts/`, and static assets in `assets/`.
- Long-form docs belong in `docs/`. Call out any new top-level directory in your PR description so the repository map stays current.

## Build, Test, and Development Commands
- `pnpm install` — bootstrap dependencies after cloning or switching branches.
- `pnpm hardhat compile` — compile Solidity contracts.
- `pnpm hardhat test [--grep "..."]` — run the default Mocha/Chai suite; use `--grep` to target cases.
- `pnpm hardhat node` — launch a local Hardhat network for manual testing.
- `pnpm lint` — lint TypeScript/React sources; run with `--fix` before opening a PR.

## Coding Style & Naming Conventions
- Solidity: include SPDX headers, indent with four spaces, name contracts in UpperCamelCase, interfaces with an `I` prefix, and libraries with a `Lib` suffix.
- TypeScript/React: two-space indentation, camelCase variables, PascalCase components, kebab-case utility filenames.
- Formatting is enforced through repository-level `.prettierrc` and `.eslintrc.*`; run `pnpm lint --fix` when updating front-end or shared packages.

## Testing Guidelines
- Use Hardhat’s Mocha/Chai stack; name specs `*.spec.ts` and co-locate unit tests under `test/unit`, scenarios under `test/integration`.
- Target ≥80 % statement coverage and document new fixtures in `docs/testing.md`.
- Run `pnpm hardhat coverage` for protocol-impacting changes and guard fork-dependent tests with `process.env.NETWORK`.

## Commit & Pull Request Guidelines
- Follow Conventional Commits (`feat:`, `fix:`, `chore:`, `refactor:`) with lines ≤72 characters; reference issues via `Refs #123`.
- PRs must summarize scope, list testing evidence, attach UI screenshots when relevant, and flag any migrations or coordination needs.
- Ensure automated checks pass and tag at least one domain owner (contracts, frontend, or DevOps) for review.

## Security & Configuration Tips
- Never commit `.env*` files or private keys; load secrets through environment variables.
- Run `pnpm audit` for new dependencies and document external protocol integrations in `docs/SECURITY.md`.
- Schedule `slither` or equivalent analysis for high-risk contract changes.
