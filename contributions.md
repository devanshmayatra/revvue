# RevVue - Contribution Tracker

This file tracks individual contributions to the project.

## October 22, 2026 — Devansh Mayatra

- Set up the shared Google Drive and Colab project environment.
- Downloaded and organized the Amazon Digital Music Purchase Reviews dataset.
- Implemented data preprocessing and feature engineering.
- Connected the project to GitHub.
- Configured Git and dataset exclusion rules.
- Updated project documentation, including README and workflow instructions.

## October 23, 2026 – Arpit Tiwari

- Assessed data quality by examining missing values, data types, and unique-value distributions.
- Identified and removed duplicate records, missing review text, blank reviews, and invalid entries.
- Implemented text cleaning to remove HTML tags, decode HTML entities, normalize Unicode, and eliminate unnecessary whitespace.
- Performed final data validation, retaining 1,681,368 clean reviews for subsequent analysis and model training.

## October 26, 2026 — Anastasiia Lapshina

- Proposed the dataset and assessed its suitability against the project requirements.
- Completed exploratory analysis using chi-square goodness-of-fit, Kruskal–Wallis, and Spearman rank correlation.
- Created supporting visualizations of rating distributions, review lengths, and rating trends over time.
- Documented three statistical conclusions, effect sizes, and implications for subsequent modeling.
- Updated dataset loading to use a shared download link without personal Google Drive paths or shortcuts.

## November 19, 2026 — Anastasiia Lapshina

- Grouped star ratings into negative, neutral, and positive sentiment labels, including four-star reviews in the neutral class.
- Removed repeated review texts and excluded texts associated with conflicting sentiment labels before splitting the data.
- Created reproducible, stratified training, validation, and test splits.
- Exported the prepared splits as Parquet files for consistent reuse across experiments and team members.
- Implemented model-specific Hugging Face tokenization for all three splits.
- Created separate PyTorch DataLoaders with dynamic padding for training, validation, and testing.
- Documented the preparation workflow and provided separate notebook routes for rebuilding the datasets or loading the prepared files.
