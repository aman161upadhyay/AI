# Train only after a measured prompt/tool baseline

Use SFT for approved successful trajectories and RL only with a defensible reward. Status date: 2026-10-25. Repository activity establishes maintenance, not training effectiveness on a new task.

| Rank | Resource | Status / authority | Why and limit |
|---|---|---|---|
| P1 | [DSPy](https://github.com/stanfordnlp/dspy), [MIPROv2](https://dspy.ai/3.0.4/api/optimizers/MIPROv2), [optimizers](https://dspy.ai/learn/optimization/optimizers/) | Active first-party repository/docs | Optimize instructions and examples before weights; keep selection/test data separate |
| P1 | [TRL](https://github.com/huggingface/trl), Hugging Face | Active first-party repository | SFT and GRPO examples, trainer APIs, tests; pin installed version |
| P1 | [verifiers](https://github.com/PrimeIntellect-ai/verifiers), Prime Intellect | Active first-party repository | Environment/reward definitions and tests; current successor to the older willccbb reference |
| P2 | [Unsloth](https://github.com/unslothai/unsloth) | Active first-party repository | Constrained-budget fine-tuning; Apache core and optional AGPL components require file-level review |
| P2 | [ART](https://github.com/OpenPipe/ART), OpenPipe | Active first-party repository | Multi-turn rollout/reward integration; inspect model/artifact licenses separately |
| P2 | [ReTool](https://arxiv.org/abs/2504.11536), Feng et al., 2025-04-17 | Original research | Cold-start SFT then tool-integrated outcome RL; not a general turnkey agent recipe |
| P2 | [SWE-RL](https://arxiv.org/html/2502.18449v1), Wei et al., 2025-02-25 | Original research | GRPO over software evolution; patch-similarity reward can penalize equivalent correct solutions |
| P2, after scaling evidence | [prime-rl](https://github.com/PrimeIntellect-ai/prime-rl) | Active first-party repository | Trainer/inference/orchestrator split; study without launching when one-device work suffices |
| P2 | [HF Agents course](https://huggingface.co/learn/agents-course/unit0/introduction) | Current first-party course | Function-calling fine-tuning unit as a targeted supplement |

Maintain disjoint train, validation, and test tasks. Remove secrets and unapproved private text. Unit-test the reward against invalid outputs and shortcuts. Inspect high-reward trajectories manually. Compare task success, schema validity, OOD behavior, cost, and unsafe actions against a strong prompt-only baseline.

TRL trains models, verifiers defines environments/rewards, ART integrates rollouts, and prime-rl scales execution. They are complementary layers, not four mandatory installations. Record actual hardware/VRAM from chosen model docs and cap GPU/API spend before launch.
