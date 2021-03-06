# Can Machines Detect Hate Speech in Memes?
### WARNING! Due to the subject matter of this project it contains content that is highly offensive

Artificial Intelligence plays a crucial role in mitigating problematic or abusive behavior, such as pornographic material, misinformation, and hate speech on social media platforms. While machines may be good at classifying content that is just images or just text, memes pose a unique challenge because it is often the combination of image and text which make a meme hate speech or not. Training a machine to recognize this as hate speech is not as easy as it sounds. While humans can easily integrate the text and image information holistically, machines struggle with this sort of task. Currently it is impossible for humans to inspect all the content posted on social media sites so being able to create a machine learning model which can accurately categorize memes as hate speech is becoming ever more important. With that in mind, the goal of our project was to develop a machine learning system that could determine whether a meme was hateful or not. We created three different models, 2 unimodal models based on just the image or text and one multimodal model that combined the meme image and text. 

In order to achieve our goal we used the Hateful Memes Challenge dataset which was created by Facebook AI. This dataset includes a training set of 8,500 memes as well as a validation dataset and a hold out test dataset. All three datasets include the images as well as a JSON file with the meme text and label. The full dataset is available to download here: https://hatefulmemeschallenge.com

## What is included in this repo?
### Data Preprocessing and EDA Folder
  * Preprocess_Meme_Image_and_Text_Data.ipynb - preprocesses 120 random samples from the training data for TSNE visualization. Sixty of the memes are classified as hate speech and the other sixty are classified as non-hate speech. Creates a BERT embedding for the text from each meme and a ResNet for the image of each meme, combines the two embeddings into one multimodal data representation and saves all the embeddings to a pickle file.
  * Exploratory Data Analysis.ipynb - includes visual exploration of the training dataset. training_combo.p and training_labels_combo.p can be created using the Preprocess_Meme_Image_and_Text_Data.ipynb file or downloaded here: https://drive.google.com/drive/folders/1gUuicGA6Gnzh1hYdAsE9powrQYuCTvyp?usp=sharing


### CNN Model Folder
The first thing we tried was to create a classifier simply based on the image data. In order to do this we trained a Convolutional Neural Network since this form of model can capture the spatial information in images. 
<img src=https://github.com/roseandgold/HatefulMemesProject/blob/main/CNN%20Model/Capstone%20CNN%20Model%20Diagram3.png>

To test out this model yourself you need the below files as well as the Hateful Memes Challenge Datasets
 * Preprocess_the_Images_for_CNN.ipynb - preprocesses the meme images so they are all 200x200x3. Outputs the data as numpy arrays to a pickle file. 
 * CNN_Image_Model.ipynb - train and test the CNN model. Requires the preprocessed images which can either be obatined by running the Preprocess_the_Images_for_CNN.ipynb notebook or downloaded here: https://drive.google.com/drive/folders/1l5QVobAOw52l5ApcVYYceOhT9TzFwVx5?usp=sharing 
 * model_0.533.h5 - This was the best model we obtained. This can be used in the CNN_Image_Model.ipynb notebook to get the AUROC score and create the ROC curve

### BERT Model Folder
Another model we decided to try was a pretrained BERT model using only the text from the memes. BERT stands for Bidirectional Encoder Representations from Transformers. According to the *BERT - transformers 4.7.0* documentation "unlike recent language representation models, BERT is designed to pre-train deep bidirectional representations from unlabeled text by jointly conditioning on both left and right context in all layers."

To test out the BERT model you need the below notebook and the Hateful Memes Challenge Datasets
 * BERT_Model.ipynb - uses the meme text and a pretrained BERT model to create a classifier. This notebook runs best in Google Colab using a GPU. If you want to use or look at our best trained model it can be downloaded here: https://drive.google.com/drive/folders/1KfpguSuk_Zz_6rAbRJCeVnS296u0SQfl?usp=sharing

### Multimodal Model Folder
Lastly, we created our multimodal model using an early fusion feed forward neural network. We embedded the text data using BERT and the image data using a pretrained ResNet

<img src=https://github.com/roseandgold/HatefulMemesProject/blob/main/Multimodal%20Model/Capstone%20Multimodal%20Model%20Diagram2.png>

To test out the Multimodal Model you need the below notebook and the Hateful Memes Challenge Dataset.
 * Multimodal_Model.ipynb - train and test the multimodal model. This notebook runs best in Google Colab using a GPU If you want to use or look at our best trained model it can be downloaded here: https://drive.google.com/drive/folders/1p0cnxL8U6zs9_dh1A6q2Sh76Ew3u59Ro?usp=sharing

### Results
 * Can Machines Detect Hate Speech in Memes?.pdf - a write up of our project which includes visualizations and results

### Requirements
 * resuirements.txt - includes all the necessary packages to run the above notebooks
