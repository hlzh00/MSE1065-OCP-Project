To run the notebook, I recommend creating a new virtual environment.

## venv

If you are using python's venv, do this from the project directory

```
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## conda

If you are using conda:

```
conda config --set channel_priority flexible
conda env create -f environment.yml
```

## Description

I extracted all the training data into a csv file called training_FULL.csv
I then separated it into 2 sets of data: one with 1 H atom as the adsorbate, one with no adsorbates, called training_h_FULL.csv and training_no_ads_FULL.csv respectively.

- training_h_FULL has around 1600 entries
- training_no_ads_FULL has around 15000 entries

I created a small sample of the full dataset (n=100) to test the featurization process. I will provide the full featurized dataset this weekend but you can also try to run it yourself, it just takes a long time. To featurize the full dataset, I provided comments on how to edit the code. U just need to change some file names.

OCP also provides a validate and a test set, but I haven’t extracted those. I will work on extracting those datasets this weekend. But if you need to test your model and I haven’t provided those datasets you can try to do it yourself, just follow the same algorithm I used for the training dataset and feed it through the same featurizers. But I don't think we need to use the validate set because we will use cross validation instead.

**NOTES**
- The H-ads dataset is much smaller than the no-ads dataset. This means the output will have a higher uncertainty. I think this will be important to include in our presentation or final report.
- When we do the screening step, we might need to be mindful of the inputs for our model; we probably cannot use materials that are too different from the dataset or the model might not extrapolate properly.
- We discussed to use the following methods:
	- Linear regression
	- Non-linear regression
	- Classification (maybe tree-based vs. logistic regression)
	- Optional advanced methods:
		- Neural network

## Updates

I tested out a decision tree regressor model with the current dataset.

H-ads dataset:
- training R^2 = 0.46
- CV R^2 = 0.31

no-ads dataset:
- training R^2 = 0.65
- CV R^2 = 0.46

Full set of features are used.

*to do*

Try out different models. 
Maybe try out classification? research and see if it makes sense with y_relaxed. 
