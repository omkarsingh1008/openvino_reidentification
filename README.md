# Multi Camera Multi Target Python\* Demo

### Installation of Dependencies

To install required dependencies, run

```bash
pip3 install -r requirements.txt
```
```
usage: multi_camera_multi_target_tracking_demo.py [-h] -i INPUT [INPUT ...]
                                                  [--loop] [--config CONFIG]
                                                  [--detections DETECTIONS]
                                                  [-m M_DETECTOR]
                                                  [--t_detector T_DETECTOR]
                                                  [--m_segmentation M_SEGMENTATION]
                                                  [--t_segmentation T_SEGMENTATION]
                                                  --m_reid M_REID
                                                  [--output_video OUTPUT_VIDEO]
                                                  [--history_file HISTORY_FILE]
                                                  [--save_detections SAVE_DETECTIONS]
                                                  [--no_show] [-d DEVICE]
                                                  [-l CPU_EXTENSION]
                                                  [-u UTILIZATION_MONITORS]

Multi camera multi object tracking live demo script

optional arguments:
  -h, --help            show this help message and exit
  -i INPUT [INPUT ...], --input INPUT [INPUT ...]
                        Input sources (indexes of cameras or paths to video
                        files)
  --loop                Optional. Enable reading the input in a loop
  --config CONFIG       Configuration file
  --detections DETECTIONS
                        JSON file with bounding boxes
  -m M_DETECTOR, --m_detector M_DETECTOR
                        Path to the object detection model
  --t_detector T_DETECTOR
                        Threshold for the object detection model
  --m_segmentation M_SEGMENTATION
                        Path to the object instance segmentation model
  --t_segmentation T_SEGMENTATION
                        Threshold for object instance segmentation model
  --m_reid M_REID       Path to the object re-identification model
  --output_video OUTPUT_VIDEO
                        Optional. Path to output video
  --history_file HISTORY_FILE
                        Optional. Path to file in JSON format to save results
                        of the demo
  --save_detections SAVE_DETECTIONS
                        Optional. Path to file in JSON format to save bounding
                        boxes
  --no_show             Optional. Don't show output
  -d DEVICE, --device DEVICE
  -l CPU_EXTENSION, --cpu_extension CPU_EXTENSION
                        MKLDNN (CPU)-targeted custom layers.Absolute path to a
                        shared library with the kernels impl.
  -u UTILIZATION_MONITORS, --utilization_monitors UTILIZATION_MONITORS
                        Optional. List of monitors to show initially.
```

Minimum command examples to run the demo for person tracking (for vehicle tracking the commands are the same with appropriate vehicle detection/re-identification models):

```sh
# videos
python multi_camera_multi_target_tracking_demo.py \
    -i <path_to_video>/video_1.avi <path_to_video>/video_2.avi \
    --m <path_to_model>/person-detection-retail-0013.xml \
    --m_reid <path_to_model>/person-reidentification-retail-0277.xml \
    --config configs/person.py

# videos with instance segmentation model
python multi_camera_multi_target_tracking_demo.py \

https://user-images.githubusercontent.com/48081267/165576266-8d45287b-1456-4d89-bc16-fdc3390fee6f.mp4


    -i <path_to_video>/video_1.avi <path_to_video>/video_2.avi \
    --m_segmentation <path_to_model>/instance-segmentation-security-0228.xml \
    --m_reid <path_to_model>/person-reidentification-retail-0277.xml \
    --config configs/person.py

# webcam
python multi_camera_multi_target_tracking_demo.py \
    -i 0 1 \
    --m_detector <path_to_model>/person-detection-retail-0013.xml \
    --m_reid <path_to_model>/person-reidentification-retail-0277.xml \
    --config configs/person.py
```

