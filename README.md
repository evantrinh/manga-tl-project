# Manga Speech Balloon Detection

Project for CS 435 @ Drexel. Winter 2026.

An automated image processing pipeline that detects and isolates speech bubbles in raw comic pages. This project frames the task as semantic segmentation to predict a pixel-level mask of speech bubble regions. 

## Architecture
The model implements a U-Net architecture with a VGG-16 encoder pretrained on ImageNet. The decoder is trained from scratch using Dice loss to optimize the overlap between prediction and ground truth masks. 

## Pipeline Steps
1. Generate a pixel-level segmentation mask using the trained U-Net model.
2. Crop the detected text regions from the original image.
3. Extract characters using a transformer optical character recognition model trained on manga fonts.
4. Translate the raw text via the Google Translate API.
5. Overlay the translated English text onto the image utilizing OpenCV.

## Performance
The model achieved an F1 score of 0.975 on the validation set after training on an NVIDIA T4 GPU. 