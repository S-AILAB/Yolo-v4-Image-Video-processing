<!DOCTYPE html>
<html>
   
</head>
<body>
    <h1>YOLOv4 Object Detection Project</h1>
    <p>This project demonstrates the use of YOLOv4 for object detection on images and videos.</p>

    <h2>Project Overview</h2>
    <p>This project uses YOLOv4 to detect objects in a provided image named <code>market.jpg</code> and videos named <code>test.mp4</code> and <code>cars(1).mp4</code>. The outputs include the detected objects highlighted in the image and videos.</p>

    <h2>Installation</h2>
    <ol>
        <li>Clone the YOLOv4 repository and navigate to the project directory:
            <pre><code>git clone https://github.com/AlexeyAB/darknet.git
cd darknet</code></pre>
        </li>
        <li>Compile the Darknet framework:
            <pre><code>make</code></pre>
        </li>
        <li>Download the pre-trained YOLOv4 weights:
            <pre><code>wget https://github.com/AlexeyAB/darknet/releases/download/yolov4/yolov4.weights</code></pre>
        </li>
    </ol>

    <h2>Usage</h2>
    <h3>Image Object Detection</h3>
    <p>To detect objects in an image named <code>market.jpg</code>, use the following command:</p>
    <pre><code>!./darknet detector test cfg/coco.data cfg/yolov4.cfg yolov4.weights market.jpg -out_filename market_output.jpg -thresh 0.7</code></pre>

    <h3>Video Object Detection</h3>
    <p>To detect objects in the video named <code>test.mp4</code>, use the following command:</p>
    <pre><code>!./darknet detector demo cfg/coco.data cfg/yolov4.cfg yolov4.weights -dont_show test.mp4 -i 0 -out_filename test_output.mp4 -thresh 0.7</code></pre>
    
    <p>To detect objects in the video named <code>cars(1).mp4</code>, use the following command:</p>
    <pre><code>!./darknet detector demo cfg/coco.data cfg/yolov4.cfg yolov4.weights -dont_show "cars(1).mp4" -i 0 -out_filename cars_output.mp4 -thresh 0.7</code></pre>

    <h3>Compressing the Output Videos</h3>
    <p>After generating the output videos, you can compress them using <code>ffmpeg</code>:</p>
    <pre><code>import os
from base64 import b64encode
from IPython.display import HTML

# Paths for test video
input_test_path = "test.mp4"
compressed_test_path = "output_compressed.mp4"

# Compress the test video using ffmpeg
os.system(f"ffmpeg -i {input_test_path} -vcodec libx264 {compressed_test_path}")

# Paths for car video
input_cars_path = "cars.mp4"
compressed_cars_path = "output_cars_compressed.mp4"

# Compress the car video using ffmpeg
os.system(f"ffmpeg -i {input_cars_path} -vcodec libx264 {compressed_cars_path}")</code></pre>

    <h2>Output Results</h2>
    <h3>Image Output</h3>
    <p>The detected objects in the image <code>market.jpg</code> are saved as <code>market_output.jpg</code>.</p>
    <img src="market_output.jpg" alt="Market Image Output" width="600">

    <h3>Video Output</h3>
    <p>The detected objects in the video <code>test.mp4</code> are saved as <code>test_output.mp4</code> and then compressed to <code>output_compressed.mp4</code>.</p>
    <p>The detected objects in the video <code>cars(1).mp4</code> are saved as <code>cars_output.mp4</code> and then compressed to <code>output_car_compressed.mp4</code>.</p>

    <h2>Display Video Results</h2>
    <h3>Test Video</h3>
    <video width="800" height="400" controls>
        <source src="output_compressed.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>

    <h3>Cars Video</h3>
    <video width="800" height="400" controls>
        <source src="output_car_compressed.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>

    <h2>Contributors</h2>
    <p>Project developed by [Your Name].</p>

    <h2>License</h2>
    <p>This project is licensed under the MIT License.</p>
</body>
</html>
