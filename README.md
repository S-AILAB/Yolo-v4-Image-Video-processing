<!DOCTYPE html>
<html>

<head>
    <title>YOLOv4 Object Detection Project</title>
</head>

<body>
    <h1>YOLOv4 Object Detection Project</h1>
    <p>This project demonstrates the use of YOLOv4 for object detection on images, videos, and custom-trained datasets.</p>

    <h2>Project Overview</h2>
    <p>This project uses YOLOv4 to detect objects in a provided image, videos, and a custom-trained model for detecting Squirrels. The outputs include the detected objects highlighted in the image, videos, and the new custom-trained model.</p>

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

    <h2>Object Detection with YOLOv4</h2>
    <p>This project consists of three Jupyter Notebooks for different object detection tasks:</p>

    <h3>1. Image Object Detection - <code>Yolov4_img.ipynb</code></h3>
    <p>This notebook performs object detection on a single image (e.g., <code>market.jpg</code>) using the YOLOv4 model. It takes an input image, performs detection, and saves the output with highlighted objects.</p>
    <p>To run this notebook, open <a href="https://colab.research.google.com/github/S-AILAB/Yolo-v4-Image-Video-processing/blob/main/Yolov4_img.ipynb" target="_blank">Yolov4_img.ipynb</a> and follow the instructions provided to detect objects in images.</p>
    <p>Example command for image detection:</p>
    <pre><code>./darknet detector test cfg/coco.data cfg/yolov4.cfg yolov4.weights market.jpg -out_filename market_output.jpg -thresh 0.7</code></pre>

    <h3>2. Video Object Detection - <code>Yolo_4v_Video.ipynb</code></h3>
    <p>This notebook performs object detection on video files (e.g., <code>test.mp4</code> and <code>cars(1).mp4</code>) using the YOLOv4 model. The model will process the video, detect objects frame-by-frame, and save the output with detected objects highlighted in each frame.</p>
    <p>To run this notebook, open <a href="https://colab.research.google.com/github/S-AILAB/Yolo-v4-Image-Video-processing/blob/main/Yolo_4v_Video.ipynb" target="_blank">Yolo_4v_Video.ipynb</a> and follow the instructions to detect objects in videos.</p>
    <p>Example command for video detection:</p>
    <pre><code>./darknet detector demo cfg/coco.data cfg/yolov4.cfg yolov4.weights -dont_show test.mp4 -i 0 -out_filename test_output.mp4 -thresh 0.7</code></pre>

    <h3>3. Custom Dataset Object Detection - <code>Yolo_Custom_dataset_training_Squirrel.ipynb</code></h3>
    <p>This notebook demonstrates how to train YOLOv4 on a custom dataset (e.g., for detecting Squirrels). It uses a custom dataset and pre-trained weights to fine-tune the model for your specific object class. The trained model can then be used to detect objects from the custom dataset.</p>
    <p>To run this notebook, open <a href="https://colab.research.google.com/github/S-AILAB/Yolo-v4-Object-Detection-Img-and-Video/blob/main/Yolo_Custom_dataset_training_Squrriel.ipynb" target="_blank">Yolo_Custom_dataset_training_Squirrel.ipynb</a> and follow the instructions to create your own dataset, train the model, and use it for custom object detection.</p>

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


num = 1
names = data/obj.names
train = data/train.txt
valid = data/test.txt
backup = backup/
</code></pre>
        </li>
    </ul>

    <h3>3. Start Training the Model</h3>
    <p>To train your custom model, run the following command:</p>
    <pre><code>./darknet detector train obj.data cfg/yolov4_squirrel.cfg yolov4.conv.137 -dont_show -map</code></pre>
    <p>The command will start training the model using the YOLOv4 architecture. The model will be trained on your custom dataset of Squirrel images and saved periodically in the <code>backup/</code> folder as <code>yolov4_squirrel.weights</code> or <code>yolov4_squirrel_last.weights</code>.</p>

    <h3>4. Using the Custom Trained Weights</h3>
    <p>Once training is complete, you can use the trained model to detect Squirrels in images or videos using the following command:</p>
    
    <h4>For Image Detection</h4>
    <pre><code>./darknet detector test obj.data cfg/yolov4_squirrel.cfg backup/yolov4_squirrel.weights market.jpg -out_filename market_output.jpg -thresh 0.7</code></pre>

    <h4>For Video Detection</h4>
    <pre><code>./darknet detector demo obj.data cfg/yolov4_squirrel.cfg backup/yolov4_squirrel.weights -dont_show test.mp4 -i 0 -out_filename test_output.mp4 -thresh 0.7</code></pre>

    <h3>Downloading Squirrel Images for Dataset</h3>
    <p>You can download Squirrel images from various online sources to create your custom dataset. Below is a list of URLs that you can use to download the images:</p>
    
    <ul>
        <li><a href="https://www.thewestmorlandgazette.co.uk/resources/images/11254999/" target="_blank">Squirrel Image 1</a></li>
        <li><a href="https://i.pinimg.com/originals/ea/32/9e/ea329e95906a2e67611c225a251c0a31.jpg" target="_blank">Squirrel Image 2</a></li>
        <li><a href="https://i.pinimg.com/originals/90/06/20/9006206d927e9a327218c14b60a0c23f.jpg" target="_blank">Squirrel Image 3</a></li>
    </ul>

    <h2>Developed by Siddharth Jain</h2>
</body>

</html>
