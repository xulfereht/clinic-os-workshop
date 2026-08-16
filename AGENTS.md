# ClinicOS workshop bootstrap

This template supports additive, agent-neutral tracks.

- `CLINIC_WORKSHOP_PROFILE=windows-native`: normal Windows terminal, remote-only ClinicOS infra.
- `CLINIC_WORKSHOP_PROFILE=codex-cloud`: optional Codex Cloud fallback.
- Profile unset: existing Claude Code + Codespaces/macOS/WSL workshop flow.

Never infer the track from the agent name. Read the environment variable first.

If `package.json` is absent, this is the pre-bootstrap template. Follow the HQ device-authorization
flow described in `README.md`, install the issued starter into this repository, then read the
starter's replacement `AGENTS.md` before continuing. Claude Code instead continues through the
starter's replacement `CLAUDE.md`; both converge on `.agent/AGENT_RUNTIME.md`.

For `windows-native` or `codex-cloud`:

- do not run local D1, `workerd`, `wrangler dev`, or `npm run dev`;
- use the clinic's dedicated Cloudflare remote resources and `*.pages.dev` URL;
- never commit Cloudflare tokens, `clinic.json`, `wrangler.toml`, or HQ installation tokens;
- allow the real Production branch only through ClinicOS deploy guard's Preview verification;
- do not attach a custom domain before client acceptance;
- report a missing Cloudflare account/token or missing HQ binding as a setup blocker instead of
  silently switching to a local database.

`codex-windows` is a legacy alias for `windows-native`. Never require a Codex app merely because
the host is Windows. Claude Code follows `CLAUDE.md`, Codex follows `AGENTS.md`, and both use the
installed starter's shared runtime contract, skill registry, workflows, state, and guardrails.

For the classic track, preserve the existing README procedure unchanged.
