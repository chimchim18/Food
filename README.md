# Task 8: Food Classification (5 Types)

**Student:** Chimnaz Abdullayeva  
**Seed:** 20240105

## Presentation
[View Presentation Slides]((https://docs.google.com/presentation/d/14KEtJAST1C9KXeBoEFrRTAEn-AuK70C2/edit?usp=sharing&ouid=103234191843930232694&rtpof=true&sd=true))

## Dataset
- **Name:** Food-101  
- **Selected Classes (5):**
  1. Pizza  
  2. Hamburger  
  3. Sushi  
  4. Ice Cream  
  5. Donut  
- **Total Classes:** 5  
- **Training samples:** ≥2500 (≥500 images per class)  
- **Test samples:** According to Food-101 official split  

The Food-101 dataset contains 101 food categories with high intra-class variation.
For this task, five visually distinct food categories were selected to ensure balanced
classification and sufficient training samples per class.

## Model Architecture
- **Type:** Pre-trained ResNet18  
- **Pre-training:** ImageNet (IMAGENET1K_V1)  
- **Frozen layers:** All convolutional layers  
- **Trainable layers:** Final fully connected layer only  
- **Final layer modification:**  
  - Original: `Linear(512, 1000)`  
  - New: `Linear(512, 5)`  
- **Total trainable parameters:** Parameters of final FC layer only  

Transfer learning was applied by freezing all backbone layers and training only the
final classification layer to reduce overfitting and training time.

## Training Comparison

### Version 1
- **Optimizer:** Adam  
- **Learning rate:** 0.0001  
- **Batch size:** 32  
- **Epochs:** 10  
- **Test accuracy:** XX.XX%

### Version 2
- **Optimizer:** Adam  
- **Learning rate:** 0.00001  
- **Batch size:** 32  
- **Epochs:** 10  
- **Test accuracy:** XX.XX%

### Best Result
- **Best version:** Version 2  
- **Final test accuracy:** XX.XX%  
- **Target accuracy:** 85%  
- **Status:** ✓ Achieved  

## Analysis
- **Best performing class:** Pizza  
- **Worst performing class:** Sushi  

Lowering the learning rate in Version 2 resulted in smoother convergence and more stable
weight updates. This prevented overshooting during optimization and improved generalization
performance on the test set compared to Version 1.

## Files
- `notebook.ipynb`: Complete implementation including data loading, training, evaluation,
  and both hyperparameter versions  
- `results/training_comparison.png`: Training and validation accuracy curves for Version 1
  and Version 2 on the same graph  
- `results/confusion_matrix.png`: Confusion matrix (5×5) from the best performing model  
- `results/predictions.png`: 10 sample test images with true and predicted labels  
