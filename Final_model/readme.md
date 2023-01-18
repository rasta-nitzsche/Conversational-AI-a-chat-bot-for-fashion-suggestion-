# Final model

link to download : https://drive.google.com/file/d/1b8bqgm8qqLiplmdLRJ7XYZAlBhet3qXW/view?usp=sharing

To run :
- Create a new conda environment using requirements.txt
- run the main cells if it is printed "Bot started" it means you can start using the bot on Telegram
- Always start by the following command : /start
- You can use /help for use case examples.


# About the code
## Parameters fine tuned by our team:

Some parameters were tested and we kept the ones that gave us the best results :
- Distance between attributes: 30. For each attributes in the same image, if 2 attributes have a distance less than 30 pixels, then we remove the attribute with the most probability of occurrence (because precise attribute get less probability)
- Image percentage: 20. If an attribute represents less than 20% of the image size, it is considered as small and is removed from the list.
- Number of recommended items: 5.
- Number of top recommendations for garment matching 10. This means that for a query (attr1,attr2) we will search for top 10 matches of attr1, and attr2 must be in those 10 items otherwise it is considered as a not recommendable pair.

## Content of each notebook   
  - Data Prepocessing.ipynb : Regrouping all the samples into one dataframe, filtring the columns to have the same attributes on each line, Removing similar items (by comparing the boundaries), and saving the bad pairs in a csv file. (Not needed for the final model)
  - Similarity search: training SimCSE model on our own data (items of attributes) and save the embeddiings in a pickle file. (Not needed for the final model)
  - co_occurrence_matrix_generation.ipynb : generate the matrix from the preprocessed data. (Not needed for the final model)
  - attribute_extraction.ipynb : contains the whole pipeline of the attribute extraction. (Needed for the final model)
