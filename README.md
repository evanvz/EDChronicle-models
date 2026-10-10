# EDChronicle-models

Backup copies of the third-party model files that [EDChronicle](https://github.com/evanvz/EDChronicle) downloads at install time. They are kept here so a fresh EDChronicle install still works if an original download link disappears.

The files are not stored in this repository's code. Each model version is a GitHub **release** with the files attached, and older releases are never deleted, so every EDChronicle version can always fetch the exact files it was tested with.

## Releases

| Release | Files | Used for | Original source |
|---|---|---|---|
| `kokoro-v1.0` | `kokoro-v1.0.int8.onnx`, `voices-v1.0.bin` | Kokoro offline text-to-speech voices | [thewh1teagle/kokoro-onnx](https://github.com/thewh1teagle/kokoro-onnx/releases/tag/model-files-v1.0) (model by [hexgrad/Kokoro-82M](https://huggingface.co/hexgrad/Kokoro-82M)) |
| `vosk-en-us-0.22-lgraph` | `vosk-model-en-us-0.22-lgraph.zip` | Vosk offline speech recognition (voice commands) | [alphacephei.com/vosk/models](https://alphacephei.com/vosk/models) |

## SHA-256

EDChronicle checks every download against these values, from either source, and rejects a file that doesn't match.

```
6e742170d309016e5891a994e1ce1559c702a2ccd0075e67ef7157974f6406cb  kokoro-v1.0.int8.onnx
bca610b8308e8d99f32e6fe4197e7ec01679264efed0cac9140fe9c29f1fbf7d  voices-v1.0.bin
d9838b4aaa82a75c4a17f5aca300eaca129aaab2a7cbf951bafbb500eb9c4334  vosk-model-en-us-0.22-lgraph.zip
```

## Adding a new model version

1. Test the new files in EDChronicle.
2. Publish them as a new release here, for example `kokoro-v1.1`. Don't replace files in an existing release.
3. Update the URLs and SHA-256 values in EDChronicle's `download_models.py` and `edc/audio/voice_commands.py`.

## License

The model files are redistributed unmodified under the Apache License 2.0 (see [LICENSE](LICENSE)); copyright remains with their original authors. See [NOTICE](NOTICE) for attribution.
