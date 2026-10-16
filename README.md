# Deep Learning Coursework

Coursework exercises exploring deep learning and related machine-learning methods with Keras, TensorFlow and scikit-learn.

## Notebooks

| Notebook | Dataset | Model | Training | Result |
| --- | --- | --- | --- | --- |
| [`CNN_MIST.ipynb`](CNN_MIST.ipynb) | MNIST | LeNet-5-style convolutional neural network | from scratch | Test accuracy 98.22% — from saved notebook output, not re-run |
| [`DL_EXP1.ipynb`](DL_EXP1.ipynb) | `placement.csv` | scikit-learn perceptron | from scratch | Test accuracy 75% — from saved notebook output, not re-run |
| [`DL_LAB_.ipynb`](DL_LAB_.ipynb) | `Life Expectancy Data.csv` | Dense neural-network regressor | from scratch | R² 96.09% — from saved notebook output, not re-run; this is a regression metric, not accuracy |
| [`DL_LAB_2.ipynb`](DL_LAB_2.ipynb) | `Churn_Modelling.csv` | Dense binary-classification neural network | from scratch | Test-set result not recorded |
| [`DL_LAB_3.ipynb`](DL_LAB_3.ipynb) | MNIST | Dense neural-network classifier | from scratch | Test accuracy not recorded in saved output |
| [`K_Fold_Cross_Validation.ipynb`](K_Fold_Cross_Validation.ipynb) | `Churn_Modelling.csv` | Dense binary-classification neural network with five-fold cross-validation | from scratch | Mean cross-validation accuracy 85.66% — from saved notebook output, not re-run |
| [`cifar10_from_scratch/VGG16_SCR.ipynb`](cifar10_from_scratch/VGG16_SCR.ipynb) | CIFAR-10 | VGG16-style convolutional neural network | from scratch | Not recorded for the saved checkpoints |
| [`cifar10_from_scratch/RESNET50.ipynb`](cifar10_from_scratch/RESNET50.ipynb) | CIFAR-10 | ResNet50-v1-style convolutional neural network adapted for 32×32 images | from scratch | Test accuracy 85.12% — from saved notebook output, not re-run |
| [`beans_transfer_learning/VGG And RESNET50.ipynb`](beans_transfer_learning/VGG%20And%20RESNET50.ipynb) | Beans | VGG16 and ResNet50 | transfer learning: ImageNet weights from Keras Applications, base frozen, new head trained | VGG16 test accuracy 84.38%; ResNet50 test accuracy 94.53% — from saved notebook output, not re-run |

## Results by dataset

- MNIST: LeNet-5-style CNN test accuracy 98.22% — from saved notebook output, not re-run. The dense classifier's test accuracy is not displayed in its saved output.
- Placement: perceptron test accuracy 75% — from saved notebook output, not re-run.
- Life Expectancy: R² 96.09% — from saved notebook output, not re-run. This is a regression metric and was measured on data also used for validation.
- Churn Modelling: mean five-fold cross-validation accuracy 85.66% — from saved notebook output, not re-run. The separate dense-classifier notebook has no test-set evaluation.
- CIFAR-10: ResNet50-style model test accuracy 85.12% — from saved notebook output, not re-run. A result for the saved VGG16 checkpoints is not recorded.
- Beans: VGG16 test accuracy 84.38% and ResNet50 test accuracy 94.53% — from saved notebook output, not re-run.

More detailed saved-output evidence is recorded in [`results.md`](results.md).

## Model files

The following trained model files are hosted on Hugging Face rather than stored in this repository:

| Model | Training | Licence |
| --- | --- | --- |
| [Beans VGG16](https://huggingface.co/faiz4320/beans-vgg16) | Transfer learning: ImageNet weights ported by Keras Applications, base frozen, new head trained, no fine-tuning. | `cc-by-4.0` |
| [Beans ResNet50](https://huggingface.co/faiz4320/beans-resnet50) | Transfer learning: ImageNet weights ported by Keras Applications, base frozen, new head trained, no fine-tuning. | `mit` |
| [CIFAR-10 ResNet50 from scratch](https://huggingface.co/faiz4320/cifar10-resnet50-scratch) | Trained from scratch, custom CIFAR-style ResNet50-v1, random init. | `mit` |

The other saved checkpoints—`best_vgg16_cifar10.keras`, `best_of_vgg16_cifar10.keras`, and `best_resnet50_cifar10.keras`—are not published because their results could not be tied to those specific files.

## Datasets

| Dataset | Availability and source | Licence |
| --- | --- | --- |
| `placement.csv` | Not included; source: not recorded | Not recorded |
| `Churn_Modelling.csv` | Not included; source: not recorded | Not recorded |
| `Life Expectancy Data.csv` | Not included; source: not recorded | Not recorded |
| MNIST | Downloaded through the Keras dataset loader | To be verified |
| CIFAR-10 | Downloaded through its loader; Krizhevsky and Hinton, University of Toronto | To be verified |
| Beans | Downloaded through its loader; Makerere AI Lab | To be verified |

## Known limitations

- `DL_LAB_.ipynb` uses the test split as validation data, including for early stopping. Its reported metrics are therefore not from an untouched test set. Its R² of 96.09% is a regression metric, not accuracy.
- `K_Fold_Cross_Validation.ipynb` standardises the full dataset before cross-validation, leaking information between folds.
- `DL_LAB_2.ipynb` has no test-set evaluation.
- `DL_LAB_3.ipynb` does not display its test accuracy in the saved output.
- Some notebooks retain harmless errors in saved output: a `NameError` in `VGG16_SCR.ipynb` and a `FileNotFoundError` in the Beans inference cell.
- Results were not re-run offline.

## Licences and credits

The VGG16 ImageNet weights are licensed under CC BY 4.0, and the ResNet50 ImageNet weights are licensed under MIT. Both weight sets were ported by Keras Applications.

## How this was built

Designed and specified by me; implemented with AI coding assistants (Codex and Claude); I review the code, run the experiments and direct the roadmap.

Published on: 2026-10-16
