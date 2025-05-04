
# 🚗 Real‑Time Object Detection using YOLOv8 and OpenCV
A Python script that captures live video from your webcam (or a video file), runs YOLOv8 object detection on each frame, and displays annotated bounding boxes, confidence scores and class names in real time. Built with Ultralytics’ YOLOv8, OpenCV for image I/O and display, plus cvzone for easy overlay of text and shapes.

# 📦 Features
1)Real‑time detection: Processes each camera frame through YOLOv8 nano model (yolov8n.pt) at interactive speeds (up to ~30 FPS on a decent GPU, ~5–10 FPS on CPU).
2)Flexible input: Use your default webcam (cv2.VideoCapture(0)) or point at any video file by changing the capture source.
3)Annotated output: Draws colored rectangles around detected objects and prints the class name plus confidence (e.g. “car 0.87”) using cvzone’s putTextRect.
4)Easy model swap: Switch to yolov8s.pt, yolov8m.pt, etc., by changing a single line—no code rewrite needed.

# Light dependency footprint: Only requires ultralytics, opencv-python, and cvzone.

# ⚙️ How It Works
1)Load YOLOv8 model
The script calls model = YOLO("yolov8n.pt"). If the weights file isn’t present locally, Ultralytics will download it automatically.

2)Capture frames
cap = cv2.VideoCapture(0) opens your webcam. You can change 0 to a filename (e.g. "cars.mp4") to process a saved video instead.

3)Inference loop
Read frame: success, img = cap.read()
Run detection: results = model(img, stream=True)
For each detected box, extract coordinates, confidence, and class.

4)Annotate
Draw bounding box: cv2.rectangle(img, (x1,y1), (x2,y2), ...)
Overlay text: cvzone.putTextRect(img, f"{conf}{class_name}", (x1,y1), ...)

5)Display
cv2.imshow("frame", img) shows the annotated frame in a resizable window. Press q to quit.

6)Cleanup
Releases camera and closes windows (cap.release(); cv2.destroyAllWindows()).

# 📁 Detailed Requirements
1)Python 3.8+
2)Ultralytics YOLOv8 (pip install ultralytics)
3)OpenCV (pip install opencv-python)
4)cvzone (pip install cvzone)
5)(Optional GPU) CUDA‑enabled NVIDIA GPU + matching torch build for faster inference


Include a requirements.txt in your repo: ultralytics, opencv-python, cvzone



# 🛠️ Customization
1)Confidence threshold: Only show boxes if conf > 0.5. Adjust in code: if conf > 0.5:
2)Tracked classes: Change which classes to display by editing the if currentClass in [...] list.
3)Window size: Resize frames before display with cv2.resize(img, (width, height)).

# 🛡️ Troubleshooting
1)No camera detected: Ensure your webcam is connected or use a video file.
2)cv2.imshow crash: On headless servers (e.g. Colab), replace with cv2_imshow.
3)Slow FPS: Use a smaller model (yolov8n.pt) or run on GPU.

# 📄 License
This project is released under the MIT License—feel free to use and modify.

# ⭐️ Support
If you find this project useful, please ⭐ star the repository and share!









