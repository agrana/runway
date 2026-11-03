# Runway a free personal stack

![Solution architecture: GitHub Actions coordinates Cloudflare DNS and Vercel deployment, with a conditional Supabase data and authentication connection.](docs/architecture/solution-overview.svg)

## Onboard your agent

New here? Paste this into your coding agent (no clone needed yet):

```text
Read https://github.com/agrana/runway/blob/main/docs/onboard-your-agent.md
and follow the prompt. Start by creating my app with Use this template.
Keep secrets out of chat.
```

Full prompt: [docs/onboard-your-agent.md](docs/onboard-your-agent.md).

## Overview

Runway is a Next.js template you onboard in GitHub: create a repo from this template, fill Actions secrets, merge `onboarding.config.json` with your hostname and `auto_apply`, and Actions deploys the shell plus DNS.

Onboarding is complete only after DNS, HTTPS, page and revision checks pass at your hostname, and database access, migrations and RLS isolation are verified. Details: [end-to-end onboarding](docs/end-to-end-onboarding.md), [secrets-only launch](docs/secrets-only-launch.md), [custom domain](docs/custom-domain.md).

## License

MIT
