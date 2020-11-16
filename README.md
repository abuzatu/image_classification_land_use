# General

Created by Adrian Buzatu on 16 Nov 2020, to classify satellite imagiry from open source data from ESA with 10 meter resolution in RGB, to classify images of the ground into ten classes of land usage or land cover. Dataset and a paper can be found [here](https://github.com/phelber/EuroSAT).

# Instructions how to set up your Python environment

Install `virtualenv`, if you do not have it already.
```
pip3 install virtualenv
```

Create a virtual environment
```
virtualenv LandUse
```

Activate the environment
```
source LandUse/bin/activate
```

Install all the python packages needed for this project
```
pip install -r requirements.txt
```

# Prepare the data folder

Download the data
```
wget http://madm.dfki.de/files/sentinel/EuroSAT.zip
```

Unzip and move to our own data folder
```
unzip EuroSAT.zip
rm -f EuroSAT.zip
mv 2750 data
```

# Run the prediction on the trained model

In the output folder there is already the trained model `model.h5`. We can run already prediction on this model.
```
python inference.py
```

Check in the `output` folder the `.png` plots. There are 32 images that are predicted, and both their true label and the predicted label are shown on the plot title. You will see that most are predicted well.
```
open output/plot_*_image_*.png
````

There is also the confusion matrix plot, where we see it is quite diagonal, as expected in a good training.
```
open output/plot_*_confusion_matrix.png
```

There is also a text file shown with the accuracy and loss and the confusion matrix values. We see the accuracy is above 90%, reasonable for a model trained quickly.

# Train the model and evaluate the model

To train the model, and also to evaluate the model, let's use a Jupyter Notebook.

```
jupyter notebook ImageClassificationLandUse.ipynb
Kernel -> Clear Output
Kernel -> Restart & Run All
```

The model will be saved in `output/model.h5`, but you can change the name too.

