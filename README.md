<p align="center">
    <strong>Assessment of Medical Foundation Models for Survival Prediction with Whole Slide Images</strong>
</p>

The preprint (https://www.researchsquare.com/article/rs-5832726/v1) accepted for AIM-FM workshop at NeurIPS'24 (https://openreview.net/forum?id=xFUeXBi7Di).

To assess the performance of the digital pathology foundation models, we used two ovarian cancer datasets with high-resolution whole slide images (WSIs) at 20x magnification:
- TCGA ovarian cancer dataset (TCGA-OV), composed of the H&E stained diagnostic slides from TCGA, available at https://portal.gdc.cancer.gov.
- Ovarian Bevacizumab Response (OBR), composed of the H&E stained WSIs for classification of bevacizumab treatment effectiveness of ovarian cancer, available at https://www.cancerimagingarchive.net/collection/ovarian-bevacizumab-response.

For each WSI, automated segmentation of tissue was performed using the public tool for WSI analysis CLAM (https://github.com/mahmoodlab/CLAM).

Following patch generation, the feature vectors were extracted using the following models:

- ResNet-50 model pretrained on ImageNet
- TIL-Maps-23 Inception-V4 model (https://github.com/ShahiraAbousamra/til_classification)
- SimCLR model pretrained on the histopathology images (https://github.com/ozanciga/self-supervised-histopathology)
- CTransPath model (https://github.com/Xiyue-Wang/TransPath)
- UNI model (https://github.com/mahmoodlab/UNI)

For each cancer dataset, we trained the PORPOISE model (https://github.com/mahmoodlab/PORPOISE), AMIL network with WSI only input in a 5-fold cross-validation.
We used the PORPOISE hyperparameters suggested by the authors, except for: the alpha_surv (serves to weigh the uncensored patients) set at 0.5 and max_epochs (the maximum number of epochs to train) set at 40 in our experiments.

All the models, except for TIL-Maps-23, are available for downloading in PyTorch ckpt or pt format (cf. the corresponding github repositories for instructions).
TIL-Maps-23 is distributed in tensorflow format, we converted it into PyTorch, please, contact if interested.
