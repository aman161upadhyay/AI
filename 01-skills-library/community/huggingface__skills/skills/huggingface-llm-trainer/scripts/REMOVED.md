# Removed conversion helper

Removed file: `convert_to_gguf.py` (entire file).

Reason (SEC-002): model loading enabled remote Python without a model revision; the helper cloned, installed dependencies, built and ran unpinned llama.cpp, then uploaded through HfApi in the same credential-bearing process.

Upstream: https://github.com/huggingface/skills/blob/fabc634a893f62ad5c2039830397efa35fa62715/skills/huggingface-llm-trainer/scripts/convert_to_gguf.py

Do not restore or reconstruct this helper without review. Any replacement must default remote-code trust off, pin model/tool revisions and dependencies, isolate conversion from credentials and egress, and separate upload into an explicitly approved phase. See the upstream-root SOURCE.md.
