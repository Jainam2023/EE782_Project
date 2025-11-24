# <p style="font-size:32px;"> <b>🧬 EE782 Project — Generative Models for Few-Shot Medical Image Augmentation</b></p>

This repository contains the implementation and analysis for the <span style="color:#007acc;"><b>EE782 (Advanced Machine Learning)</b></span> course project.
The work explores whether deep generative models can enhance few-shot medical image classification, using the HAM10000 dermoscopic skin lesion dataset.

We evaluate and compare:

- <b>GAN</b> (Generative Adversarial Network)

- <b>CVAE</b> (Conditional Variational Autoencoder)

- <b>Diffusion Model (DDPM)</b>

Synthetic images are used to augment a few-shot training set, and a ResNet50 classifier is evaluated under multiple training conditions.


Each notebook includes:

- Data loading & processing

- Few-shot split creation

- Generative model training

- Synthetic image sampling

- ResNet50 classifier training

## Evaluation & visualization tools

- <p style="font-size:26px;"><b>🩺 Dataset: HAM10000</b></p>

The HAM10000 dataset contains dermoscopic images across 7 diagnostic classes:

- akiec — Actinic keratoses

- bcc — Basal cell carcinoma

- bkl — Benign keratosis

- df — Dermatofibroma

- mel — Melanoma

- nv — Melanocytic nevi

- vasc — Vascular lesions

This dataset is widely used for benchmarking skin lesion classification models.

## <p style="font-size:26px;"><b>🎯 Few-Shot Experimental Setup</b></p>

For each class:

- <b>50 images → Train set</b>

- <b>10% of remaining → Validation set</b>

- <b>15% of remaining → Test set</b>

This creates a 350-sample few-shot training set, used for all three generative models.

All generative models are trained exclusively on these 350 real images, ensuring fairness.

## <p style="font-size:26px;"><b>🧪 Generative Models</b></p>
### <b>1️⃣ GAN (Generative Adversarial Network)</b>

- Class-conditional convolutional generator + discriminator

- Trained on 50/class few-shot real images

- Produces sharp but occasionally unstable samples

### <b>2️⃣ CVAE (Conditional VAE)</b>

- Encoder–decoder latent-variable model

- Smooth reconstructions, lower diversity

- Class-conditioning improves separability

### <b>3️⃣ Diffusion Model (DDPM)</b>

- Denoising diffusion with UNet-based architecture

- Highest sample realism among the three

- Used to generate ~1200 synthetic images for augmentation

### <p style="font-size:26px;"><b>🧠 Classifier: ResNet50</b></p>

We evaluate under three training conditions:

- <b>Baseline:</b>

- Real few-shot images only (50/class)

- <b>Synthetic-Only:</b> Classifier trained entirely on generated samples

- <b>Augmented:</b> Real few-shot + synthetic generative samples

### Key metrics calculated:

- <b>Accuracy</b>

- <b>Per-Class F1 Score</b>

- <b>Confusion Matrix</b>

- <b>Qualitative visual comparisons</b>
