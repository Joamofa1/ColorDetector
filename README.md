# PythonColorDetector  😜

## Tools and Libraries 

### Tools
- Install [python](https://www.geeksforgeeks.org/download-and-install-python-3-latest-version) 3.7 upwards 👋
- install any IDE but the preferred IDE used is [Visual Studio Code](https://code.visualstudio.com/download)


## Installing python packages and libraries
#### Required libraries 
- [openCV](https://pypi.org/project/opencv-python/) or simply `pip install cv2`
- [pandas](https://data-flair.training/blogs/pandas-tutorials-home/) or simply `pip install pandas`

### First import these libraries in your python IDE
- `import cv2`
- `import numpy as np`
- `import pandas as pd`
- `import argparse`

Import your image bu=y using the CV to read the image
try 
- `image = cv2.imread ("path/to/image.png")` or better still use the [link](https://www.pyimagesearch.com/2021/01/20/opencv-load-image-cv2-imread/#:~:text=To%20load%20an%20input%20image%20from%20disk%20using,cv2.imread%20function%20then%20returns%20either%20of%20two%20values%3A)

- now calling your functions 
# Creating argument parser to take image path from command line
`ap = argparse.ArgumentParser()`
`ap.add_argument('-i', '--image', required=True, help="Image Path")`
`args = vars(ap.parse_args())`
`img_path = args['image']`

# Reading the image with opencv
`img = cv2.imread(img_path)`

#declaring global variables (are used later on)
clicked = False
r = g = b = xpos = ypos = 0

# Reading csv file with pandas and giving names to each column
`index=["color","color_name","hex","R","G","B"]
csv = pd.read_csv('colors.csv', names=index, header=None)`

# function to calculate minimum distance from all colors and get the most matching color
`def getColorName(R,G,B):
    minimum = 10000
    for i in range(len(csv)):
        d = abs(R- int(csv.loc[i,"R"])) + abs(G- int(csv.loc[i,"G"]))+ abs(B- int(csv.loc[i,"B"]))
        if(d<=minimum):
            minimum = d
            cname = csv.loc[i,"color_name"]
    return cname`
 
