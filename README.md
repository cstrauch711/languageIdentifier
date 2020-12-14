# language Identifier
Human Language Identifier with Deep Learning on WiLi-2018 Dataset

A need for consistent human language translation is growing as humanity becomes more globalized, which requires a need for what two languages are being translated. This project created a Deep Neural Network to identify a string of text into one of 63 common human languages taken from Wikipedia that used alphabetic writing systems. The data consisted of this one string feature that was vectorized using the “bag of words” method using characters instead of words to generate frequency vectors. The final testing accuracy of this neural network architecture was .

## Introduction:
As the world becomes increasingly connected, clear communication becomes even more essential. When different parties need to communicate, but do not share a common language, they must rely on translation to get their information across. Before even considering translating the material, it must be known what two languages you are translating between. This paper aims to explore the first step of this process by identifying a language that a piece of information is written in. This paper accomplishes this feat by training a machine learning model to identify what human language a short text string is written in. 

## Methods:
The data used in this project is from the WiLI-2018 database, which is free to use. The data consist of one variable, which is a short string of human language text along with one label of the human language name in English. All paragraphs of text are from Wikipedia and therefore constitute a less colloquial form of the languages, which is something to keep in mind. There are 235,000 observations evenly distributed amongst 235 various languages written in a variety of scripts in the original dataset, but I chose to take a subset of this data of only certain languages. I chose to do this because some languages are harder to work with than others; for example, various Chinese languages, and Japanese and Korean are hard to work with because this model works using character frequencies. These languages can consist of 1000s of characters because of their writing systems, so I chose to exclude them and work with languages with more alphabetized writing systems. To reduce the number of labels even further, languages were chosen somewhat arbitrarily that have a significant number of speakers. After narrowing down the languages, there are 63 labels used in total. A list of the languages used can be found after the citations.

After choosing the languages, the data consist of one feature that is the string of text in the human language and the label which is a 3-character label of the language, but it is later encoded into integers.

After acquiring the data, it was processed quite heavily. First, punctuation and digits were removed from the strings as those are common between all languages and will not aid in classification. As the texts are from wikipedia, there are often languages present in some sentences that do not belong to that particular class, such as in a citation or pronunciation inlet. This is typically not a problem, but Chinese characters in particular contribute well over a thousand new characters, which increases the feature space drastically, so these characters were removed in addition to the punctuation and digits using regex. After those characters were removed, the features were separated from the labels and the sklearn CountVectorizer() was used to implement the ‘bag-of-words’ method. The difference here is that instead of a bag of words, it is a bag of characters. The training and testing features were transformed with this vectorization and the labels were encoded with integers using sklearn’s LabelEncoder().
With the data processed and ready, a baseline logistic regression was used to create a baseline of the classification; the baseline was quite high at around 92% accuracy.
A deep neural network (DNN) was chosen as a machine learning algorithm for this classification problem because it is quite good at text classification with only a couple layers. The architecture used in this neural network is as follows:
>  Dense( 500, activation= ‘relu’ )
>  Dense( 500, activation= ‘relu’ )  
>  Dense( 500, activation= ‘sigmoid’ )  
>  Dense( 250, activation= ‘sigmoid’ )  
>  Dense( 63, activation=softmax )
  
  
The loss function used was “sparse_categorical_crossentropy” because the labels are categorical and formatted as integers  and with the ‘Adam’ optimizer. This architecture was created by playing around with different arrangements of layers with varying levels of neurons and tinkering around to raise the accuracy metrics. The RELU activation function always worked the best for this text data.
 
## Results:
The testing accuracy in the final model was: 0.915 .
To further improve this work, it would be helpful to further analyze the results to see which languages are being identified correctly and which are not. This could lead to some insight into why the model is not learning as well as it possibly could. It would also be useful to try other architectures or even transition to a convolutional neural network to try. Once an even better model is established, it would be very beneficial to find a solution to expand it to include many more languages and not just this small subset.


As the training and testing features are too large, please kindly refer to the links below for the testing and training data.

Testing Data Link: https://drive.google.com/file/d/1GFDUsAMbQWy6btUaWHwHK3IvKL7VdtNl/view?usp=sharing 
Training Data Link: https://drive.google.com/file/d/1OoiaZa2LML5Hy8I3bccQGiIQCcpYTrNB/view?usp=sharing 

The labels are provided in the data folder of this repository.

## Data and Original Paper
Data:  https://zenodo.org/record/841984#.X6CiLYhKhPY

## Languages Used:

Afrikaans
Albanian
Arabic
Armenian
Azerbaijani
Belarusian
Bengali
Bosnian
Croatian
Czech
Danish
Dutch
English
Esperanto
Estonian
Finnish
French
German
Gujarati
Haitian Creole
Hebrew
Hindi
Hungarian
Icelandic
Igbo
Indonesian
Irish
Italian
Kazakh
Kurdish
Latin
Latvian
Lithuanian
Malay
Malayalam
Maltese
Modern Greek
Mongolian
Norwegian Nynorsk
Panjabi
Persian
Polish
Portuguese
Romanian
Russian
Serbian
Slovak
Spanish
Swahili (macrolanguage)
Swedish
Tagalog
Tajik
Tamil
Telugu
Thai
Turkish
Turkmen
Ukrainian
Uzbek
Vietnamese
Wolof
Xhosa
Yoruba

