# Vehicle Speed Detection

![output.gif](output.gif)

Technologies used :

-   Python
-   opencv
-   dlib
    <br>

Tasks breakdown

1. Vehicle Detection
    - We are using Haarcascade classifier to identify vehicles.
2. Vehicle Tracking - ( assigning IDs to vehicles )
    - We have used corelation tracker from dlib library.
3. Speed Calculation
    - We are calculating the distance moved by the tracked vehicle
      in a second, in terms of pixels, so we need pixel per meter
      to calculate the distance travelled in meters.
    - With distance travelled per second in meters, we will get the
      speed of the vehicle.

### Features

YOLOv8 Object Detection with DeepSORT Tracking(ID + Trails)

### Dataset Used

> ⁠which dataset -> stats of the dataset, how many images etc. and that it’s widely used…

_pls fill_

### Model Details

> ⁠⁠which model was used and technical details about the model

_YOLO-V8._ (add more details)

### Problem Statement

> ⁠why the model is useful (i.e. what problem is it solving and how is it benefiting mankind)

Helps to detect potholes

### Model Pros...

> ⁠why the particular model selected by us is great (high high accuracy, state of the art, low inference time)

_fill_

## How to run project?

Follow steps:

1. Clone repo :
   `git clone ...`

2. cd (change directory) into vehicle-speed-check
   `cd 3_Vehicle-Speed-Check-Estimator`

3. Create virtual environment
   `conda create -n speed-estimator python=3.8`

4. Activate virtual environment
   `conda activate speed-estimator`

5. Install requirements
   `pip install dlib`
   `pip install opencv-python`

6. run speed_check.py script
   `python speed_check.py`

#### Note:

##### Estimating Pixels Per Metre (PPM)

The estimation of Pixels Per Metre (PPM) is a crucial step for speed calculation in our project. This process is manually performed for each specific road, as PPM values can vary significantly from one road to another. Therefore, when applying this method to different videos, adjustments to the PPM value are necessary.

##### How PPM is Estimated

The estimation involves two key measurements:

1. **Actual Road Width in Metres**: This is obtained through online resources, such as Google, to find an approximate width of the road in your country.
2. **Road Width in Pixels**: By analyzing a frame from our video footage, we determine the width of the road in pixels.

With these two measurements, we map real-world distances to those in our video frame. Pixels Per Metre (PPM) is then calculated by dividing the road width in pixels by its width in metres.

##### Calculating Speed

To estimate the speed of a vehicle, we follow these steps:

1. **Determine Pixel Distance (d_pixels)**: This represents the distance travelled by the vehicle in one frame of our video.
2. **Convert d_pixels to Metres (d_metres)**: Using our PPM value, we convert the pixel distance to metres.
3. **Calculate Speed**: The formula used is `speed = d_metres * fps * 3.6`. Here, `d_metres` is the distance travelled in one frame, and `fps` is the average frames per second obtained during video processing. The speed is initially calculated in metres per second (m/s) and then converted to kilometres per hour (km/hr) by multiplying with 3.6.
