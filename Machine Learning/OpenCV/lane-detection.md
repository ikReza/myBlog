<h1 style="color:tomato; display:flex; justify-content:center">Line Detection</h1>

We'll use **Hough transorm** method to detect lines.<br/>

> Prerequisite libraries:
>
> > matplotlib
>
> > numpy
>
> > opencv-python

Let's see the code:

```python
import matplotlib.pyplot as plt
import numpy as np
import cv2
```

```python
image = cv2.imread("sudoku.jpg")
image = cv2.resize(image, (1200, 650))
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
edges = cv2.Canny(gray, 50, 150, apertureSize=3)
#cv2.imshow("image", edges)
```

Now we can use two methods:

- The Sandard Hough Transform (HoughLines( ) method)
- The Probabilistic Hough Transform (HoughLinesP( ) method)

<input placeholder="write something" type="text" id="pass"/>
<button onclick="cond()">FB</button>
