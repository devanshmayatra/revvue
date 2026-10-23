# **RevVue**

**Consumer sentiment and product perception analysis using Amazon customer reviews.**

RevVue is a data science coursework project for **DATA602**. Our goal is to explore how customers rate digital music purchases, what they discuss in written reviews, and which factors may relate to review sentiment and helpfulness.

## **Project objectives**

* Prepare and clean public review data for reproducible analysis.  
* Explore the distribution of star ratings and review characteristics.  
* Examine positive, neutral, and negative feedback using star ratings as an initial sentiment proxy.  
* Investigate relationships among rating, review length, verified-purchase status, and helpfulness votes.  
* Visualize findings and support conclusions with summary statistics and hypothesis testing.  
* Explore themes in review text and product-level differences where supported by the data.

> **Scope note:** The current dataset contains product identifiers and titles, but no dedicated `brand` column. Brand or artist comparisons will require an explicitly documented method for identifying those entities. Star-rating groups are not the same as text-based sentiment predictions.

## **Dataset**

**Name:** Amazon US Customer Reviews — Digital Music Purchase  
**File:** `amazon_reviews_us_Digital_Music_Purchase_v1_00.tsv`  
**Source:** [Amazon US Customer Reviews Dataset (Kaggle mirror)](https://www.kaggle.com/datasets/cynthiarempel/amazon-us-customer-reviews-dataset)

The current imported DataFrame contains **1,681,484 rows and 15 original columns**. This count reflects the TSV import using `on_bad_lines="skip"`; malformed lines may have been omitted and should be accounted for in the data-quality report.

Original attributes cover:

* **Review identification:** `customer_id`, `review_id`, `product_id`, `product_parent`  
* **Product metadata:** `marketplace`, `product_title`, `product_category`  
* **Ratings and votes:** `star_rating`, `helpful_votes`, `total_votes`  
* **Review metadata:** `vine`, `verified_purchase`, `review_date`  
* **Review text:** `review_headline`, `review_body`

The raw TSV lives in a **shared Google Drive `data/` folder** and is intentionally excluded from Git using `.gitignore`. It is **not** included in this repository.

## **Repository structure**

```
revvue/
├── README.md                # Project overview
├── WORKFLOW.md              # Collaboration and execution guide
├── requirements.txt         # Project dependencies
├── .gitignore               # Includes /data/ exclusion
├── Checkpoint-02.ipynb      # Preprocessing, cleaning and exploration work
├── git-control.ipynb        # Git command helper (no credentials)
└── data/                    # Google Drive only; not tracked by Git
    └── amazon_reviews_us_Digital_Music_Purchase_v1_00.tsv
```

The `data/` directory above describes the shared Drive workspace; it is absent from a fresh GitHub clone until you provide access to the dataset.

## **Getting started**

1. Open `Checkpoint-02.ipynb` in **Google Colab**.  
2. Ensure that you have access to the project's shared Google Drive folder and its `data/` directory.  
3. Mount Drive and set `PROJECT_DIR` to the folder as it appears **in your own Drive**:

```
from google.colab import drive
from pathlib import Path
import pandas as pd

drive.mount("/content/drive")

PROJECT_DIR = Path(
    "/content/drive/MyDrive/Colab Notebooks/DATA602-Project"
)  # Change if your shared-folder shortcut is elsewhere
DATASET_PATH = PROJECT_DIR / "data" / "amazon_reviews_us_Digital_Music_Purchase_v1_00.tsv"

assert DATASET_PATH.is_file(), f"Dataset not found: {DATASET_PATH}"
df = pd.read_csv(DATASET_PATH, sep="\t", on_bad_lines="skip")
print(df.shape)
```

5\.  
Run notebook cells in order. The preprocessing stage builds `df_preprocessed` from `df`; subsequent work should avoid mutating the raw DataFrame in place.

4. Refer to \[WORKFLOW.md\](WORKFLOW.md) before editing shared files or pushing changes to GitHub.

If your Colab runtime cannot find the dataset, confirm that Drive is mounted and that `PROJECT_DIR` points to **your** shared-folder or shortcut location. Colab does not automatically infer a notebook's Google Drive directory.

## **Preprocessing in Checkpoint 2**

The current preprocessing approach is designed to:

* Represent IDs as strings, votes and ratings as nullable numeric types, and review dates as datetimes.  
* Give categorical and textual attributes appropriate pandas data types.  
* Derive Boolean indicators from `vine` and `verified_purchase`.  
* Engineer features such as review year/month, text length, and helpfulness ratio.  
* Preserve missing values for a separate data-cleaning step.

**Cleaning and exploration are separate stages.** These include auditing parsing issues, handling missing or inconsistent values and duplicates, calculating summary statistics, running hypothesis tests, and creating supporting plots. Results should be reported only after those analyses have been performed.

## **Current status**

**Checkpoint 2 — in progress.** Dataset import and the preprocessing workflow have been established. Data cleaning, exploratory analysis, statistical conclusions, and visualizations are to be completed and verified as part of the checkpoint.

## **Collaboration**

* **GitHub** stores versioned notebooks, code, documentation, and dependencies.  
* **Google Drive** provides access to the large raw dataset.  
* **Colab** runs the analysis in each contributor's runtime.  
* Each contributor should use their **own Git clone and GitHub credentials**. Avoid concurrent Git commands in the same shared Drive `.git/` directory.  
* Never commit large datasets, access tokens, personal credentials, or Colab authentication output.

See \[WORKFLOW.md\](WORKFLOW.md) for setup, notebook handoffs, and Git collaboration steps.

&nbsp;