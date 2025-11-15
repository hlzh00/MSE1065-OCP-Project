To run the notebook yourself, I recommend creating a new virtual environment.

## venv
From the project directory, create a new python virtual environment with `python -m venv .venv`

activate the environment with `source .venv/bin/activate`

once your virtual environment is activated, use `pip install -r requirements.txt` to install all the dependencies.

You can check the list of installed dependencies with `pip list`

## Conda
If you are using conda, create a new conda environment with `conda env create -f environment.yml`

I extracted all the training data into a csv file called training_FULL.csv
I then separated it into 2 sets of data: one with 1 H atom as the adsorbate, one with no adsorbates, called training_h_FULL.csv and training_no_ads_FULL.csv respectively.

training_h_FULL has around 1600 entries
training_no_ads_FULL has around 15000 entries

I only created a small sample of the full dataset (n=100) to test the featurization process.
I will provide the full featurized dataset this weekend but you can also try to run it yourself, it just takes a long time. To featurize the full dataset, I provided comments on how to edit the code. U just need to change some file names.

Important: some entries are missing structural data, which are these columns: 
- density
- vpa
- packing fraction
- spacegroup_num
- crystal_system
- crystal_system_int
- is_centrosymmetric
- n_symmetry_ops

I think the right step would be to remove entries missing these features entirely. It should only be a handful. 

OCP also provides a validate and a test set, but I haven’t extracted those. I will work on extracting those datasets this weekend. But if you need to test your model and I haven’t provided those datasets you can try to do it yourself, just follow the same algorithm I used for the training dataset and feed it through the same featurizers. If using cross validation, which is probably a good idea anyway since the H-ads dataset is so small, then we won't need the validate set.

**NOTES:**
The H-ads dataset is much smaller than the no-ads dataset. This means the predicted target (relaxed E_surface+H) will have a higher uncertainty. I think this will be important to include in our presentation or final report.
Also, when we do the screening step, we might need to be mindful of the inputs for our model; we probably cannot use materials that are too different from the dataset or the model might not extrapolate properly.

We discussed to use the following methods:
- Linear regression
- Non-linear regression
- Classification (maybe tree-based vs. logistic regression)

Optional advanced methods:
- Neural network

