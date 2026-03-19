# CIFAR10_Image_classification

A deep learning project for classifying images from the CIFAR-10 dataset using a ResNet-18 model in PyTorch. The project covers data preprocessing, training, fine-tuning, model evaluation, and test-time augmentation to improve classification performance.

## Project Overview

This project uses the CIFAR-10 dataset, which contains 60,000 color images across 10 classes:

- airplane
- automobile
- bird
- cat
- deer
- dog
- frog
- horse
- ship
- truck

The model was trained and refined in multiple stages:
- Initial training
- Fine-tuning
- Polish phase for further performance improvement

## Model

The project uses:

- **ResNet-18**
- Modified final fully connected layer for **10 output classes**
- Implemented in **PyTorch**

## Data Augmentation

Training transforms include:
- Random cropping
- Random horizontal flipping
- AutoAugment for CIFAR-10
- Normalization

Test transforms include:
- Tensor conversion
- Normalization

## Training Setup

- **Batch size:** 64
- **Initial epochs:** 100
- **Fine-tuning epochs:** 100
- **Polish epochs:** 200
- **Optimizer:** SGD with momentum and Nesterov
- **Weight decay:** 5e-4
- **Scheduler:** Cosine Annealing LR
- **Loss function:** CrossEntropyLoss with label smoothing

## Results

### Best accuracies achieved:
- **Best fine-tuned model:** 89.52%
- **Best polished model:** 90.07%

The best model checkpoint was saved as:

- `best_resnet_cifar10.pt`
- `best_resnet_cifar10_ft.pt`
- `best_resnet_cifar10_polish.pt`

## Test-Time Augmentation

The project also uses **Test-Time Augmentation (TTA)** by averaging predictions from:
- Original images
- Horizontally flipped images

This helps improve evaluation robustness.

## Files

- `cifar10_resnet.ipynb` — main notebook with training and evaluation


## Dataset

This project uses the **CIFAR-10** dataset.  
The dataset is automatically downloaded through `torchvision.datasets.CIFAR10`.

Example:

```python
train_dataset = torchvision.datasets.CIFAR10(
    root="./data",
    train=True,
    download=True,
    transform=train_tfms
)
