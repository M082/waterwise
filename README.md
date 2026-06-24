
# Waterwise: Smart Water Tracking for South Africa

**Waterwise** is a cross-platform mobile application designed to empower South African consumers and utility providers by automating the traditional, manual process of water sub-meter reading. By leveraging modern Computer Vision and Deep Learning, Waterwise eliminates human error, prevents billing disputes, and provides real-time transparency into household water consumption.

---

## 🇿🇦 The South African Context & Challenges

Traditional water sub-metering in South Africa heavily relies on manual municipal or landlord tracking, which introduces several critical pain points:

* **Inefficient Data Collection:** Personnel must manually visit properties to log meter readings into spreadsheets, which is both costly and slow.
* **Environmental Wear & Tear:** Meters are frequently dirty, weather-worn, or placed in dark, inaccessible spots, making them incredibly difficult to read accurately.
* **Human Error & Data Disputes:** Disconnects between paper logs and central accounting software often lead to billing anomalies, shock "estimated" bills, and prolonged consumer disputes.
* **Lack of Transparency:** Consumers and tenants rarely have access to real-time consumption trends, making it difficult to detect leaks or actively conserve water in drought-prone areas.

---

## 🚀 How Waterwise Works (The Workflow)

Waterwise simplifies water tracking into a few seamless steps:

1. **Snap a Photo:** The consumer or representative opens the app and takes a photo of the water meter.
2. **Quality Check:** Embedded Computer Vision techniques automatically assess image quality (checking for blur, low resolution, or poor lighting). If it falls below a specific threshold, the user is instantly prompted to retake it.
3. **Automated Extraction:** Approved images undergo a two-fold Deep Learning process to extract data securely:
* **Text Detection (Area of Interest):** The app isolates the specific numeric display box using highly efficient scene text detectors like **EAST** or **Single Shot Detectors (YOLO/SSD)**.
* **Digit Extraction (CRNN & OCR):** The isolated digits are processed using a Convolutional Recurrent Neural Network (CRNN) paired with OCR tools like Tesseract to accurately transcribe the exact water usage volume.


4. **Instant Billing & Analytics:** The numeric data is sent to the central database, calculating the accurate amount owed based on local tariffs, updating accounting systems instantly, and generating a transparent digital e-bill for the consumer.

---

## ✨ Key Benefits

* **Empowered Consumers:** South Africans can track their daily consumption metrics, gain visual insights to reduce waste, catch leaks early, and ensure they only pay for what they use.
* **Streamlined Operations:** Organizations and property managers can redirect personnel from manual logs to high-priority maintenance tasks.
* **Hardware Agnostic:** No need for expensive, specialized smart meter upgrades. Existing smartphones act as the reading devices, requiring zero technical training for the end-user.
* **Reduced Financial Loss:** Drastically minimizes the multi-billion rand losses typically caused by poor data standards, duplicate data entry, and inaccurate estimations.

---

## 🛠️ Technical Limitations & Ongoing Improvements

While Deep Learning streamlines the pipeline, the underlying OCR engines face specific challenges that the app actively works to mitigate:

* **Small or Sparse Fonts:** Font sizes under 12 points or unstructured meter backgrounds can occasionally lower recognition accuracy.
* **Extreme Environments:** Capturing images in pitch-black or highly obscured settings requires heavy image preprocessing, which can cause information loss.
* **Dataset Dependencies:** Achieving high accuracy requires continuously training and updating models on varied, localized, and accurately labeled datasets of South African water meter variants.

---

## 💻 Getting Started (Developer Setup Example)

To integrate or test the underlying OCR prediction model locally, follow these steps:

### Prerequisites

Ensure you have Python installed, then install the required dependencies:

```bash
pip install requests tqdm

```

### Configuration

Set your API credentials and model IDs as environment variables:

```bash
export WATERWISE_API_KEY="your_secret_api_key"
export WATERWISE_MODEL_ID="your_trained_meter_model_id"

```

### Run a Prediction

Test the extraction pipeline by pointing the script to a saved meter photograph:

```bash
python ./prediction.py /path/to/water_meter_sample.jpg

```
