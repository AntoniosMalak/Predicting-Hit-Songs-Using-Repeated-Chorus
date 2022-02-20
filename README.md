# Predicting-Hit-Songs-Using-Repeated-Chorus
Songwriters and producers have long believed writing a successful hook is what makes a song popular. In this work, we examined this myth by creating a data set of choruses from popular artists and applied five supervised Machine Learning techniques to predict the popularity purely based on the audio features extracted from a 15s chorus.
## This is a report of what I did in this project...
______
### [Collect data](https://github.com/AntoniosMalak/Predicting-Hit-Songs-Using-Repeated-Chorus/blob/main/CollectData.ipynb)
- Here I collected data as a (name of artist, title of song, label which 1 for popular and 0 for unpopular) by using [`billboard`](https://github.com/guoguo12/billboard-charts) package to collect data from [Billboard.com](https://www.billboard.com/).
- I collected data for the top 10 artists from 2006 to 2021 for popular songs.
- For unpopular songs, I collected other songs from the same artists from 2006 to 2021.
- Finally, check if I have any missed data.

### [Download full songs](https://github.com/AntoniosMalak/Predicting-Hit-Songs-Using-Repeated-Chorus/blob/main/DownloadFullSongs.ipynb)
- I downloaded all songs I collected before by using [`yt_dlp`](https://github.com/yt-dlp/yt-dlp) package to download all songs as mp3 extension from [Youtube](https://www.youtube.com/).
  - <b>`Note:`</b> download songs by using the title of song and the name of artist to avoid downloading another audio.
- Make a new dataset or just add it to the last one by adding a path column that includes the path of songs.
- Finally, check if I have any missed data.

### [Extract repeated chrous](https://github.com/AntoniosMalak/Predicting-Hit-Songs-Using-Repeated-Chorus/blob/main/ExtractTheRepeatedChorus.ipynb)
- By using the [`pychorus`](https://github.com/vivjay30/pychorus) package, extract repeated chorus as wav extension from songs I downloaded from the above step.
  - <b>`Note:`</b> there are some songs that cannot extract repeated chorus so I made it return None to drop it later.
- Finally, check if I have any missed data.

### [Extract audio features](https://github.com/AntoniosMalak/Predicting-Hit-Songs-Using-Repeated-Chorus/blob/main/ExtractAudioFeature.ipynb)
- By using the [`librosa`](https://librosa.org/) package I extract audio fetaures 518 features for every song.
- For every feature, I get statistics for each feature as mean, median, kurtosis, minimum, and so on....
- I used features like chroma_stft, chroma_cqt, spectral_bandwidth, zero_crossing_rate, rms, and so on.....
- Finally, check if I have any missed data.

### [Data analysis](https://github.com/AntoniosMalak/Predicting-Hit-Songs-Using-Repeated-Chorus/blob/main/DataAnalysis.ipynb)
- I used pair plot of the median value of all major audio features

![pair plot of the median value of all major audio features](https://user-images.githubusercontent.com/57007944/153756175-361fa013-30f0-4680-b5ef-d20a292d203c.jpg)

- Used plot explained variance to see how may features I need to reach 95% variance

![plot explained variance](https://user-images.githubusercontent.com/57007944/153756249-ab1a9c18-ed48-40b1-a210-5f0309f96a46.jpg)
- Finally, get best features I got from last two steps.

### [Build models](https://github.com/AntoniosMalak/Predicting-Hit-Songs-Using-Repeated-Chorus/blob/main/Chours%20Model.ipynb)
- Build seven classification models like LogisticRegression, LinearDiscriminantAnalysis, RandomForestClassifier, and so on....
- See accuracy, f1, recall and precision for training and validation.
- Compare all models and use the best in develop.

### [Develop](https://github.com/AntoniosMalak/Predicting-Hit-Songs-Using-Repeated-Chorus/tree/main/Devolp)
- Use [`Flask`](https://flask.palletsprojects.com/en/2.0.x/) to classify songs which is popular and unpopular.
- And I did this very simple API.

![Unpopular](https://user-images.githubusercontent.com/57007944/153757517-7367889e-3ea5-42ac-86e1-3c73030f75d0.jpg)
 
![Popular](https://user-images.githubusercontent.com/57007944/153757535-e218e190-ea6b-4b64-84b8-d4e8c3f45a94.jpg)

Thanks for reading :)

