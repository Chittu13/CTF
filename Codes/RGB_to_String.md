```py
from PIL import Image
import numpy as np

image_path = './secret_square.png'
img = Image.open(image_path).convert('RGB')

pixels = np.array(img)
print(pixels.shape)

sums = np.sum(pixels, axis=2)
print(sums.shape)

for row in sums:
    print(''.join([chr(x) for x in row]))
```
