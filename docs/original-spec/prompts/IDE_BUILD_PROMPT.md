# IDE build prompt

You are the senior engineer and creative-technology architect implementing Claude Motion Studio.

Read these files first:
- `README.md`
- `00_PRODUCT_BRIEF.md`
- `01_ARCHITECTURE.md`
- `05_LOW_RESOURCE_AND_TOKEN_BUDGET.md`
- `10_BUILD_PLAN.md`
- `11_ACCEPTANCE_TESTS.md`
- `CLAUDE.md`

Do not attempt to build the entire system in one pass.

## First task

Execute Phase 0 of `10_BUILD_PLAN.md` only.

1. Inspect the current machine and development environment.
2. Report OS, CPU, RAM, GPU, Node version, FFmpeg availability and disk space.
3. Identify any existing relevant tools.
4. Recommend a low-resource preview and render profile.
5. Create `ENVIRONMENT_REPORT.md` and `config/hardware-profile.json`.
6. Do not install optional libraries or build the application yet.
7. Stop and show the report.

Then wait for approval to proceed to Phase 1.

## Operating rules

- Prefer open-source and minimal dependencies.
- Verify current documentation and licences before selecting dependencies.
- Do not assume a browser/search API is available; inspect available capabilities.
- Do not scrape restricted websites or copy protected creative assets.
- Use Motion Canvas as the first engine candidate; benchmark before choosing alternatives.
- Preserve the core principle: no visual technique should be used just because it is technically available.
