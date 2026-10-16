# Beans transfer-learning experiments

`VGG And RESNET50.ipynb` compares two frozen ImageNet feature extractors on three-class bean-leaf disease classification.

## Models

| Exact model class | Architecture and initialization | Layers | Training | Data and preprocessing | Licence |
| --- | --- | --- | --- | --- | --- |
| `tf.keras.applications.VGG16` with `include_top=False` | ImageNet weights ported by Keras Applications; 224x224 input; global average pooling, Dense(128), Dropout(0.4), Dense(3) head | Entire VGG16 base remains frozen; only the new head trains | Adam, learning rate 0.0001; sparse categorical crossentropy; accuracy; batch 16; at most 10 epochs; early stopping on `val_loss`, patience 3, restoring best weights | Beans (`AI-Lab-Makerere/beans`), source: as stated in notebook or unverified; `tf.keras.applications.vgg16.preprocess_input` is embedded in the model | VGG: CC BY 4.0 |
| `tf.keras.applications.ResNet50` (v1) with `include_top=False` | ImageNet weights ported by Keras Applications; 224x224 input; global average pooling, Dense(128), Dropout(0.4), Dense(3) head | Entire ResNet50 base remains frozen; only the new head trains | Adam, learning rate 0.0001; sparse categorical crossentropy; accuracy; batch 16; at most 10 epochs; early stopping on `val_loss`, patience 3, restoring best weights | Beans (`AI-Lab-Makerere/beans`), source: as stated in notebook or unverified; `tf.keras.applications.resnet50.preprocess_input` is embedded in the model | ResNet50 v1: MIT |

The notebook uses the dataset's stated splits unchanged: 1,034 train, 133 validation and 128 test examples. Validation data controls early stopping; test data is used only after training for evaluation and reports. It does not tune or select an epoch on the test split.

## Saved artifacts and outputs

- `beans_vgg16.keras` and `beans_resnet50.keras` are explicitly saved by this notebook after evaluation.
- The notebook has outputs in 22 of 27 original code cells, including five embedded PNGs, training logs, test metrics, classification reports and confusion-matrix figures.
- A later optional single-file inference cell retains a `FileNotFoundError` because `bean_leaf.jpg` was absent. This does not affect training or test evaluation.
- Saved runtime-home paths were sanitized in this organized copy; no token value or personal identifier was found. The `HF_TOKEN` text is only a warning naming an unset environment variable.

Model files are intentionally ignored and remain under `pretrained/_incoming/`. Evaluation evidence is in [`../results.md`](../results.md).
