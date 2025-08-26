# Vision-Eye Mapping — People Distance & IDs (YOLOv11 + OpenCV)

Detect people, assign a unique ID per person and compute the distance from the bottom-left corner of the frame.  
The overlay shows a bounding box, a line from the origin to each person, and a label: `person ID | Distance m`

> Demo video and repository link — replace with your own:
> - GitHub: https://github.com/ValerioCann/VisionEye_Mapping_Yolov11

---

## ✨ Features
- **YOLOv11 (COCO)** for `person` detection.
- **Multi-object tracking** (ByteTrack / BoT-SORT) via Ultralytics → **stable IDs** across frames.
- **Metric distance** using a simple **meters-per-pixel** scale (default **50 px = 1 m** → `0.02 m/px`).
- Clean overlay: bounding box, foot point, **origin→person** line, and an inline label with **ID + distance**.
- **Robust video export** (tries multiple codecs).


🧠 How it works

Detection: model(..., classes=[0]) (COCO class person) or model.track(...) for tracking.

Tracking: model.track(frame, tracker=TRACKER, persist=True) returns r.boxes.id (track IDs).

Distance:

Origin = bottom-left pixel (0, H).

Foot point ≈ bottom-center of the bounding box (cx, y2).

Meters = hypot(cx - 0, y2 - H) * METERS_PER_PIXEL.


🗺️ Possible extensions

Trails (short trajectories) per ID.

Directional counters (in/out lines).

CSV export (frame, ID, confidence, pixel coords, distance).

Homography calibration for true ground-plane meters.

ROI masks to ignore irrelevant zones.



🙌 Librairies

Ultralytics YOLO
OpenCV


### Output preview

<img src="[https://github.com/ValerioCann/VisionEye_Mapping/assets/136093296/d59111c0-db17-4fca-9883-0b58e316180a](https://github.com/ValerioCann/VisionEye_Mapping_Yolov11/blob/main/Vision_Eye_Mapping_%26_Distance_Calculation_Output.mp4.mp4)" width="500" height="300"> 





### Output preview

<img src="https://github.com/ValerioCann/VisionEye_Mapping/assets/136093296/d59111c0-db17-4fca-9883-0b58e316180a" width="500" height="300"> <img src="https://github.com/ValerioCann/VisionEye_Mapping/assets/136093296/ac062ccc-ad42-4dd1-b77a-05fadc3e90a1" width="500" height="300">

