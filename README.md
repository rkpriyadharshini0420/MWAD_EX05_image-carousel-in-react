# MWAD_EX05_image-carousel-in-react
## Date:17-11-2025

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
App.jsx
```
import React, { useState, useEffect } from "react";

const ImageCarousel = () => {
  const images = [
    "https://picsum.photos/id/1015/800/450",
    "https://picsum.photos/id/1025/800/450",
    "https://picsum.photos/id/1035/800/450",
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  // Next image
  const nextImage = () => {
    setCurrentIndex((prev) => (prev + 1) % images.length);
  };

  // Previous image
  const prevImage = () => {
    setCurrentIndex((prev) => (prev - 1 + images.length) % images.length);
  };

  // Auto-rotation
  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval);
  }, []);

  return (
    <div style={{ textAlign: "center", width: "100%" }}>
      <h2>Image Carousel</h2>

      <img
        src={images[currentIndex]}
        alt="carousel"
        style={{
          width: "800px",
          height: "450px",
          borderRadius: "10px",
          objectFit: "cover",
        }}
      />

      <div style={{ marginTop: "20px" }}>
        <button onClick={prevImage}>Previous</button>
        <button onClick={nextImage} style={{ marginLeft: "20px" }}>
          Next
        </button>
      </div>
    </div>
  );
};

export default ImageCarousel;
```

## OUTPUT
<img width="1536" height="1024" alt="carousal" src="https://github.com/user-attachments/assets/7dcca936-0e83-47a6-b7c4-c04a87057408" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
