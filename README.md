# AI BIPOD

**Artificial Intelligence Bulk Image Processor for Object Detection**

Batch-sort large image libraries into folders by detected object class.

Please read readme in release zip file.

NVIDIA GPU: bipod-rtx — RF-DETR + TensorRT https://github.com/baboeska/bipod-rtx

Intel/AMD CPU (AVX2): bipod-yolo26s-openvino — YOLO26s + OpenVINO https://github.com/baboeska/bipod-yolo26s-openvino

Raspberry Pi 4/5: bipod-pi — YOLO26n + OpenVINO https://github.com/baboeska/bipod-pi

Rockchip RK3568: bipod-yolo-rknn — YOLO11s + RKNN https://github.com/baboeska/bipod-yolo-rknn


## Performance

| NVIDIA RTX 4060M 8GB| RF-DETR Large + TensorRT | **60–80 img/s** | 15-25 img/s |

| AMD Ryzen 4650U | YOLO26s + OpenVINO | ~6.5 img/s | 2-5 img/s |

| Core i9 13900H | YOLO26s + OpenVINO | 10-13 img/s | 4-8 img/s |

| Raspberry Pi 4/5 Untested | YOLO26n + OpenVINO | ~10 FPS estimated | Soon |

| Rockchip RK3568 (0.8 TOPS NPU) | YOLO11s + RKNN | ~6.5 img/s | ~1-1.5 img/s |


## Usage

    python bipod-*.py -i /your/images -o /sorted/images -m model



Known pitfalls

OpenVINO: point --model at the exported directory, not the .xml file. Export with nms=False to avoid the mask-shape error.

TensorRT: rebuild the .engine on the machine that will run it — engines are GPU-specific.

WSL2: keep your image library on the native Linux filesystem, not /mnt/. On a USB drive mounted through Windows, throughput can drop 10–16×.

Requirements

Python 3, plus tqdm, opencv-python, and backend-specific packages (see each sub-repo).

If you get stuck, ask your AI buddy. DeepSeek, ChatGPT, Gemma4 and Google Search AI were all very helpful in making this.
License

Mixed licences: Apache 2.0, AGPL 3.0, RKNN-Toolkit License.
Share and share alike, and do good things.

AI BIPOD
