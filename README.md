# Inference Speed Comparison of YOLO Models for Object Tracking

## Overview
This report compares the inference speeds of three YOLO models—YOLOv10n, YOLO11n, and YOLO12n used for object tracking on a 942 frame video (`test1.mp4`). The models were evaluated in Google Colab with a GPU (T4).

## Methodology
- **Models**: YOLOv10n, YOLO11n, YOLO12n (pretrained weights: `yolov10n.pt`, `yolo11n.pt`, `yolo12n.pt`).
- **Task**: Object tracking with persistent tracking (`persist=True`, `conf=0.25`, `iou=0.7`) using Ultralytics’ `track` method.
- **Video**: `test1.mp4` (942 frames).
- **Metrics**: Inference time per frame (ms), averaged over all frames.
- **Environment**: Google Colab, Python 3.11, Ultralytics 8.3.111, CUDA-enabled.

## Results
The table below summarizes the average inference speeds (ms per frame):

| Model     | Avg. Inference Speed (ms) |
|-----------|---------------------------|
| YOLOv10n  | 169.19                    | 
| YOLO11n   | 155.91                    |
| YOLO12n   | 180.98                    |

## Analysis
- **YOLOv11n**: Fastest, with an average inference speed of 155.91 ms per frame. Its optimized architecture likely improves efficiency over others.
- **YOLOv10n**: Slightly slower at 169.19 ms, but competitive, suggesting a good balance between speed and accuracy for lightweight models.
- **YOLO12n**: Slowest at 180.98 ms, as it suggests further investigation into its tracking implementation. Verify `flash-attn` installation may improve results.

## Conclusion
YOLO11n is the fastest model for object tracking on this video, followed closely by YOLOv10n. YOLO12n, while robust, is noticeably slower. For applications prioritizing speed, YOLO11n is recommended. Future work could explore accuracy metrics like tracking precision or test on different hardware or different videos.

## Notes
- Speeds may vary with GPU type, batch size, or video content.
- Tracking results (videos) are saved as `test1_yolov10n_tracked.mp4`, `test1_yolo11n_tracked.mp4`, and `test1_yolo12n_tracked.mp4` in `/content/runs/detect/`.
- For fast results check it is attached in the `output` folder in the repo.
