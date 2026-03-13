---
name: 🚀 Bug Report (Efficiency & Runtime)
about: Report a runtime crash, logic error, or performance issue.
title: "[Bug]: <Brief description of the issue>"
labels: ["bug", "triage"]
assignees: ""
---

### ⚠️ IMPORTANT: HUMAN-ONLY SUBMISSION POLICY

**AI-generated Issues or Pull Requests will be closed without review.**
- Please use AI(artificial intelligence) only as a auxiliary tool to assist in brainstorming, code analysis, or adding comments.
- A human developer must verify the accuracy, necessity, and urgency of this report before submission.
- It's cool to learn about AI and how it works through a project to improve yourself, right? ;)
---

### Prerequisites

* [ ] I am running the latest code from the **JamePeng/llama-cpp-python** branch.
* [ ] I carefully followed the [README.md](https://github.com/JamePeng/llama-cpp-python/blob/main/README.md).
* [ ] I have verified the issue is not a duplicate.
* [ ] I have tested it using the official binary `llama-cli` or `llama-server` provided by `llama.cpp`, and the problem (exists/does not exist) still exists.
* [ ] I reviewed the [Discussions](https://github.com/JamePeng/llama-cpp-python/discussions), and have a new bug or useful enhancement to share.

### Environment & Hardware Configuration

Please provide your specific setup. Use the suggested commands for your OS to verify.

| Category | Windows 10/11 | Ubuntu / Linux | macOS 15/18/26+ |
| --- | --- | --- | --- |
| **OS Version** | `winver` or System > About | `lsb_release -a` | `sw_vers` |
| **CPU** | Task Manager > Performance | `lscpu` | `sysctl -n machdep.cpu.brand_string` |
| **RAM Size** | Task Manager > Performance | `free -h` | Activity Monitor > Memory |
| **GPU/Multi-Card** | Device Manager / `nvidia-smi` | `nvidia-smi` or `lspci` | System Report > Graphics/Displays |

* **Multi-GPU Setup**: (e.g., 2x RTX 4090 / SLI / None)
* **Specific Hardware Screenshots**: [Insert screenshot of Task Manager / `nvidia-smi` / System Info here]

### Toolchain Versions

Provide the exact versions or commit hashes:

* **Python**: `python --version`
* **Python Library**: `pip list`
* **Compiler**: (e.g., `g++ --version`, `msvc` via VS Installer, or `xcode-select -v`)
* **llama-cpp-python Commit**: `git rev-parse HEAD`
* **vendor/llama.cpp Commit**: `cd vendor/llama.cpp && git rev-parse HEAD`

### Model & Logic Context

* **Model Source**: (e.g., HuggingFace, ModelScope, Custom Conversion)
* **Model Path**: `Qwen3.5-9B-Q4_K_M.gguf`
* **Multimodal Path**: `mmproj-BF16.gguf` (if applicable)

### Failure Timing & Logs

**Is the issue occurring during Build (Compilation) or Runtime?**

#### Runtime Debugging Requirement:

When reporting a runtime bug, you **must** set `verbose=True` in both the `Llama` class and the `ChatHandler` to capture internal logs.

```python
# Required Debugging Configuration
llm = Llama(
    model_path="./Qwen3.5-9B-Q4_K_M.gguf",
    chat_handler=Qwen35ChatHandler(
        clip_model_path="./mmproj-BF16.gguf",
        enable_thinking=True,
        verbose=True  # SET TO TRUE
    ),
    n_gpu_layers=-1,
    n_ctx=40960,
    verbose=True,      # SET TO TRUE
    ctx_checkpoints=0
)

```

### Steps to Reproduce & Reproduction Logic

1. Provide the full `CMAKE_ARGS` used during installation (e.g., `CMAKE_ARGS="-DGGML_CUDA=ON" pip install .`).
2. Provide the full runtime Python script.
    - If privacy is a concern, `pseudo-paths` and `business logic code` can be used to hide the script, while preserving the initialization and runtime code surrounding bug triggers. 
    - Relatively complete code is best for tracking issues. Your choice :)
3. **Reproduction Screenshot**: [Insert screenshot of the error or the unexpected behavior here]

### Analysis & Brainstorming

> Use this section to include any insights gained from AI-assisted code analysis or your own/team's brainstorming.

* **Potential Root Cause**: (e.g., buffer overflows, inaccurate memory releases, kv cache management, unnecessary memory allocations, redundant mergeable runtime logic, etc.)
* **Code Comments/Fix Ideas**: (Paste analyzed code snippets with your added comments)

```text
<PASTE ANALYSIS OR EXPLANATION HERE>

```

---

### Expected Behavior

Describe the expected outcome.

### Current Behavior

Describe the actual outcome and paste the **Verbose Logs** below:

```text
<PASTE FULL VERBOSE LOGS HERE>

```
