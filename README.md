downloading the folder from the github link:
https://github.com/hlzh00/MSE1065-OCP-Project
To ensure you get the most updated version

To run the notebook yourself, I recommend creating a new conda virtual environment.

Once your virtual env is activated, download the v1 folder, cd into the folder, and use command  `pip install -r requirements.txt`. It will automatically install all the dependencies.

I extracted all the training data into a csv file called training_FULL.csv
I then separated it into 2 sets of data: one with 1 H atom as the adsorbate, one with no adsorbates, called training_h_FULL.csv and training_no_ads_FULL.csv respectively.

training_h_FULL has around 1600 entries
training_no_ads_FULL has around 15000 entries

I only created a small sample of the full dataset (n=100) to test the featurization process.
I will provide the full featurized dataset this weekend but you can also try to run it yourself, it just takes a long time. To featurize the full dataset, I provided comments on how to edit the code. U just need to change some file names.

Important: some entries are missing structural data, which are these rows: 
DensityFeatures:
- density
- vpa
- packing fraction


GlobalSymmetryFeatures:
- spacegroup_num
- crystal_system
- crystal_system_int
- is_centrosymmetric
- n_symmetry_ops
I think the right step would be to remove these entries entirely before training the model.

The dataset also provides a validate and test set, but I haven’t extracted those. I will work on extracting those datasets this weekend.

But if you need to test your model and I haven’t provided those datasets you can try to do it yourself, just follow the same algorithm I used for the training dataset and feed it through the same featurizers. 
If using cross validation, which is probably a good idea anyway since the H-adsorbate dataset is so small, then we don’t actually need the validate set I guess. Just extract the test set should be enough. 


NOTES:
The dataset for H-adsorbate relaxed energies is much smaller than the no-adsorbate relaxed energies dataset. This means the predicted target value (relaxed E_surface+H) will have a higher uncertainty. I think this will be important to include in our presentation or report.

Also, when we do the screening step, we might need to be mindful of the inputs for our model, we cannot use materials that are too different from the dataset or it might not extrapolate properly.

We discussed to use the following methods:

Linear regression
Non-linear regression
Classification (maybe tree-based vs. logistic regression)

Optional advanced methods:
Neural network ?

