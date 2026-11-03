# Onboard your agent

Paste the prompt below into your coding agent after you generate a repository with GitHub **Use this template** (not a fork or clone of upstream).

It walks the agent through GitHub-only shell deploy and hostname/DNS: accounts, Actions secrets, merge-reviewed config, and how to read readiness. You fill Secrets and merge config in GitHub; you should not need local installs for routine onboarding.

## Prompt

```text
I generated an independent app repository from the Runway template
(https://github.com/agrana/runway via GitHub “Use this template” — not a fork).
Work only in THIS repository. Confirm it is my generated app, not upstream.

Goal: guide me through GitHub-only shell deploy + hostname/DNS. I should only
fill Secrets and merge reviewed config in GitHub. Do not require local installs,
Terraform apply, or pasting credentials into chat.

Read first: AGENTS.md, README.md, docs/secrets-only-launch.md,
docs/end-to-end-onboarding.md, docs/custom-domain.md, onboarding.config.json.

Then walk me step-by-step through:
1) Accounts I need (GitHub, Vercel team, existing Supabase project, Cloudflare
   zone + domain) and what each is for.
2) Exact Actions repository secrets to create, with where to get each value
   (names only — never ask me to paste secret values here):
   VERCEL_API_TOKEN, VERCEL_TEAM_ID, SUPABASE_URL, SUPABASE_ANON_KEY,
   CLOUDFLARE_API_TOKEN (plus optional SUPABASE_ACCESS_TOKEN only if enabling
   database catalog preflight).
3) Prepare a PR that sets onboarding.config.json: hostname,
   cloudflare_zone_name, auto_apply: true. Explain that merging that PR is the
   apply authorization (not “Run workflow”).
4) What Merge onboarding does after App Quality, how to read the run summary,
   and how to verify at the intended hostname (/ and /api/health revision).

Be explicit about readiness:
- Shell + DNS success is intermediate (e.g. infrastructure_dns_verified_database_incomplete).
- Onboarding is complete only after DNS, HTTPS, page and revision checks pass at
  the hostname, plus database connection, migrations and RLS isolation.
- Say which of those are still gaps vs already automated.
Do not bypass disabled migration/Terraform gates. Ask before any secret write,
provider mutation, or migration. Prefer docs-backed checklists over improvisation.
```

## Where the detail lives

| Topic | Doc |
| --- | --- |
| Secrets, team ID, recovery | [secrets-only-launch.md](secrets-only-launch.md) |
| Hostname and DNS | [custom-domain.md](custom-domain.md) |
| Full readiness contract and gaps | [end-to-end-onboarding.md](end-to-end-onboarding.md) |
| Agent working rules | [AGENTS.md](../AGENTS.md) |
