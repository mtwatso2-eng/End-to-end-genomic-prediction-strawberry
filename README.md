# End-to-end genomic prediction: direct prediction of images and text from genome-wide molecular markers

This repository provides the code supporting Watson et al., 2025 for end-to-end genomic prediction of images and text, using a strawberry dataset from the Strawberry Breeding & Research Program at UC Davis.

## Directory Structure

### `genome-to-image/`

This directory contains notebooks for end-to-end genomic prediction of strawberry images.

- **`buildRandomSets.ipynb`**: Creates random train/test splits for cross-validation. Generates 50 different random seeds and corresponding train/test keys for each split, ensuring clones are properly assigned to either training or testing sets.

- **`getCorrelations.ipynb`**: Calculates correlations between predicted and actual traits from end-to-end predictions. Compares conventional rrBLUP predictions with end-to-end predictions by decoding predicted embeddings back to images and extracting phenotypic traits (LWR, shape index, color metrics, redness).

- **`makeFigures.ipynb`**: Creates visualization figures comparing original images, encoded-decoded images, mean encoded-decoded images, and end-to-end predicted images. Generates mosaic visualizations and correlation plots to assess prediction accuracy.

- **`rrBLUPembeddingPredictor.ipynb`**: Uses rrBLUP (ridge regression BLUP) to predict VAE embeddings from genotypes. Trains genomic prediction models for each embedding component and saves predicted embeddings for downstream image reconstruction.

- **`rrBLUPextractedTraitPredictor.ipynb`**: Uses rrBLUP to predict extracted traits (LWR, B, G, R, Redness) directly from genotypes. This represents the conventional genomic prediction approach where traits are predicted directly without going through the image representation.

- **`VAE.ipynb`**: Trains and evaluates a Variational Autoencoder (VAE) to encode/decode strawberry images. The VAE compresses images into a low-dimensional embedding space (16 dimensions) and can reconstruct images from these embeddings. Evaluates reconstruction quality by comparing predicted vs. actual phenotypic traits.

### `genome-to-text/`

This directory contains notebooks for end-to-end genomic prediction of strawberry text descriptions.

- **`genoToEmbedding.ipynb`**: Uses rrBLUP to predict text embeddings from genotypes. Predicts each component of the text embedding vector using genomic markers, enabling end-to-end text prediction.

- **`numericToText.ipynb`**: Converts numeric phenotypes to text descriptions using both heuristic rules and OpenAI's GPT-4o-mini API. Generates natural language descriptions of strawberries based on phenotypic measurements (LWR, color values, redness) and can extract numeric traits back from text descriptions.

- **`predictingRawTextFeatures.ipynb`**: Predicts raw text features (character encodings) directly from genotypes using rrBLUP. Converts text descriptions to ASCII character codes and predicts these codes from genomic data, then reconstructs text from predicted character codes.

- **`rrBLUPextractedTraitPredictor.ipynb`**: Uses rrBLUP to predict extracted traits (Length, Redness) from genotypes. This represents the conventional genomic prediction approach where numeric traits extracted from text are predicted directly.

- **`textToEmbedding.ipynb`**: Converts text descriptions to embeddings using OpenAI's text-embedding-ada-002 model and inverts embeddings back to text using the vec2text library. Creates embeddings for text descriptions and demonstrates the encoding/decoding process for text representations.

- **`viewCorrelations.ipynb`**: Visualizes correlations comparing end-to-end vs. conventional genomic prediction methods. Creates box plots and statistical summaries to assess the relative performance of end-to-end text prediction compared to conventional trait-based prediction.
