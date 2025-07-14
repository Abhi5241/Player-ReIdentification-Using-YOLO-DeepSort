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
   - Click the “Choose Files” widget in Colab and select:
     - `best.pt` (YOLOv11 model weights)  
     - `15sec_input_720p.mp4` (sample video)

3. **Run all cells**  
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
