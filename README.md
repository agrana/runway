# Runway a free personal stack

![Solution architecture: GitHub Actions coordinates Cloudflare DNS and Vercel deployment, with a conditional Supabase data and authentication connection.](docs/architecture/solution-overview.svg)

## Onboard your agent

Open your generated repository in your coding agent and paste:

```text
Read docs/onboard-your-agent.md and follow the prompt there.
Confirm this is my generated app, not upstream. Keep secrets out of chat.
```

Full prompt and checklist: [docs/onboard-your-agent.md](docs/onboard-your-agent.md).

## Overview

Runway is a Next.js template you onboard in GitHub: fill Actions secrets, merge `onboarding.config.json` with your hostname and `auto_apply`, and Actions deploys the shell plus DNS.

Onboarding is complete only after DNS, HTTPS, page and revision checks pass at your hostname, and database access, migrations and RLS isolation are verified. Details: [end-to-end onboarding](docs/end-to-end-onboarding.md), [secrets-only launch](docs/secrets-only-launch.md), [custom domain](docs/custom-domain.md).

## License

MIT
