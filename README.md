# 📋 **Person Re-Identification Project Setup Guide**

This guide outlines the steps to set up the project on **Windows** and **Mac**.

---

## ⚙️ **System Requirements**

- **Python 3.9** (Recommended)
- **OpenVINO** for deep learning inference
- **Paho MQTT** for message communication
- **DroidCam/Other IP Camera Apps** (For IP Camera support)
- **GPU Recommended** (For better performance)

---

## 🖥️ **Windows Setup**

### **Step 1: Install Python 3.9**

1. Download Python 3.9 from the official website: [Download Python 3.9](https://www.python.org/downloads/release/python-390/)
2. During installation:
   - ✅ Check **Add Python 3.9 to PATH**
   - ✅ Select **Customize installation** → Enable **"Install for all users"**
3. Verify installation:

```bash
python --version
```

---

### **Step 2: Install Dependencies**

1. Navigate to the project folder:

```bash
cd C:\feds_person_reidentification-main
```

2. Create a virtual environment:

```bash
python -m venv person_reid_env
```

3. Activate the environment:

```bash
.\person_reid_env\Scripts\activate
```

4. Upgrade `pip` and install required libraries:

```bash
pip install --upgrade pip
pip install -r requirements.txt
pip install openvino==2022.3.0 paho-mqtt==1.6.1
```

---

### **Step 3: Enable PowerShell Script Execution (If Required)**

If you encounter an error like `ExecutionPolicy Error`:

1. Open **PowerShell as Administrator**.
2. Run the following command:

```powershell
Set-ExecutionPolicy RemoteSigned
```

---

### **Step 4: Running the Project**

To start the project with the camera:

```bash
python app.py -i cam --device_reidentification CPU
```

For IP camera:

```bash
python app.py -i "http://<YOUR-IP-CAMERA-URL>/video" --device_reidentification CPU
```

For GPU acceleration:

```bash
python app.py -i cam --device_reidentification GPU
```

---

### **Step 5: Browser Access**

- Open your browser and visit:

```
http://localhost:8000
```

---

## 🍎 **Mac Setup**

### **Step 1: Install Homebrew (if not already installed)**

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### **Step 2: Install Python 3.9**

```bash
brew install python@3.9
```

### **Step 3: Create Virtual Environment**

```bash
python3.9 -m venv person_reid_env
```

### **Step 4: Activate Virtual Environment**

```bash
source person_reid_env/bin/activate
```

### **Step 5: Install Dependencies**

```bash
pip install --upgrade pip
pip install -r requirements.txt
pip install openvino==2022.3.0 paho-mqtt==1.6.1
```

### **Step 6: Running the Project**

For webcam:

```bash
python app.py -i 0 --device_reidentification CPU
```

For IP camera:

```bash
python app.py -i "http://<YOUR-IP-CAMERA-URL>/video" --device_reidentification CPU
```

For GPU acceleration (If supported):

```bash
python app.py -i cam --device_reidentification GPU
```

---

## 📰 **For IP Camera Setup**

1. Install **DroidCam** (or any IP camera app) on your phone.
2. Connect your phone to the same Wi-Fi network as your computer.
3. Use the provided IP address in the command:

```
python app.py -i "http://192.168.0.131:4747/video" --device_reidentification CPU
```

---

## 🚨 **Troubleshooting**

1. **Error:** `ExecutionPolicy Error` (Windows)
   - Run PowerShell as Admin → `Set-ExecutionPolicy RemoteSigned`
2. **Error:** `OpenVINO Error`
   - Ensure `openvino==2022.3.0` is correctly installed.

---

## 🎯 **Recommended Settings for Better Identification**

- **Confidence Threshold**: Increase to `0.80` or `0.90` for improved accuracy.
- **Tracking Threshold (`sim_thld`)**: Reduce to `0.40` for fast-moving objects.
- **Bounding Box Size (`resize_width`)**: Increase for better visibility of distant objects.

---

If you face issues, feel free to ask! 🚀
