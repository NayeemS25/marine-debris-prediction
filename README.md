# Marine Debris Detection (Prototype)

## 🌊 Overview
This project is a **prototype for detecting marine debris** using the YOLO object detection framework.  
The ocean is one of our most important natural resources, and protecting it from pollution is crucial.  
By building models that can identify debris, we take a step toward creating tools that can support clean-up efforts and raise awareness.

This is an early-stage prototype, but it demonstrates how AI can be applied to environmental protection.

---

## 📂 Dataset
The dataset was prepared and hosted on **Roboflow**.  
You can access it here:  
👉 [Marine Debris Dataset on Roboflow](https://universe.roboflow.com/tamkang/marine-debris-yolo/dataset/1)

The dataset includes:
- `train/`
- `valid/`
- `test/`
- `data.yaml`

Classes include:  
`can`, `foam`, `plastic`, `plastic bottle`, and `unknown`.

---

## 🛠️ Training
We trained the model in **Google Colab** using YOLOv8.  
Example training script:

```python
from ultralytics import YOLO

# Load YOLO model (pre-trained on COCO)
model = YOLO("yolov8n.pt")

# Train on Marine Debris dataset
model.train(
    data="data.yaml",   # path to dataset YAML
    epochs=50,
    imgsz=640,
    batch=16
)

🔍 Inference
After training, you can run inference on new images:

python
Copy
Edit
from ultralytics import YOLO

# Load your trained weights
model = YOLO("runs/detect/train/weights/best.pt")

# Run inference on an image
results = model.predict("sample.jpg", save=True, imgsz=640, conf=0.25)
The results will be saved in the runs/detect/predict/ folder.

📊 Results
The model was trained on Roboflow’s Marine Debris dataset.

Early results show it can detect plastic bottles, plastic, foam, cans, and other debris.

This is just a prototype — with more data, higher-resolution imagery, and advanced architectures, accuracy can be improved significantly.

🚀 Future Work
Expand dataset size and balance across all debris classes

Use satellite and drone imagery to scale detection

Experiment with larger YOLO models (YOLOv8m, YOLOv8l)

Deploy as a real-time monitoring tool for coastal and ocean cleanup projects

📜 License
This project uses a dataset licensed under CC BY 4.0 License from Roboflow.
The code is open for educational and research purposes.

🙌 Acknowledgments
Roboflow for dataset hosting and preprocessing tools

Ultralytics for YOLOv8

Everyone working towards a cleaner ocean 🌊

sql
Copy
Edit
