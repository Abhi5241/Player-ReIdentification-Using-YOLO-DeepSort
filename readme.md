# Player-ReIdentification-Using-YOLO-DeepSort

---

## 📋 Overview

This project demos a simple real-time pipeline that:

1. Loads a fine-tuned YOLOv11 model to detect players (and the ball).
2. Uses DeepSORT to assign and maintain consistent IDs as players exit/re-enter the frame.
3. Writes out a tracked video showing each player’s bounding box + ID.

---

## ⚙️ Requirements

- **Python 3.8+**
- **Google Colab** (GPU runtime recommended)

---

## 🚀 Steps to Run

1. **Open the Colab notebook**

   - Open `PlayerReidentification.ipynb` in Google Colab.

2. **Upload your files**

   - Click the **Choose Files** widget in Colab and select:
     - `best.pt` (YOLOv11 model weights)
     - `15sec_input_720p.mp4` (sample video)

3. **Install dependencies**\
   In the first cell, run:

   ```bash
   !pip install ultralytics deep-sort-realtime opencv-python-headless
   ```

4. **Run all cells**

   - Execute each cell in order.
   - After completion, you’ll get `tracked_output.mp4` with persistent player IDs.

---

## 📂 Folder Structure

```plaintext
.
├── PlayerReidentification.ipynb   # Colab notebook
├── README.md                      # This documentation
├── best.pt                        # Fine-tuned YOLOv11 weights
└── 15sec_input_720p.mp4           # Sample video file
```

---

## 📝 How It Works

### 1. Detection (YOLOv11)

- The model predicts bounding boxes and confidence scores for each player and the ball.

### 2. Tracking (DeepSORT)

- Each detection is formatted as `(x1, y1, x2, y2, score)` and fed to DeepSORT.
- New tracks receive new IDs; “lost” tracks remain valid for a configurable `max_age` of frames.

### 3. Rendering

- Draw green bounding boxes and ID labels on each frame.
- Save the annotated frames into `tracked_output.mp4`.

---

## ⚙️ Configuration

If IDs flicker or split, tweak in the notebook:

```python
tracker = DeepSort(
    max_age=30,            # how long to keep “lost” IDs alive
    n_init=3,              # frames to confirm a new track
    max_cosine_distance=0.4  # appearance-matching threshold
)
```

---

## ❓ Troubleshooting

- **No GPU?**\
  In Colab: **Runtime → Change runtime type → GPU**.
- **File not found?**\
  Check that your uploaded `.pt` and `.mp4` match the names in the notebook.
- **IDs jump?**\
  Increase `max_age` or decrease `max_cosine_distance`.

---

## 🎥 Viewing the Result

Watch the final tracked video here:\
➡️ [Tracked Output on Drive](https://drive.google.com/file/d/1sa4PhxEVM3a49Vhlnwj_0mi1X3k7vyDp/view?usp=sharing)

*Video demonstrates persistent player IDs across the 15-second clip.*

---

## 📞 Contact

For questions, email [**arshdeep@liat.ai**](mailto\:arshdeep@liat.ai) or [**rishit@liat.ai**](mailto\:rishit@liat.ai).

