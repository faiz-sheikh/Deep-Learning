# CIFAR-10 experiments

These notebooks train VGG16-style and ResNet50-v1-style classifiers from random initialization. They do not use Keras Applications or pretrained weights.

## Models

| Notebook | Exact model class | Architecture and initialization | Layers | Training | Data and preprocessing | Licence |
| --- | --- | --- | --- | --- | --- | --- |
| `VGG16_SCR.ipynb` | `tf.keras.Sequential` (not `tf.keras.applications.VGG16`); `include_top` not applicable | VGG16-style five convolutional blocks, five max pools, Flatten, Dense(4096), Dropout(0.5), Dense(4096), Dropout(0.5), Dense(10); random init / from scratch | All layers trainable; no frozen or fine-tuned pretrained layers | Adam, learning rate 0.0001; sparse categorical crossentropy; accuracy; batch 64; at most 20 epochs; checkpoint on `val_accuracy`; early stopping and LR reduction on `val_loss` | CIFAR-10, source: as stated in notebook or unverified; 32x32 RGB; scale pixels to [0,1]. This is the model's training preprocessing; an Applications `preprocess_input` does not apply. | VGG: CC BY 4.0 |
| `RESNET50.ipynb` | Custom `tf.keras.Model` returned by `build_resnet50`; `include_top` not applicable | CIFAR-10 adaptation of ResNet50 v1: 3-4-6-3 bottleneck stages, 3x3 stride-1 stem, no initial max pool, global average pool and Dense(10); random init / from scratch | All convolution and classifier layers trainable; batch-normalization moving statistics account for the non-trainable parameter count; no pretrained or fine-tuned layers | Adam, learning rate 0.001; sparse categorical crossentropy; accuracy; batch 64; at most 20 epochs; checkpoint on `val_accuracy`; early stopping and LR reduction on `val_loss` | CIFAR-10, source: as stated in notebook or unverified; 32x32 RGB; scale pixels to [0,1]. This is the custom model's training preprocessing; an Applications `preprocess_input` does not apply. | ResNet50 v1: MIT |

Both use the official 50,000-image training portion, split with `random_state=42` and stratification into 45,000 training and 5,000 validation examples. The official 10,000-image test split is used only for final evaluation. Test data is not used for tuning, early stopping, learning-rate changes, or checkpoint selection.

## Saved artifacts

- `best_vgg16_cifar10.keras` is explicitly produced by the VGG notebook's best-`val_accuracy` checkpoint.
- `best_of_vgg16_cifar10.keras` has the same serialized model configuration as the VGG notebook but is not named or saved by its code. Its mapping to that notebook is architectural inference; its exact producing run is unknown.
- `best_resnet50_cifar10.keras` is explicitly produced by the ResNet notebook's best-`val_accuracy` checkpoint.
- `resnet50_cifar10_final.keras` is explicitly saved by the ResNet notebook after its final test evaluation.

Model files are intentionally ignored and remain under `pretrained/_incoming/`. Checksums and evaluation evidence are in [`../results.md`](../results.md).

## Saved notebook outputs

- `VGG16_SCR.ipynb`: outputs in 17 of 19 original code cells, including three embedded PNGs, training logs, metrics and a classification report. It also retains an early `NameError` (`plt` not defined) from a duplicated setup sequence; later cells ran successfully.
- `RESNET50.ipynb`: outputs in 16 of 20 original code cells, including four embedded PNGs, training logs, metrics and a classification report.
