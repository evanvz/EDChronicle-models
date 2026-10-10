# EDChronicle-models

Backup copies of the third-party model files and voice packages that [EDChronicle](https://github.com/evanvz/EDChronicle) downloads at install time. They are kept here so a fresh EDChronicle install still works if an original download disappears.

The files are not stored in this repository's code. Each version is a GitHub **release** with the files attached, and older releases are never deleted, so every EDChronicle version can always fetch the exact files it was tested with.

## Releases

| Release | Files | Used for | Original source |
|---|---|---|---|
| `kokoro-v1.0` | `kokoro-v1.0.int8.onnx`, `voices-v1.0.bin` | Kokoro offline text-to-speech voices | [thewh1teagle/kokoro-onnx](https://github.com/thewh1teagle/kokoro-onnx/releases/tag/model-files-v1.0) (model by [hexgrad/Kokoro-82M](https://huggingface.co/hexgrad/Kokoro-82M)) |
| `vosk-en-us-0.22-lgraph` | `vosk-model-en-us-0.22-lgraph.zip` | Vosk offline speech recognition (voice commands) | [alphacephei.com/vosk/models](https://alphacephei.com/vosk/models) |
| `packages-2026-10` | Wheels (Windows x64, Python 3.12) and source archives for `kokoro-onnx` 0.6.1, `vosk` 0.3.45, `espeakng-loader` 0.2.4, `phonemizer` 3.4.0, plus `espeak-ng` 1.52.0 source; `SHA256SUMS` | Python packages, used by EDChronicle's `install.bat` (`pip --find-links`) if PyPI no longer has them | [PyPI](https://pypi.org); source from PyPI sdists or the matching GitHub tag/commit |

## SHA-256

EDChronicle checks every model download against these values, from either source, and rejects a file that doesn't match. Package hashes are in the `SHA256SUMS` file of the `packages-*` release.

```
6e742170d309016e5891a994e1ce1559c702a2ccd0075e67ef7157974f6406cb  kokoro-v1.0.int8.onnx
bca610b8308e8d99f32e6fe4197e7ec01679264efed0cac9140fe9c29f1fbf7d  voices-v1.0.bin
d9838b4aaa82a75c4a17f5aca300eaca129aaab2a7cbf951bafbb500eb9c4334  vosk-model-en-us-0.22-lgraph.zip
```

## Adding a new model version

1. Test the new files in EDChronicle.
2. Publish them as a new release here, for example `kokoro-v1.1`. Don't replace files in an existing release.
3. Update the URLs and SHA-256 values in EDChronicle's `download_models.py` and `edc/audio/voice_commands.py`.

For new package versions, publish a new `packages-*` release with the wheels, source archives and `SHA256SUMS`, then update `EDC_PACKAGES` in EDChronicle's `install.bat` and the pins in `requirements.txt`.

## License

The model files are redistributed unmodified under the Apache License 2.0 (see [LICENSE](LICENSE)). The packages keep their own licenses (MIT, Apache-2.0, GPL-3.0); the GPL-3.0 parts (phonemizer, and the espeak-ng build inside the espeakng-loader wheel) are accompanied by their complete source in the same release. Copyright remains with the original authors. See [NOTICE](NOTICE) for attribution.
