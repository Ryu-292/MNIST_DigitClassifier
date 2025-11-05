MNIST Digit Classifier (Tinygrad + WebGPU)

Real-time handwritten digit recognition in the browser using Tinygrad-trained models deployed with WebGPU


![MNIST Web App Screenshot](image-1.png)

#### Live Demo Link: #####

Project demo: [MNIST Web App]([https://yourusername.github.io/mnist_Project/](https://ryu-292.github.io/MNIST_DigitClassifier/))

https://ryu-292.github.io/MNIST_DigitClassifier/

This project trains a handwritten-digit recognition model using TinyGrad, and then runs it directly in the browser using WebGPU. Instead of sending anything to a server, the whole model lives right on the page and runs on your GPU in real time.

You can draw any digit from 0 to 9 on the canvas, and the model will guess what you wrote while showing its confidence across all ten classes.

#### Features ####

- Train MLP & CNN models in Python with TinyGrad

- Export weights to safetensors & run on the web

- WebGPU inference in real-time

- Drawing canvas with pen/eraser tools

- Live confidence bar chart output

- Model switcher (MLP vs CNN)

#### Model Summary ####

| Model | Architecture | Best Accuracy | Steps | Notes |

| MLP | 2-layer fully connected | **97.87%** | 190 | Batch 512, LR 0.002 |
| CNN | Convolutional network | **98.90%** | 180 | Batch 512, slight augmentation |

The best MLP reached 97.87% accuracy, while the CNN achieved 98.90% on MNIST.

#### Local Setup ####

1. Clone the project

```bash
git clone <your-repo-url>
cd mnist_Project
```

2. Create a Python environment and install dependencies

- macOS/Linux
```bash
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
```

- Windows
```powershell
python -m venv .venv
. .venv\Scripts\Activate.ps1
pip install --upgrade pip
pip install -r requirements.txt
```
3. WebGPU Installation 

To export and run the model with WebGPU in Python (tinygrad export step), you need the Dawn WebGPU runtime installed on your system.

- macOS (Apple Silicon)
```bash
brew tap wpmed92/dawn
brew install dawn
```

- Linux (x86-64)
```bash
sudo curl -L https://github.com/wpmed92/pydawn/releases/download/v0.3.0/libwebgpu_dawn_x86_64.so -o /usr/lib/libwebgpu_dawn.so
```

- Windows
```powershell
pip install dawn-python
```

4. Train a model

**Key Commands for Training & Export:**

- macOS/Linux
```bash
JIT=1 STEPS=180 BATCH=512 ANGLE=0 SCALE=0.1 SHIFT=0.4 LR=0.005 python mnist_mlp.py

```

- Windows
```powershell
$env:STEPS=180                      
$env:BATCH=512
$env:ANGLE=0
$env:SCALE=0.1
$env:SHIFT=0.4
$env:LR=0.005
python mnist_convnet.py
```
Try differents hyperparameters

For detailed training configurations and results, see the hyperparameter log:  
➡️ [HYPERPARAMETERS.md](./docs/HYPERPARAMETERS.md)


