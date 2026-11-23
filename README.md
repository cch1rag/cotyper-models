# cotyper-models

The signed list of new models that Cotyper can offer. Cotyper reads it only when "Check for new models" is on in its settings (off by default), and sends nothing about you when it does.

- `models.json`: the list. `version` is 1. Raise `issued` (ISO 8601) whenever the list changes, because Cotyper refuses a list older than the last one it accepted.
- `models.json.sig`: an Ed25519 signature over the exact bytes of `models.json`, in base64. Cotyper pins the public key `L2MdcxIPMbiFuUIfYMFu46AF9cntBv5uEbYnhj8I9Rs=` and ignores any list whose signature doesn't check.

Each entry in `models`:

```json
{
  "displayName": "Qwen 3 4B",
  "family": "Alibaba Qwen 3",
  "isInstruct": false,
  "quantization": "i1-Q4_K_M",
  "repo": "mradermacher/Qwen3-4B-Base-i1-GGUF",
  "fileName": "Qwen3-4B-Base.i1-Q4_K_M.gguf",
  "url": "https://huggingface.co/mradermacher/Qwen3-4B-Base-i1-GGUF/resolve/main/Qwen3-4B-Base.i1-Q4_K_M.gguf?download=true",
  "sha256": "<64 hex characters>",
  "byteSize": 2497280960,
  "minimumSystemRAMGB": 8
}
```

To publish a change, edit `models.json`, sign it with `swift tools/dev/sign_models.swift models.json` from the Cotyper repo, and push both files.
