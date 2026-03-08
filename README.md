# Face Emotion Detection using DeepFace and OpenCV

This project detects **faces in an image** and displays the **dominant emotion above each detected face** using the **DeepFace library** and **OpenCV**.

The system analyzes an image, finds human faces, predicts emotions such as **happy, sad, angry, surprise, fear, disgust, or neutral**, and draws the results on the image.

---

# Project Output

The program will:

1. Detect all faces in an image.
2. Predict the **emotion for each face**.
3. Draw a **rectangle around each face**.
4. Display the **emotion label above the face**.

Example output:

```
[Happy]     [Neutral]     [Surprise]
  □            □             □
```

---

# Requirements

Install the following libraries before running the project.

### 1 Install Python libraries

```bash
pip install deepface
pip install opencv-python
pip install matplotlib
```

---

# Project Structure

Example project folder:

```
emotion-detection-project
│
├── celebrity.jpg
├── main.py
└── README.md
```

`celebrity.jpg` → Image that will be analyzed
`main.py` → Python program

---

# Step-by-Step Implementation

## Step 1 Import Required Libraries

Import the libraries needed for:

* Image processing
* Face emotion analysis
* Displaying the image

Libraries used:

* OpenCV
* DeepFace
* Matplotlib

---

## Step 2 Load the Image

Load the input image using OpenCV.

The image will be stored in a variable so it can be processed by the emotion detection system.

Example task:

* Read the image from disk
* Store it in memory

---

## Step 3 Analyze Faces Using DeepFace

Use the DeepFace library to analyze the image.

The system will:

1. Detect faces
2. Analyze emotions
3. Return results for each face

Important configuration:

* Enable **emotion detection**
* Allow detection even if faces are slightly unclear

The output will contain:

```
region (face location)
emotion scores
dominant emotion
```

---

## Step 4 Handle Single or Multiple Faces

DeepFace sometimes returns:

* A **dictionary** when only one face is detected
* A **list** when multiple faces are detected

To make the program stable:

Convert the result into a **list format** so the program can loop through each detected face.

---

## Step 5 Extract Face Coordinates

For each detected face, extract the region values:

```
x → horizontal position
y → vertical position
w → width of face
h → height of face
```

These coordinates help draw the rectangle around the face.

---

## Step 6 Get the Dominant Emotion

Each detected face will contain emotion predictions.

Example structure:

```
happy
sad
angry
fear
surprise
neutral
```

The system selects the **dominant emotion**, which is the emotion with the highest probability.

---

## Step 7 Draw a Rectangle Around the Face

Using OpenCV:

1. Draw a rectangle
2. Use the extracted coordinates
3. Highlight the face

Typical rectangle properties:

```
Color → Green
Thickness → 2 pixels
```

---

## Step 8 Display Emotion Text

Place the detected emotion **above the face rectangle**.

Use OpenCV text rendering to display:

```
Happy
Sad
Neutral
Surprise
```

Position:

```
(x , y - 10)
```

This places the label slightly above the detected face.

---

## Step 9 Convert Color Format

OpenCV uses **BGR color format**, but Matplotlib uses **RGB**.

Before displaying the image:

Convert the color format from **BGR → RGB**.

---

## Step 10 Display the Final Image

Use Matplotlib to display the processed image.

The final image will contain:

* Face bounding boxes
* Emotion labels above each face

---

# Algorithm

```
Start

Load input image

Send image to DeepFace analyzer

Detect faces in image

For each detected face

    Extract face coordinates (x, y, width, height)

    Get dominant emotion

    Draw rectangle around face

    Display emotion label above face

Convert image color format (BGR to RGB)

Display final image

End
```

---


# Basic Syntax and example To Show Text in image using opencv
cv2.putText(image, text, position, font, font_scale, color, thickness)
Parameters

image → Image where text will appear

text → Text string to display

position → (x, y) starting position

font → Font type

font_scale → Size of text

color → (B, G, R) color

thickness → Text thickness

Minimal Example
```
import cv2

# Create a blank image
img = cv2.imread("person.jpg")

# Add text
cv2.putText(img, "Hello World", (50, 50),
            cv2.FONT_HERSHEY_SIMPLEX,
            1, (0, 255, 0), 2)

```

This will display:

Happy
[ face rectangle ]
Common Fonts
cv2.FONT_HERSHEY_SIMPLEX
cv2.FONT_HERSHEY_COMPLEX
cv2.FONT_HERSHEY_DUPLEX
