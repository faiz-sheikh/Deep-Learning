# Pretrained experiment results

Audit date: 2026-10-16 (Asia/Kolkata).

## Offline evaluation status

No model was re-run. The local Keras dataset cache contains no CIFAR-10 archive, no local Beans/Hugging Face dataset cache was found, and TensorFlow is not installed in the audit environment. In accordance with the no-network requirement, nothing was downloaded. All figures below are therefore either explicitly marked as saved notebook output or unavailable; none is estimated.

Audit hardware: Intel Core i5-14450HX, 16 logical CPUs, Linux x86_64. An NVIDIA device was not available through the installed driver (`nvidia-smi` could not communicate with it). These are audit-host details, not evidence of the hardware used for the saved notebook runs. The notebooks record TensorFlow 2.21.0 and CUDA-capable sessions, but GPU model names are unknown.

## Artifact-to-notebook map and test evidence

| Artifact | Producing notebook | Mapping confidence | Offline test result |
| --- | --- | --- | --- |
| `beans_vgg16.keras` | `beans/VGG And RESNET50.ipynb` | Explicit `save()` call; saved after the reported evaluation | Accuracy 84.38%, loss 0.4315 — from saved notebook output, not re-run |
| `beans_resnet50.keras` | `beans/VGG And RESNET50.ipynb` | Explicit `save()` call; saved after the reported evaluation | Accuracy 94.53%, loss 0.1735 — from saved notebook output, not re-run |
| `best_vgg16_cifar10.keras` | `cifar10/VGG16_SCR.ipynb` | Explicit best-`val_accuracy` checkpoint | Unknown for this artifact: the notebook evaluates the in-memory model after `EarlyStopping` restores the best-`val_loss` epoch, not the checkpoint file |
| `best_of_vgg16_cifar10.keras` | Probably `cifar10/VGG16_SCR.ipynb` | Inferred from identical serialized architecture/configuration; filename is absent from the notebook and the producing run is unknown | Unknown; no artifact-specific saved evaluation |
| `best_resnet50_cifar10.keras` | `cifar10/RESNET50.ipynb` | Explicit best-`val_accuracy` checkpoint | Unknown for this artifact: the notebook evaluates the in-memory model after `EarlyStopping` restores the best-`val_loss` epoch, not the checkpoint file |
| `resnet50_cifar10_final.keras` | `cifar10/RESNET50.ipynb` | Explicit final `save()` after the reported evaluation | Accuracy 85.12%, loss 0.7481 — from saved notebook output, not re-run |

The VGG CIFAR-10 notebook reports 76.70% test accuracy and 0.7792 test loss for its restored in-memory model. This is from saved notebook output, not re-run, and must not be attributed to either saved VGG checkpoint without loading and testing it.

## Saved per-class reports

All rows in this section are from saved notebook output, not re-run. Columns are precision / recall / F1 / support.

### Beans VGG16 (`beans_vgg16.keras`)

| Class | Precision | Recall | F1 | Support |
| --- | ---: | ---: | ---: | ---: |
| angular_leaf_spot | 0.77 | 0.86 | 0.81 | 43 |
| bean_rust | 0.84 | 0.72 | 0.78 | 43 |
| healthy | 0.93 | 0.95 | 0.94 | 42 |
| macro average | 0.85 | 0.84 | 0.84 | 128 |
| weighted average | 0.85 | 0.84 | 0.84 | 128 |

### Beans ResNet50 (`beans_resnet50.keras`)

| Class | Precision | Recall | F1 | Support |
| --- | ---: | ---: | ---: | ---: |
| angular_leaf_spot | 0.95 | 0.95 | 0.95 | 43 |
| bean_rust | 0.89 | 0.95 | 0.92 | 43 |
| healthy | 1.00 | 0.93 | 0.96 | 42 |
| macro average | 0.95 | 0.95 | 0.95 | 128 |
| weighted average | 0.95 | 0.95 | 0.95 | 128 |

### CIFAR-10 VGG16-style in-memory model (artifact association unknown)

| Class | Precision | Recall | F1 | Support |
| --- | ---: | ---: | ---: | ---: |
| Airplane | 0.7027 | 0.8700 | 0.7775 | 1000 |
| Automobile | 0.8584 | 0.8730 | 0.8656 | 1000 |
| Bird | 0.7185 | 0.6280 | 0.6702 | 1000 |
| Cat | 0.6013 | 0.5460 | 0.5723 | 1000 |
| Deer | 0.7448 | 0.7560 | 0.7504 | 1000 |
| Dog | 0.6629 | 0.7020 | 0.6819 | 1000 |
| Frog | 0.8195 | 0.8310 | 0.8252 | 1000 |
| Horse | 0.8447 | 0.8050 | 0.8244 | 1000 |
| Ship | 0.8592 | 0.8480 | 0.8535 | 1000 |
| Truck | 0.8674 | 0.8110 | 0.8382 | 1000 |
| macro average | 0.7680 | 0.7670 | 0.7659 | 10000 |
| weighted average | 0.7680 | 0.7670 | 0.7659 | 10000 |

### CIFAR-10 ResNet50 final (`resnet50_cifar10_final.keras`)

| Class | Precision | Recall | F1 | Support |
| --- | ---: | ---: | ---: | ---: |
| Airplane | 0.8506 | 0.8940 | 0.8718 | 1000 |
| Automobile | 0.9280 | 0.9410 | 0.9345 | 1000 |
| Bird | 0.7992 | 0.7840 | 0.7915 | 1000 |
| Cat | 0.6586 | 0.7660 | 0.7083 | 1000 |
| Deer | 0.8343 | 0.8210 | 0.8276 | 1000 |
| Dog | 0.8059 | 0.7680 | 0.7865 | 1000 |
| Frog | 0.9057 | 0.8450 | 0.8743 | 1000 |
| Horse | 0.9037 | 0.8730 | 0.8881 | 1000 |
| Ship | 0.9281 | 0.9170 | 0.9225 | 1000 |
| Truck | 0.9338 | 0.9030 | 0.9181 | 1000 |
| macro average | 0.8548 | 0.8512 | 0.8523 | 10000 |
| weighted average | 0.8548 | 0.8512 | 0.8523 | 10000 |

## Integrity checks

The paired files have identical serialized model configurations but different full-file SHA-256 checksums. Their internal `model.weights.h5` payloads also have different SHA-256 checksums, so the difference is not merely archive metadata:

| Artifact | Full `.keras` SHA-256 | Internal weights-payload SHA-256 |
| --- | --- | --- |
| `best_of_vgg16_cifar10.keras` | `a6d1f1ca896408539d80eadaee08ef7140c8e19b44bbcb319d8b5e296981311d` | `43fa7f001c31d81a3565edeae013eb303ed298fad770a9c11119aea2ddd8a5ef` |
| `best_vgg16_cifar10.keras` | `ba533985f1cf66517566ecad7ebf691bc5babc825819e47811e0b568404cad75` | `5312c29e8edc1b08a4d9fcb6bca1f1a9a6a4fd48948076021bafb36b10362485` |
| `best_resnet50_cifar10.keras` | `5b1a85ffb5587766ed15040e9dda489fceac13e48fef19b9b9ab553e68c0b229` | `9fac0e6befa61a47a30808f8859d2b25c36560ae7780eaeb59ce1aa56f4d8519` |
| `resnet50_cifar10_final.keras` | `5e1de8fab89610accb7175b89cdbaecca4d290e1437317c78e41d67a3120921a` | `0cced8d25f31cf12cc5160802be6932f097233536b51bf06cc03f8f50b684075` |

Neither pair is byte-identical.
