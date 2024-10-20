# OwlSAM
A one shot instance segmentation approach combining Owl-v2 and SAM.



The goal of this project is provide a workflow for one-shot instance segmentation without the need of text prompting , it solely focuses on detecting  objects on the target images similar to the image prompt. For more details on how the Owl-v2 transformer works check out https://huggingface.co/docs/transformers/model_doc/owlv2 

The main components of this project include:

OWL-v2 for Object Detection: Utilizing the OWL-v2 model from Hugging Face's transformers library for zero-shot object detection. This model is well-suited for detecting a wide range of object categories without needing to be retrained for specific tasks.

SAM (Segment Anything Model) for Segmentation: SAM is integrated to perform segmentation tasks on the images, which allows you to delineate specific regions within the detected objects. It uses bounding boxes detected from Owl-v2 to generate these segmentations.



The project is meant to be as user-friendly as possible all neccesary installments are done through it.
A few notes before running :
1) Make sure to change the paths , since the project was developed in a google colab environment.
2) Make sure to experiment with the different thresholds when using with your own dataset , the model's thresholds are tuned for my  "control" dataset which is provided in this repo.
3) As of now the selection of the best part of the query  to crop (as you will in the notebook) is done manually so make sure to observe how you crop the prompts.
4) Although I am using the large SAM model the project should run with other checkpoints as well.Same goes for Owl-v2.


A few notes on the thresholds:
1) NMS for bounding boxes used for filtering out overlapping boxes
   
2) NMS for segmentation masks used for filtering out overlapping masks
   
3) Tolerance used to filter out bounding boxes based on confidence relative to best detection score
   
4) Area threshold  with value of  areams.mean() - std_multiplier*areas.std() used to filter out detections of bboxes that are too large.
   
5) There are a few more thresholds implemented for example height filtering that are unused feel free to experiment with those as well.


Examples and results.

Prompt:
![rgb_00110](https://github.com/user-attachments/assets/0a1fbbad-fd45-441e-bb83-80292b8d37ae)






A few of the best results:





![λήψη (2)](https://github.com/user-attachments/assets/d1f28542-1990-4b15-92a4-42c17fc73fbf)
![λήψη (3)](https://github.com/user-attachments/assets/e5f3d997-dbe6-43b8-9439-9e4c6b75bc9c)
![λήψη (4)](https://github.com/user-attachments/assets/1dc6f684-cc87-4878-ac9a-c740b572f711)





   
