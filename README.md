# VR_Assignment1_BysaniAkshaya_IMT2022579

Assignment is done in google colab.

## Part 1 : Use computer vision techniques to Detect, segment, and count coins from an image containing scattered Indian coins.

### a. Detecting all coins in the image.

#### Preprocessing 
- Loading the input image
  
- ![image](https://github.com/user-attachments/assets/a363d1c0-62b5-40c0-b382-9b786c4177e9)
  
- Converting the image into **grayscale**.
  
- ![image](https://github.com/user-attachments/assets/f17d5af6-6618-496a-a6f6-9455e39076f0)
  
- Applying **gaussian blur** with parameters grayscaled image, kernel size (5, 5), standard deviation 0 to smooth the image.
  
- ![image](https://github.com/user-attachments/assets/d20cd52d-7247-4c80-a383-82ea58d37b5a)

- **Otsu's thresholding** is used to binarize the image, converting it into a black-and-white format for easier segmentation.
- **Morphological closing** is applied to remove small holes and improve segmentation quality.

- ![image](https://github.com/user-attachments/assets/e60d3ce9-d16d-4072-a88d-325bf57b1115).
 
- **Canny edge detection** is used to find the edges of coins in the image.

- ![image](https://github.com/user-attachments/assets/f82c6c58-10ed-4003-aee5-d0cb19a08cfc)

- Contours are detected from the thresholded image to locate the coins using the inbuilt cv2 functions **findContours** and **drawContours**.

- ![image](https://github.com/user-attachments/assets/9415566e-b8fd-403b-b214-878fa6b54bf4)

### b. Segmentation of each coin.

Here segmentation has been performed using two methods:

#### Method 1: Contour based segmentation
- Uses contour area and convex hull to refine the detected coins and segment them.
- Helps in ensuring smooth boundaries by using convex hull operations.
- Filters out small noise by considering only contours within a specific area range.
- Crops and extracts individual coin images based on the bounding box of the contour.

#### Method 2: Region growing segmentation
- Uses flood fill to segment the coins based on pixel connectivity.
- Selects a seed point within the image to initiate the region-growing process.
- Expands regions by considering neighboring pixels with similar intensity values.
- Extracts segmented coins by applying the mask obtained from the flood fill operation.
- Helps in detecting connected components in cases where coin edges are not well-defined.

- **Output: Segmenting each coin**

<p align="center">
  <img src="output/coin1.png" width="7%" />
  <img src="output/coin2.png" width="7%" />
  <img src="output/coin3.png" width="7%" />
  <img src="output/coin4.png" width="7%" />
  <img src="output/coin5.png" width="7%" />
  <img src="output/coin6.png" width="7%" />
  <img src="output/coin7.png" width="7%" />
  <img src="output/coin8.png" width="7%" />
  <img src="output/coin9.png" width="7%" />
  <img src="output/coin10.png" width="7%" />
  <img src="output/coin11.png" width="7%" />
  <img src="output/coin12.png" width="7%" />
</p>

### c. Counting number of coins in the image

Each contour identify belongs to a different coin. Therefore, number of coins will be equal to the number of contours ientified.
