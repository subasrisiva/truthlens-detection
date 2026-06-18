### User Video Upload

```python
from flask import Flask, request

app = Flask(__name__)

@app.route('/upload', methods=['POST'])
def upload_video():
    video = request.files['video']
    video.save(video.filename)
    return "Video Uploaded Successfully"
```

### Video Frame Extraction

```python
import cv2

video = cv2.VideoCapture("sample.mp4")

while True:
    success, frame = video.read()
    if not success:
        break

    cv2.imwrite("frame.jpg", frame)
```

### Loading Machine Learning Model

```python
from tensorflow.keras.models import load_model

model = load_model("deepfake_model.h5")
```

### Video Prediction

```python
import numpy as np

frame = np.array(frame)
frame = frame.reshape(1, 224, 224, 3)

prediction = model.predict(frame)

if prediction > 0.5:
    result = "Fake Video"
else:
    result = "Real Video"

print(result)
```

### Display Result

```python
return {
    "Prediction": result,
    "Confidence Score": str(round(float(prediction[0][0]) * 100, 2)) + "%"
}
```

### React Video Upload Component

```javascript
import React, { useState } from "react";

function UploadVideo() {
  const [video, setVideo] = useState(null);

  const handleUpload = (e) => {
    setVideo(e.target.files[0]);
  };

  return (
    <input
      type="file"
      accept="video/*"
      onChange={handleUpload}
    />
  );
}

export default UploadVideo;
```
