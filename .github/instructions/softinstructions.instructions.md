---
applyTo: '**'
---
Coding standards, domain knowledge, and preferences that AI should follow.Here’s a single prompt you can paste into GitHub Copilot (in a Markdown or comment block) that will generate a detailed, expert‐level step-by-step guide for cloning, installing, configuring and running the e-commerce project (including Next.js, Payload CMS, dependencies, JSON config, MongoDB in Docker, etc.):

```markdown
# Project Setup Guide Generator

You are an expert full-stack developer and instructor. Generate a comprehensive, step-by-step setup guide for this repository:

  https://github.com/adrianhajdin/ecommerce

Your guide must cover:
 
2. **Installing all dependencies needed ** (Next.js, Payload CMS, other npm packages)  
help getting all keys for environment variables, such as Stripe keys, Payload secret, etc. as in the exemple PORT=3000
DATABASE_URI=mongodb://127.0.0.1/payload-template-ecommerce
PAYLOAD_SECRET=712kjbkuh87234sflj98713b
PAYLOAD_PUBLIC_SERVER_URL=http://localhost:3000
STRIPE_SECRET_KEY=
PAYLOAD_PUBLIC_STRIPE_IS_TEST_KEY=true
STRIPE_WEBHOOKS_SIGNING_SECRET=
PAYLOAD_PUBLIC_DRAFT_SECRET=demo-draft-secret
REVALIDATION_KEY=demo-revalation-key

# Next.js vars
NEXT_PUBLIC_SERVER_URL=http://localhost:3000
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=
NEXT_PUBLIC_IS_LIVE=
NEXT_PRIVATE_DRAFT_SECRET=demo-draft-secret
NEXT_PRIVATE_REVALIDATION_KEY=demo-revalation-key

explain how to get these keys, such as Stripe keys, Payload secret, etc. and api keys for other services if needed.

3. **help setting and Explaining the key JSON/config files etc ** (`package.json`, `payload.config.ts`, `.env.local`, etc.)  
4. **Setting up MongoDB via Docker** (including `docker-compose.yml`, volume mounting, seed data)  
5. **Running the Payload admin panel and get authorizations for access to make changes**  
6. **Running the Next.js storefront**  
7. **How each major piece works together** (Next.js SSR, Payload CMS API, Stripe integration, TypeScript types)  
8. **Common troubleshooting tips**

Format your answer as a numbered list of terminal commands and config snippets, followed by concise explanatory paragraphs for each step. Use code blocks for commands and config file examples.
```

Paste that into Copilot’s prompt window and it will generate your detailed instructions.
