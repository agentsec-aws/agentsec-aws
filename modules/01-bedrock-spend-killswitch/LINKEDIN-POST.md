# LinkedIn Post — Bedrock Spend Kill-Switch

> Copy-paste this when you post the video. Edit the numbers to match your real experience.

---

## Post text

Our AI agent ran for 6 hours unmonitored.

AWS bill: $4,200.

Here's the 3-component system I built to make sure it never happens again 👇

```
AWS Budgets → SNS → Lambda → IAM Explicit Deny
```

How it works:

1. **AWS Budgets** watches your Bedrock spend in real-time
2. When it crosses your limit, it fires an **SNS alert**
3. A **Lambda** picks it up and attaches a policy to the agent's IAM role
4. That policy is an **Explicit Deny** — it overrides everything, even admin access

The agent is dead. Instantly. No human needed.

The key insight: IAM Explicit Deny is the only permission that can't be overridden by anything else in AWS. That's what makes this reliable.

Full Terraform module is open source — deploy it in 10 minutes:
👉 github.com/adam-ai-aws/agentsec-aws

If you're running AI agents on AWS without this, you're one stuck loop away from a surprise bill.

What's your current AI cost guardrail? Drop it below 👇

---
#AWS #AIAgents #AmazonBedrock #DevOps #CloudSecurity #Terraform #IAM #AWSCosts

---

## Video script outline

**[0:00 - 0:30] Hook**
- Open with the AWS bill screenshot
- "This happened because we had no kill-switch on our AI agent"

**[0:30 - 1:30] The problem**
- Show a Bedrock agent running in a loop
- Watch the cost climb in Cost Explorer
- "There's nothing stopping it"

**[1:30 - 3:00] The solution — diagram walkthrough**
- Draw/show the flow: Budgets → SNS → Lambda → IAM Deny
- Explain why Explicit Deny is the key — nothing can override it
- "Not even your admin role"

**[3:00 - 4:30] Live demo**
- `terraform apply` — show it deploying in ~2 minutes
- Trigger the budget alarm manually
- Watch the Lambda attach the deny policy
- Try to call Bedrock — show the AccessDenied error

**[4:30 - 5:00] CTA**
- "Full module is free on GitHub — link in comments"
- "Follow for one new AI security pattern every week"
- "What's your current guardrail? Let me know below"

---

## Thumbnail text ideas

- "I stopped a $4,200 AWS bill with 3 lines of Terraform"
- "The IAM trick that kills your AI agent's bill automatically"
- "AWS Bedrock cost kill-switch — deploy in 10 min"
