# Cloud Video Intelligence API VS AWS Rekognition Video Inference

Today, I tested the GCP's Cloud Video Intelligence API and AWS Rekogniton Video Inference. I was able to deduce following points:

1. GCP and AWS both charge on per min basis for video inference.
2. During my tests on GCP for Logo Detection, I deduced that it performed detection of video_fps/3 fps. 
3. During my tests on AWS, different APIs performed inference on different FPS:
    * Celebrity identification inference on 2-3 fps
    * Labels detection on video_fps/2. 
