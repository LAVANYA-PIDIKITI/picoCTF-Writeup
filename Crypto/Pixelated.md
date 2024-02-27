# Pixelated
AUTHOR: SARA

Description
I have these 2 images, can you make a flag out of them? scrambled1.png scrambled2.png
# Solution:
Use the below program to decrypt as in to stack the images properly
```python
from PIL import Image
import numpy as np
import os

file_names = ["scrambled1.png", "scrambled2.png"]
img_data = [np.asarray(Image.open(f'{name}')) for name in file_names]

data = img_data[0].copy() + img_data[1].copy()

new_image = Image.fromarray(data)
new_image.save("out.png", "PNG")
```
![image](https://github.com/LAVANYA-PIDIKITI/picoCTF-Writeup/assets/98797256/622ec70b-a40a-4af4-8c94-25d50a14b13b)
