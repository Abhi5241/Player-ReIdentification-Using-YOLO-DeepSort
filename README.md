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
- **Colab**


# Steps to run the project

## 1.Open the Colab Notebook

## 2.Upload your files

Use the Colab “Choose Files” widget to upload:

best.pt
15sec_input_720p.mp4

## 3.Run all cells

The pipeline will produce tracked_output.mp4 with persistent IDs.



## Folder Structure
.
├── PlayerReidentification.ipynb   # Colab notebook

├── README.md                     # This file

├── Best.pt        # Your YOLO model weights

└── 15sec_input_720p.mp4          # Sample video



# How It Works

## 1.Detection (YOLOv11)

  1. Predicts bounding boxes + confidences for players/ball.

## 2.Tracking (DeepSORT)

  1.Converts each box → (x1,y1,x2,y2,score) → updates tracks.
  
  2.New tracks get new IDs; lost tracks survive for max_age frames.

## 3.Rendering

  1.Draws green boxes + ID labels on each frame.
  
  2.Writes frames to tracked_output.mp4.
