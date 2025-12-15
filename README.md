# dicom-meta-lite

`dicom-meta-lite` is a lightweight Python utility for extracting essential metadata from DICOM medical imaging files (CT, MRI, X-ray, PET, etc.) without requiring heavy medical imaging frameworks.  
It is ideal for machine learning pipelines, research, radiomics preprocessing, dataset cleaning, and oncology workflows.

---

## ✨ Features

- Extracts key DICOM metadata in a single function call
- Lightweight (minimal dependencies)
- Returns clean Python primitives (not pydicom objects)
- Optional patient anonymization
- Folder batch processing
- Designed for ML preprocessing and dataset inspection

---

## 🚀 Installation

Install via pip:

```

pip install dicom-meta-lite

```

You must also have `pydicom`:

```

pip install pydicom

````

---

## 📌 Usage

### Extract metadata from a single DICOM file:

```python
from dicom_meta_lite import extract_meta

meta = extract_meta("scan.dcm")
print(meta)
````

Example output:

```json
{
  "PatientID": "12345",
  "Modality": "CT",
  "StudyDate": "20240513",
  "Manufacturer": "SIEMENS",
  "Rows": 512,
  "Columns": 512,
  "PixelSpacing": [0.5, 0.5],
  "SliceThickness": 1.2
}
```

---

### Extract only selected keys:

```python
extract_meta("scan.dcm", keys=["PatientID", "Modality"])
```

---

### Remove sensitive identifiers:

```python
extract_meta("scan.dcm", anonymize=True)
```

Removes fields such as:

* PatientName
* PatientBirthDate
* InstitutionName

---

### Batch process a folder of DICOM files:

```python
from dicom_meta_lite import extract_folder

results = extract_folder("dicom_folder/")
print(results)
```

---

## 🔬 Why this library?

Medical imaging datasets contain important metadata used for:

* Image normalization (pixel spacing, slice thickness)
* Quality checks
* Machine learning model preprocessing
* Radiotherapy planning research
* Oncology research pipelines

Existing tools (pydicom, highdicom, MONAI) are powerful but heavy for simple metadata extraction.

`dicom-meta-lite` gives you the essentials in seconds.

---

## 📦 Default extracted tags

By default, the library extracts:

* PatientID
* StudyDate
* Modality
* Manufacturer
* Rows
* Columns
* PixelSpacing
* SliceThickness

Custom keys are supported.

---

## 🧠 Use Cases

* ML model preprocessing
* Dataset cleaning & inspection
* Radiomics feature pipelines
* Medical research automation
* Oncology imaging workflows

---

## 🛡️ Privacy Notice

With anonymization enabled, this package removes identifiers commonly used in DICOM headers.
However, compliance depends on your dataset and jurisdiction.

For sensitive projects, consult your institution’s IRB or DPO.

---

## 📁 Project Structure

```
dicom-meta-lite/
│   README.md
│   setup.cfg
│   pyproject.toml
│   LICENSE
│
└── dicom_meta_lite/
        __init__.py
        core.py
```

---

## 🗺️ Roadmap

Future versions will add:

* JSON export support
* CSV metadata export
* CLI (`dicom-meta file.dcm`)
* Tag description mapping
* Handling nested tag structures

Community contributions are welcome.

---

## 🧩 Requirements

* Python >= 3.8
* pydicom >= 2.4.0

---

## 👤 Author

**Rusheel Sharma**
GitHub: https://github.com/Rusheel86
LinkedIN : https://www.linkedin.com/in/rusheel-sharma/

---

## 📄 License

This project is licensed under the MIT License — see `LICENSE` for details.

---

## ⭐ Support the Project

If this package helps your research or ML workflow, please consider:

* Leaving a star on PyPI/GitHub
* Citing it in your project
* Sharing with classmates

Every bit of community visibility helps!


