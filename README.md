## Document Scanner with Text Detection and Recognition

This project implements the pipeline described in your mini-project proposal
*“Document Scanner with Text Detection and Recognition using OpenCV and Python”*
([proposal PDF](file://Image%20processing%20project%20proposal.pdf)). It uses
classical image processing in OpenCV plus Tesseract OCR.

### Features
- **Preprocessing**: resize, grayscale, Gaussian blur, adaptive thresholding.
- **Document detection**: Canny edges, contour detection, quadrilateral
  approximation, perspective transform (homography).
- **Scanning**: warped, rectified top-down view of the document.
- **OCR**: PyTesseract with appropriate page segmentation mode to extract text.
- **UI**: Streamlit app to upload multiple images, preview scanned outputs, and
  download a combined PDF and extracted text file.

### Installation

1. **Create and activate a virtual environment (recommended)**

```bash
cd "D:\Final Year\7 SEM\Image Processing\Project\OUR\project\ImageScanner"
python -m venv .venv
.venv\Scripts\activate
```

2. **Install Python dependencies**

```bash
pip install -r requirements.txt
```

3. **Install Tesseract OCR (system dependency, not via pip)**

- Download the Windows installer from the official Tesseract site or from
  `https://github.com/tesseract-ocr/tesseract`.
- Install it (default path is usually
  `C:\Program Files\Tesseract-OCR\tesseract.exe`).
- If Tesseract is not on your `PATH`, open `app.py` and set:

```python
import pytesseract
pytesseract.pytesseract.tesseract_cmd = r"C:\Program Files\Tesseract-OCR\tesseract.exe"
```

### How to Run

From the project folder:

```bash
streamlit run app.py
```

This will open the Streamlit app in your browser.

### How to Test

1. **Functional test**
   - Open the Streamlit app.
   - Upload one or more document photos (JPG/PNG) with skewed angles or uneven
     lighting.
   - Verify that:
     - The displayed result is a rectified, “scanned-like” top-down view.
     - Text in the image is recognized and shown under each document.
     - You can download a PDF of all scanned images.
     - You can download a `.txt` file with concatenated OCR text.

2. **Proposal alignment check**
   - Confirm that the following steps are present in `app.py`:
     - Grayscale + Gaussian blur preprocessing.
     - Edge detection (Canny) and contour detection for document localization.
     - Perspective transformation (`cv2.getPerspectiveTransform` +
       `cv2.warpPerspective`) for rectification.
     - Adaptive thresholding and morphological operations before OCR.
     - OCR with PyTesseract using an appropriate PSM (e.g. 6).

3. **Quality / robustness testing**
   - Capture ~100–200 images with different lighting, angles, and document
     types (books, receipts, notes), as described in the proposal.
   - For a subset with known ground-truth text, compute a simple **character
     accuracy** metric: correct characters / total characters.
   - Observe OCR quality on clean vs noisy images to discuss in your report.

### Notes
- The implementation focuses on classical image processing (Canny, blur,
  thresholding, morphology, homography) in line with the proposal, without
  training deep learning models.
- You can further extend it with real-time camera input and language packs
  for multilingual OCR if needed.


###
.\.venv\Scripts\activate
streamlit run app.py