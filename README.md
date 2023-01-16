# Conversational-ai

## Goal:
In this project, the main goal is to be able to give suggestions of items to a user through an automated process, which is Answering questions based on information from images. The domain worked on was fashion, but the conception must take into consideration an easy switch between domains.<br />
Example : Would blue jeans match with my yellow shirt ?<br />
Answer : Yes it's a great combination / No this does not match


## Global Architecture:
![alt text](https://github.com/rasta-nitzsche/Topic-Labeling-with-Ukparl-Dataset/blob/main/Conv%20AI%20Architecture.JPG)

This architecture represents the attribute extraction from the query. First when we have a query, we check that it is a question, if not it is rejected. We do a semantic check to make sure that the sentence is correct :  for example the following query will be rejected in this phase: Can I have launch with a blue jean ? Once all the steps above are validated, we extract all the entities from the query, and we check if it is a fashion item using the model developed before. The results of this step are the attributes (features) we are going to search in the occurrence matrix.

## VinVL:
<br />
VinVL stands for Visual Representations in Vision-Language Models is an improved object detection model to provide object-centric representations of images. Compared to the most widely used bottom-up and top-down model (code), the new model is bigger, better-designed for VL tasks, and pre-trained on much larger training corpora that combine multiple public annotated object detection datasets. Therefore, it can generate representations of a richer collection of visual objects and concepts.

## Preprocessing :
- Filtring the columns to have the same attributes on each line 
- Removing similar items (by comparing the boundaries)
- Saving the bad pairs in a csv file in order to remove them from the data

## Image Response:
<br />
Regarding the image response we displayed images of matches from our own dataset. At first results were not good because of the distribution of the data I talked about earlier, and we thought about generating images from google as a simple solution. But we wanted a quality project and with some preprocessing and further work we were able to get promising results using our very own data. At some point when the query is complexe we achieve even better results than google image.

## Dataset:
<br />
For the image database we opted for polyvore dataset (2017), it contains 33000 samples. The data is multi distributed which means that not all images are defined in the same approach: we can have an image of people wearing clothes, or a set of clothes alone displayed or both (person + cloth) as we can see in this image.

## Trained models and data:
<br />
For the project, adding to the models that were already in the litterature (SimCSE , VinVL,...) we created 2 models for the approach. Both are NLP models based on pre-trained BERT architecture (distilBERT base uncased to be precise) with manually annotated dataset. The first model for semantic check (200-300 data) and got 92% accuracy. The second and the most important was for fashion item classification (2000 rows) and got 99% accuracy.


## Metrics & Evaluation:
<br />
We created a metric to evaluate our model . We manually annotated 100 rows of fashion query with predefined answers (according to our sense of fashion + instagram/pinterest) we then compared with the results of our model. The accuracy was about 87%, a result that can be improved by getting more data (the dataset from 2017 is a bit old and a new trend is going on every week in this domain) and by doing some quick modifications in the pipeline.

## Deployment:
![alt text](https://github.com/rasta-nitzsche/Conversational-AI-a-chat-bot-for-fashion-suggestion-/blob/main/example.png)
<br />
Regarding the deployment we used a telegram bot that recognized 3 intents : Garment matching / Garment advice / Other. We faced some limited resources problems when using free solutions so we are currently deploying the model on Heroku using Docker containers.

## Advantages of our approach:
<br />
We consider our approach as a good one mainly because it is Easily Portable from a domain to another, we only need to get a new database image, and change the manual annotated data for the modules and the metrics (which is a total of 1000 rows). Theorically, no code is needed to be changed (unless some preprocessing/ feature engennering specific to each domain). 
Also, the approach is Data dependant which means a good dataset results in good results. Finnaly, we opted for an Incremental process that improved team work and obtained fast results that we improved week by week.

## Further improvements for next cohort:
<br />
In order to get the next cohort to start on good basics we are commenting, defining and writing all the process. We would suggest the following to get a real robust product: Make a more responsive bot for example Add more intents and interactions so the user do not get bored of predefined answers and can actually have a chat. Improving the quality of the dataset will improve the prediction (either by manual cleaning or finding a more promising one). Get a confidence level to the prediction instead of answering with a yes/no answer. Finding a better model than VinVL or creating a new one can be a really challenging task because it will generate way better attributes which leads to better patterns.
