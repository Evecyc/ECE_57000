# ECE 57000 Course Project README

## Project
This project is a tiny reproduction of Focal Loss under imbalanced classification using CIFAR-10.

The main goal is to test whether the core idea of Focal Loss still works in a simplified classification setting with strong class imbalance.

---

## Files

- `Focal.ipynb`: main notebook for all experiments
- `README.md`: project instructions and notes
- `paper.pdf`: final report 

---

## Code structure

The notebook is organized in this order:

1. imports and random seed setup  
2. imbalanced CIFAR-10 construction  
3. model and loss functions  
4. training / evaluation functions  
5. experiment setup  
6. result table and plots  

Main parts of the code:
- building the imbalanced CIFAR-10 dataset
- implementing focal loss with `gamma` and `alpha`
- computing minority accuracy and macro-F1
- running multi-seed comparisons
- summarizing results into tables and plots

---

## Dependencies

This project uses:

- Python 3
- torch
- torchvision
- numpy
- pandas
- matplotlib

Example install:
```bash
pip install torch torchvision numpy pandas matplotlib
```

---

## How to run

### Google Colab
1. Upload `Focal.ipynb`
2. Turn on GPU
3. Run all cells from top to bottom

### Local Jupyter
1. Install the packages above
2. Open `Focal.ipynb`
3. Run all cells in order

---

## Dataset and model download

- The dataset is CIFAR-10 (automatically downloaded)
- No pretrained model is used
- ResNet-18 is initialized from scratch

---

## Which parts were written by me

The following parts were written by me for this project:
- imbalanced CIFAR-10 sampling
- focal loss implementation
- alpha-balanced focal loss implementation
- macro-F1 computation
- training / evaluation pipeline
- fair comparison with shared initialization
- multi-seed result aggregation
- final plotting and result tables

---

## Adapted / external code

I used library components only, no copied repository code.

This project uses standard components from PyTorch / torchvision:
- `torchvision.datasets.CIFAR10`
- `torchvision.models.resnet18`
- standard PyTorch training utilities

---

## Main experiment setting

- Dataset: CIFAR-10
- Imbalance ratio: about 50:1
- Model: ResNet-18
- Epochs: 30
- Seeds: 3

Methods compared:
- Cross-Entropy
- Focal Loss (`gamma = 1, 2`)
- Focal Loss with `alpha = 10`
- Focal Loss with `alpha = 25`

Metrics:
- Minority Accuracy
- Macro-F1

---

## Main findings

- Focal Loss with `gamma = 1` improves over Cross-Entropy
- Larger `gamma` hurts performance
- `alpha = 10` gives the best overall result
- `alpha = 25` improves minority accuracy but hurts balance overall
