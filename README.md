# Cylix downloads

Model files that the Cylix app downloads the first time a feature needs them. Nothing here runs on its own. Cylix
checks each file's size and full SHA-256 after download.

## AllTracker (release `alltracker-v1`)

The point cloud tracker in Cylix's Track panel. [AllTracker](https://github.com/aharley/alltracker) is by Adam W.
Harley and is under the MIT licence (the release's
[LICENSE](https://github.com/Strothy/cylix-downloads/releases/download/alltracker-v1/LICENSE)). These files are its
published weights, exported to ONNX:

| File | What | SHA-256 |
|---|---|---|
| `enc_ac16.onnx` | the frame encoder (fp16 autocast export) | `2c0d4d086531320c94ef3c01dadeb2c5b51c75273cb986889f02ae9f6daaee07` |
| `enc_ac16.onnx.data` | its weights (stored in fp32) | `0687bd407470037a3fc2f0274717e75ed0ae9ef03cdcfb59196061a9aeb00467` |
| `win_384x640_ac16.onnx` | the 16-frame window refiner, landscape | `acfb35a42f1e35435ae585c6a8938c77a7eb198712259aeb99647c3cd6fd8acd` |
| `win_384x640_ac16.onnx.data` | its weights | `6ae4dfda86106fda5cd5dfb7c5913fd2d2cf91bd68887fc7215fc7182825bb89` |
| `win_640x384_ac16.onnx` | the same, portrait | `7159ba177f804bc50c58b6a3946d6527526b0df9b2786bd8b2f0a1b11542b40f` |
| `win_640x384_ac16.onnx.data` | its weights | `3df28b9033bd74683c99a3edc1e9bdaac08d5d826658c497a06061c601b54efd` |

The only change from a plain export: in the window graphs, `allowzero` is set to 0 on the Reshape nodes that never see
a zero dimension, so DirectML accepts them. The results are the same. The author does not endorse Cylix.

## SigLIP 2 base, picture half (release `siglip2-base-v1`)

The picture model for Cylix's Chapter finder: the image encoder of **SigLIP 2** (google/siglip2-base-patch16-224) by
Google, under the Apache License 2.0. The ONNX export and its int8 quantization are the onnx-community's
(onnx-community/siglip2-base-patch16-224-ONNX, commit ba1f3b0), mirrored unchanged. Cylix downloads it only after the
user says yes. Licence and source: the release's LICENSE.md and LICENSE-Apache-2.0.txt.

| File | Bytes | SHA-256 |
|---|---|---|
| `vision_model_quantized.onnx` | 94553333 | `5f2b401c1a4fc095702a5d45348e17ad46c4f87064085365b43c6e8eaa5c0070` |

Google and the onnx-community do not endorse Cylix.
