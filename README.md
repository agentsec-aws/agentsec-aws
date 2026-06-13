# agentsec-aws

**Production AI agent security on AWS — short lessons + copy-paste Terraform you can run today.**

AI agents are showing up in real production systems, and they fail in expensive, embarrassing ways: they leak cloud credentials, run up huge bills, get more permissions than they should, and expose tools to the internet. Most teams find out the hard way.

This repo fixes those problems one at a time. Each module is two things:

- **A lesson** — a plain-English README that explains *what goes wrong* and *the pattern that prevents it*.
- **A working demo** — Terraform you can deploy in about 10 minutes, see fire for real, and tear down. Cost is always stated up front.

You don't need to be a security expert. If you can run a command in a terminal, you can use this.

> Built in public by [Adam Koyuncu](https://github.com/adamkoy). New module roughly every week.

---

## Start here

👉 **[Module 01 — Bedrock Spend Kill-Switch](modules/01-bedrock-spend-killswitch/)**
Stop an AI agent from burning your AWS bill. When Bedrock spend crosses a limit you set, the agent's access is automatically cut off. Free to run.

## All modules

| # | Module | What it does | Status |
|---|--------|--------------|--------|
| 01 | [Bedrock spend kill-switch](modules/01-bedrock-spend-killswitch/) | Hard-stops an agent's AI model access when spend crosses your budget | ✅ Ready |
| 02 | Agent IAM | Least-privilege roles for agents — and the ways agents leak AWS credentials | 🔜 Planned |
| 03 | MCP secure deployment | Running MCP servers on AWS without handing out the keys | 🔜 Planned |
| 04 | Prompt-injection containment | Limiting the blast radius when an agent gets hijacked | 🔜 Planned |
| 05 | Agent audit trail | Knowing exactly what your agent did, and when | 🔜 Planned |

---

## What you'll need (one-time setup)

To run any module you need three free things installed:

1. **An AWS account** — [sign up here](https://aws.amazon.com/free/). The demos stay inside the free tier.
2. **The AWS CLI**, logged in — [install guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html). Run `aws configure` once to add your keys.
3. **Terraform** — [install guide](https://developer.hashicorp.com/terraform/install). This is the tool that creates the AWS resources for you.

Check it's all working:

```bash
aws sts get-caller-identity   # should print your AWS account number
terraform -version            # should print a version
```

That's it. Open a module and follow its README.

---

## What this project believes

1. **Deny by default.** Agents should get the *least* access that lets them work, with hard limits behind them.
2. **If it doesn't run, it doesn't count.** Every idea here ships as something you can actually deploy.
3. **Honest about cost and limits.** Every module tells you what it costs and where it stops working. No magic.

## License

[Apache 2.0](LICENSE) — free to use, modify, and build on, including commercially.
