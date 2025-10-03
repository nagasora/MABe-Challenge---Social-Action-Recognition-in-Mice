# MABe-Challenge---Social-Action-Recognition-in-Mice
Overview: In this competition, you’ll develop machine learning models to recognize behaviors in mice based on their movements, providing new insights into animal social structures and advancing behavioral science research.

Description:
Animal social behavior is complex. Species from ants to wolves to mice form social groups where they build nests, raise their young, care for their groupmates, and defend their territory. Studying these behaviors teaches us about the brain and the evolution of behavior, but the work has usually required subjective, time-consuming documenting of animals' actions. ML advancements now let us automate this process, supporting large-scale behavioral studies in the wild and in the lab.

But even automated systems suffer from limited training data and poor generalizability. In current methods, an experimenter must hand-label hundreds of new training examples to automate recognition of a new behavior, which makes studying rare behaviors a challenge. And models trained within one research group usually fail when applied to data from other studies, meaning there is no guarantee that two labs are really studying the same behavior.

This competition challenges you to build models to identify over 30 different social and non-social behaviors in pairs and groups of co-housed mice, based on markerless motion capture of their movements in top-down video recordings. The dataset includes over 400 hours of footage from 20+ behavioral recording systems, all carefully labeled frame-by-frame by experts. Your goal is to recognize these behaviors as accurately as a trained human observer while overcoming the inherent variability arising from the use of different data collection equipment and motion capture pipelines.

Your work will help scientists automate behavior analysis and better understand animal social structures. These models may be deployed across numerous labs, in neuroscience, computational biology, ethology, and ecology, to create a foundation for future ML and behavior research.

Evaluation:
This competition uses an F-Score variant as the metric. The F scores are averaged across each lab, each video, and score only the specific behaviors and mice that were annotated for a specific video. You may wish to review the full implementation here.

Submission File
You must create a row in the submission file for each discrete action. The file should contain a header and have the following format:

row_id,video_id,agent_id,target_id,action,start_frame,stop_frame
0,101686631,mouse1,mouse2,sniff,0,10
1,101686631,mouse2,mouse1,sniff,15,16
2,101686631,mouse1,mouse2,sniff,30,40
3,101686631,mouse2,mouse1,sniff,55,65

Dataset Description
Annotating the behavior of mice is currently a tremendously time consuming behavior. This competition challenges you to automate this process and unlock new insights into animal behavior.

This competition uses a hidden test set. When your submitted notebook is scored, the actual test data (including a full length sample submission) will be made available to your notebook. Expect to see roughly 200 videos in the hidden test set.

Files
[train/test].csv Metadata about the mice and recording setups.

lab_id - The pseudonym of the lab that provided the data. The CalMS21, CRIM13, and MABe22 datasets are copies of publicly available datasets provided as additional training data. Some tracking files in CalMS21 set are largely duplicated-- these were annotated by multiple individuals for different sets of behaviors.
video_id - A unique identifier for the video.
mouse[1-4] [strain/color/sex/id/age/condition] - Basic information about each mouse.
frames per second
video duration (sec)
pix per cm (approx)
video [width/height]
arena [width/height] (cm)
arena shape
arena type
body parts tracked - Each lab used different technology to track their mice, so the specific body parts tracked may vary.
behaviors labeled - The behaviors labeled in this video. Necessary as the annotations are sparse. Each lab annotated their videos differently, may not have annotated all behaviors for a video, and may not have annotated all mice in each video.
tracking method - The model used to track the animal's pose.
[train/test]_tracking/ The feature data.

video_frame
mouse_id
bodypart - The tracked body part. Different labs may track different body parts
[x/y] - The body part's X/Y coordinate position in pixels.
train_annotation/ Train labels.

agent_id - ID of the mouse performing the behavior.
target_id - ID of the mouse targeted by the behavior. Some behaviors, such as a mouse grooming itself, have the same agent and target ID.
action - What behavior is occurring (e.g., grooming, chasing). Different labs annotated different behaviors.
[start/stop]_frame - The first/last frame of the action.
sample_submission.csv A submission file in the correct format.

row_id - You'll need to provide a column of unique row IDs. A simple enumeration will suffice.
video_id
agent_id
target_id
action
[start/stop]_frame
