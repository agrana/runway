# Onboard your agent

Paste the prompt below into your coding agent when you first find this repository. You do not need a local clone yet. The agent should guide you to create your own app from the template, then through GitHub-only deploy.

You fill Secrets and merge config in GitHub; you should not need local installs for routine onboarding.

## Prompt

```text
I am new to https://github.com/agrana/runway. I have not created my app yet.
Guide me from zero through GitHub-only shell deploy + hostname/DNS.

First step: help me create an independent repository with GitHub
“Use this template” → Create a new repository (not Fork, not clone of upstream).
Suggest a valid lowercase repo name and confirm Template repository stays off
on my new app. After it exists, work only in THAT repository—not upstream.

I should only fill Secrets and merge reviewed config in GitHub. Do not require
local installs, Terraform apply, or pasting credentials into chat.

In my generated repo, read: AGENTS.md, README.md, docs/secrets-only-launch.md,
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
