# Changelog: 01_2025-10-23 - DeepSeek Flash Attention Fallback (Task ID)

**Task:** [[N/A]] Disable Flash Attention on CPU-only environments for DeepSeek-OCR notebook  
**Status:** Done

### Files Updated:
- **UPDATED:** `deepseek_ppt_to_markdown.ipynb` – guard Flash Attention usage and provide CPU warning

### Description:
Adjusted the DeepSeek-OCR loading cell to detect CUDA availability before enabling Flash Attention and to surface a clear error on CPU-only systems.

### Reasoning:
FlashAttention2 requires CUDA hardware. The notebook previously attempted to enable it unconditionally, causing runtime failures on CPU environments. Adding the hardware check and fallback prevents misconfiguration.

### Key Decisions & Trade-off:
- Disabled Flash Attention automatically when CUDA is unavailable to maintain usability.
- Retained an explicit error for CPU-only execution because the model still requires a GPU, ensuring users do not run unsupported configurations.

### Testing:
- Notebook logic inspected; no automated tests run (hardware-dependent change).
