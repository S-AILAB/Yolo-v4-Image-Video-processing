<!DOCTYPE html>
<html>
<head>
    <title>YOLOv4 Object Detection Project</title>
</head>
<body>
    <h1>YOLOv4 Object Detection Project</h1>
    <p>This project demonstrates the use of YOLOv4 for object detection on images and videos.</p>

    <h2>Project Overview</h2>
    <p>This project uses YOLOv4 to detect objects in a provided image and videos. The outputs include the detected objects highlighted in the image and videos.</p>

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
    <p>To detect objects in an image, use the following command:</p>
    <pre><code>!./darknet detector test cfg/coco.data cfg/yolov4.cfg yolov4.weights market.jpg -out_filename market_output.jpg -thresh 0.7</code></pre>

    <h3>Video Object Detection</h3>
    <p>To detect objects in a video, use the following commands:</p>
    <pre><code>!./darknet detector demo cfg/coco.data cfg/yolov4.cfg yolov4.weights -dont_show test.mp4 -i 0 -out_filename test_output.mp4 -thresh 0.7</code></pre>
