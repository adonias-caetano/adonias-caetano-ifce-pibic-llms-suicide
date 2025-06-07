 # Large Language Models in the Identification of Suicidal Ideation in Non-Clinical English Texts

<p align="center">
This repository provides LLMs codes used to identify suicidal ideation in non-clinical texts in English.
</p>

## :mortar_board: Authors
<p align="center">
Laís Carvalho Coutinho, Antonia Estefane Ribeiro Veras, Rosana Celine Pinheiro Damaceno, Adonias Caetano de Oliveira, and Ariel Soares Teles
</p>

This study is the result of three scientific initiation and technological development research projects, namely PIBIC/IFCE (2023-2024), PIBIC/IFCE (2024-2025), and PIBITI/IFCE (2024-2025).

<div align="justify">

 ## 📋 Requirements

* Google Colab
* python pandas library
* python unidecode library
* python word_tokenize, stopwords, sent_tokenize (nltk) libraries
* python wordcloud library
* python matplotlib.pyplot library
* python transformers library
* python seaborn library
* python imblearn.under_sampling library
* python sklearn.model_selection library

## 📖  Dataset

Two textual datasets were used in this study. The first dataset was the <a href="https://www.kaggle.com/datasets/nikhileswarkomati/suicide-watch"><strong>"Suicide and Depression Detection"t</strong></a> (SDD), available in the Kaggle repository. It is a collection of posts from the "SuicideWatch" and "depression" subreddits on the social network Reddit. The dataset has two main columns: "text" and "class". The "text" column contains the posts, while the "class" column indicates whether the post is classified as "suicide" or "non-suicide". The labelling process has not been validated by mental health professionals.

The second dataset was the <a href="https://github.com/ayaanzhaque/SDCNL"><strong>"Suicide vs Depression Classification"t</strong></a> (SDCNL), which gathers user posts extracted from the r/SuicideWatch and r/depression subreddits on Reddit, totalling 1,895 posts. Post texts from r/SuicideWatch were labelled as suicidal, while those from r/Depression were labelled as depressive. To validate the label correction methodology, the Reddit Suicide C-SSRS dataset was used, containing 500 posts from the r/Depression subreddit, classified by psychologists according to the Columbia Suicide Severity Rating Scale. Furthermore, validation was strengthened with the IMDB Large Movie Dataset, an NLP benchmark containing 50,000 polarised movie reviews.

The SDCNL is a modified combination of these datasets (n = 8853 sentences) for binary classification of clinically healthy versus suicidal texts, using posts from the r/CasualConversation and r/SuicideWatch subreddits. r/CasualConversation, a general conversation subreddit, was used as a reference for clinically healthy texts. The resulting samples were organised into two columns: "text", containing the textual content of the post, and "target", with the label assigned to the sample. The posts were labelled by experts in a binary manner, with "0" attributed to the absence of suicidal ideation (negative class) and "1" to the presence of suicidal ideation (positive class).

## 🛠 Fine-tuning BERT-based Models

For the SDD dataset, fine-tuning was performed on four BERT-based models, namely BERT-Base, RoBERTa, Mental-RoBERTa, and AlBERT. To evaluate these models, the SDD dataset was divided into 80% for training and 20% for testing. Of the 80% allocated for training, 20% was reserved for validation.
The BERT-Large, mBERT, RoBERTa, Mental-RoBERTa, and AlBERT models were applied to the SDCNL dataset. Due to the length of the sentences (number of words) in SDCNL, the models were trained on 7,011 sentences and tested on 100 pre-selected sentences, randomly chosen (50 sentences from each class). Of the training subset, 20% was reserved for validation in each training epoch.

The fine-tuning of each BERT model was performed using the validation data subset at the end of each epoch, with a batch size of 16, including weight adjustments to maintain generalisation. Among the models applied to the SDD dataset, only AlBERT was trained for 13 epochs, while the remaining models were trained over 4 epochs.
As for the models applied to the SDCNL dataset, only mBERT was trained for 10 epochs, while the others were trained for 8 epochs. All BERT models were configured with a learning rate of 2e-6 to ensure more stable convergence and were fed with tokenised inputs of up to 128 tokens to maintain consistency in the vector representation of sentences.

## 🛠 Use of Generative LLMs

Due to the performance of BERT models on the SDCNL dataset, this study explored generative LLMs, including ChatGPT-4o, Gemini 1.5 Flash, Copilot (Azure Cognitive Services), and DeepSeek. A total of 100 sentences (50 from each class) were selected from the SDCNL test set to be used in the evaluation of generative LLMs, which did not require data pre-processing. The 100 sentences were evenly distributed between two classes (50 from each) for assessment, and the test was conducted without the need for pre-processing.

The application of generative LLMs required prompt engineering to guide model output. A zero-shot prompt structure was adopted, without examples of positive or negative sentences, as outlined in Table 1. Gemini was accessed via Google's Application Programming Interface (API) within the Google Colaboratory environment, using HTTP requests in a prompt-response format. A Python script implemented in Google Colab applied the prompt for queries to ChatGPT-4o via an API key. Copilot, already integrated into the Microsoft Azure platform, was used directly within the Google Colaboratory environment through a Python script, without requiring a customised prompt. DeepSeek was the only model consulted manually. Therefore, the methodology of using 100 sentences for generative LLMs was also adopted to ensure a fair comparison between these models.

## 🤖 Access our submitted article

Published paper in the <a href="https://sbbd.org.br/2025/eniac/"> <strong>35ª Conferência Brasileira de Sistemas Inteligentes (BRACIS)/Encontro Nacional de Inteligência Artificial e Computacional
 (ENIAC) </strong></a>

### [Paper Link]() 

## 👏 Contributing
 
If there is a bug, or other improvement you would like to report or request, we encourage you to contribute.

Please, feel free to contact us for any questions: [![Gmail Badge](https://img.shields.io/badge/-adonias.oliveira@ifce.edu.br-c14438?style=flat-square&logo=Gmail&logoColor=white&link=mailto:adonias.oliveira@ifce.edu.br)](mailto:adonias.oliveira@ifce.edu.br)


## 📚 References

* <a href="https://www.mdpi.com/2227-9032/10/4/698"><strong>Paper about Boamente System</strong></a>.
* <a href="https://www.sciencedirect.com/science/article/pii/S1877050922009668"><strong>Paper about XAI Boamente System</strong></a>.
* <a href="https://www.scielo.br/j/csp/a/XrbVfvybPj9tvJ8qWv7j8VC/?lang=en"><strong>Comparative analysis of LLMs for detecting suicidal ideation</strong></a>.
* <a href="https://ieeexplore.ieee.org/document/10945851"><strong>Effect of XAI on Trust of Mental Health Professionals in an AI-Based System for Suicide Prevention</strong></a>.
