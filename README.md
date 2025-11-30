# Ex05 Image Carousel


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

## App.jsx
```
import React, { useState } from "react";
import "./App.css";

function App() {
  const images = [
    "https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=900&q=60", // Ocean sunset
    "https://images.unsplash.com/photo-1501973801540-537f08ccae7b?auto=format&fit=crop&w=900&q=60", // Beach evening
    "https://images.unsplash.com/photo-1500375592092-40eb2168fd21?auto=format&fit=crop&w=900&q=60", // Waves
    "https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=900&q=60"  // Sea horizon
  ];

  const [index, setIndex] = useState(0);

  const nextImage = () => {
    setIndex((prevIndex) => (prevIndex + 1) % images.length);
  };

  const prevImage = () => {
    setIndex((prevIndex) => (prevIndex - 1 + images.length) % images.length);
  };

  return (
    <div className="carousel">
      <h2>🌅 Sunset & Sea Carousel 🌊</h2>
      <div className="carousel-container">
        <button className="arrow left" onClick={prevImage}>❮</button>
        <img src={images[index]} alt="Sunset Sea" className="carousel-image" />
        <button className="arrow right" onClick={nextImage}>❯</button>
      </div>
    </div>
  );
}

export default App;
```

## App.css
```
body {
  background: linear-gradient(to bottom, #001f3f, #0074d9);
  height: 100vh;
  margin: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: "Segoe UI", sans-serif;
}

.carousel {
  text-align: center;
  color: white;
}

.carousel-container {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}

.carousel-image {
  width: 600px;
  height: 350px;
  object-fit: cover;
  border-radius: 20px;
  box-shadow: 0 0 25px rgba(0, 0, 0, 0.5);
}

.arrow {
  background: rgba(255, 255, 255, 0.3);
  border: none;
  font-size: 2.5rem;
  color: white;
  cursor: pointer;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  border-radius: 50%;
  padding: 10px 15px;
  transition: background 0.3s;
}

.arrow:hover {
  background: rgba(255, 255, 255, 0.5);
}

.left {
  left: -60px;
}

.right {
  right: -60px;
}
```

## OUTPUT

<img width="1918" height="1195" alt="image" src="https://github.com/user-attachments/assets/ac414573-898f-4f8c-929c-3daf7a6d33fa" />
<img width="1918" height="1198" alt="image" src="https://github.com/user-attachments/assets/1fc47dc3-10ac-45ff-874e-eca31c6c78f6" />
<img width="1916" height="1197" alt="image" src="https://github.com/user-attachments/assets/3b7e179f-331b-4ea7-9126-b4e3b6392f11" />
<img width="1913" height="1193" alt="image" src="https://github.com/user-attachments/assets/de385745-0813-413f-857f-0f4d7239faa4" />

## RESULT
The program for creating Image Carousel using React is executed successfully.
