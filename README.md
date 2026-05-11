# AI Agent Evaluation

## What is AI Agent Evaluation?

AI Agent Evaluation is the process of **systematically testing and measuring how well an AI agent performs its intended tasks** before deploying it to production.

Unlike traditional software testing that checks if code works correctly, AI agent evaluation measures:
- **Correctness**: Does the agent provide factually accurate information?
- **Helpfulness**: Are the responses useful and actionable?
- **Coherence**: Is the output well-structured and logical?
- **Safety**: Does the agent avoid harmful or destructive actions?

## Why This Matters

AI agents can autonomously make decisions and take actions. Without proper evaluation, they can cause serious damage.

**Real-world example:** In December 2024, an AI agent from PocketOS [accidentally deleted a customer's entire database](https://zenity.io/blog/current-events/ai-agent-database-deletion-pocketos). The agent misinterpreted a routine query and executed destructive commands without proper safeguards.

This incident highlights a critical gap: **AI agents are being deployed without rigorous evaluation of their decision-making capabilities, especially in high-stakes scenarios.**

## The Problem

Current AI agent development often:
- ✗ Skips systematic evaluation
- ✗ Focuses only on happy-path testing
- ✗ Doesn't test destructive action prevention
- ✗ Lacks automated evaluation frameworks
- ✗ Deploys agents based on "it seems to work"

## The Solution: Systematic Evaluation

Before deploying any AI agent, evaluate it on:

1. **Functional Correctness** - Does it answer questions accurately?
2. **Task Completion** - Does it achieve its goals reliably?
3. **Safety Guardrails** - Does it refuse harmful actions?
4. **Edge Case Handling** - How does it behave in unexpected situations?
5. **Tool Usage Appropriateness** - Does it use tools correctly and safely?

## What This Repository Demonstrates

This repository shows how to build a **robust evaluation framework** for AI agents using:
- **AWS Bedrock** - LLM provider
- **Strands SDK** - Agent framework
- **LLM-as-a-Judge** - Automated evaluation methodology

### Example: Travel Agent Evaluation

We build a simple travel planning agent and evaluate it on:
- **Correctness** (0-5): Is the travel information factually accurate?
- **Helpfulness** (0-5): Are the recommendations useful and actionable?
- **Coherence** (0-5): Is the response well-structured?

This same methodology can be applied to evaluate ANY AI agent, including:
- Customer support agents
- Database management agents (preventing incidents like PocketOS)
- Code generation agents
- System administration agents

## Files

- **`travel_agent_evaluation_fixed.ipynb`** - Main notebook with complete evaluation framework
- **`README.md`** - This file

## Quick Start

### Prerequisites
- AWS CLI configured (`aws configure`)
- Python 3.10+
- Amazon Bedrock access with Claude models enabled

### Installation

```bash
pip install strands-agents boto3 requests
```

### Run

```bash
jupyter notebook travel_agent_evaluation_fixed.ipynb
```

## How It Works

1. **Build an Agent** - Create an AI agent with specific tools
2. **Test with Queries** - Run multiple test scenarios
3. **Evaluate Responses** - Use LLM-as-a-Judge to score outputs
4. **Analyze Results** - Identify strengths and weaknesses
5. **Iterate** - Improve the agent based on evaluation data

## Key Takeaway

**Don't deploy AI agents without evaluation.** 

The PocketOS database deletion could have been prevented with:
- ✓ Systematic evaluation of edge cases
- ✓ Testing destructive action scenarios
- ✓ Scoring safety and reliability metrics
- ✓ Automated regression testing

This repository gives you the tools to evaluate AI agents **before** they cause production incidents.

## Evaluation Criteria Explained

### Correctness
Measures factual accuracy. A score of 0 means completely wrong information; 5 means perfectly accurate.

**Example**: Agent says "Paris is the capital of Germany" → Correctness: 0/5

### Helpfulness
Measures usefulness and actionability. Does the response actually help the user?

**Example**: User asks "best time to visit Japan" and agent says "Japan is in Asia" → Technically correct but not helpful → Helpfulness: 1/5

### Coherence
Measures structure and clarity. Is the response easy to understand and logically organized?

**Example**: Agent provides scattered, disorganized bullet points with no clear flow → Coherence: 2/5

## Extending This Framework

To evaluate your own AI agents:

1. **Define your criteria** - What matters for your use case? (Safety, accuracy, speed, cost)
2. **Create test scenarios** - Include edge cases and adversarial inputs
3. **Build evaluation prompts** - Guide the LLM-as-a-judge on what to assess
4. **Automate testing** - Run evaluations on every agent update
5. **Set thresholds** - Don't deploy agents scoring below acceptable levels

## Resources

- [Strands SDK Documentation](https://strandsagents.com/docs/)
- [AWS Bedrock Documentation](https://docs.aws.amazon.com/bedrock/)
- [PocketOS Database Deletion Incident](https://zenity.io/blog/current-events/ai-agent-database-deletion-pocketos)
- [LLM-as-a-Judge Paper](https://arxiv.org/abs/2306.05685)

## License

MIT

## Contributing

Issues and pull requests welcome. Let's make AI agents safer together.

---

**Remember**: The PocketOS incident wasn't a failure of AI technology—it was a failure of evaluation and testing practices. Build, test, evaluate, then deploy.
