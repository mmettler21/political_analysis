<img src="static/titre2.png">

# Introduction

## Abstract

Donald Trump banned from twitter; this sentence should be familiar to you. In the last ten years, there has been an explosion of polemical phrases of all kinds. Most of the well-known newspapers have picked up these quotations and put them in their columns, and not only from Twitter... Thanks to the framework *Quobert*, developed by Robert West and others, we have a dataset of millions of quotations on hand coming from different newspapers between 2015 to 2020. The <b> million-dollar </b> question was the next one, what can we proceed with such a dataset?


To point out some interesting facts about these quotations, we have decided that we are going to focus on three main reading axes. Before doing this, the key step is <b> to read the entire dataset </b>. Once this has been done, we can then <b> much easily play with our data </b> ! Then, we decided to make <b> comparisons </b> between newspapers affiliated with <b> Democrats or Republicans </b>, and to see if there is an affiliation between the quotations reported in the newspapers and their political positioning. Since there are plenty of different newspaper, we decided <b> to focus initially on only two newspapers </b>, whose political views are well known. For doing comparisons between two newspapers, the objective is to analyze which <b> parameters </b> allow to make a difference between them. 

The three <b> parameters </b> we picked out are <b> topic detection, speakers, and sentiment analysis </b>. Once we analyze the quotations of two newspapers with those guidelines, the next step is apply the parameters whose give a signifcant results to other journals. That in order to produce a clear framework that would allow to compare newspapers and state their political affiliation.

# Methods

## Choice of the two reference newspapers

First, the choice of the two newspapers we will work with is crucial. Some journals have “centered” opinions or shaded positioning. That is why, the focus will be made on polarized newspapers, which will make it easier to study and define the parameters. For our study, two newspaper have been chosen: Foxnews and New York Times. Both are polarized, Foxnews is in favor of more conservative political positions and is mainly viewed by Republican partisans while New York Times is more left-leaning and followed mainly by Democrats (figure below, [Statista, consulted the 15.11.2021](https://www.statista.com/chart/21328/party-affiliation-by-news-source/)).


<a href="https://www.statista.com/chart/21328/party-affiliation-by-news-source/" title="Infographic: Party Affiliation Defines News Sources | Statista"><img src="https://cdn.statcdn.com/Infographic/images/normal/21328.jpeg" alt="Infographic: Party Affiliation Defines News Sources | Statista" width="50%" height="auto" align="center" style="width: 50%; height: auto !important; max-width:960px;-ms-interpolation-mode: bicubic;"/></a>

## Wrangling and reading the dataset


Concerning the reading of the data, our first approach was to read the dataset using chunks and then to generate a single pickle file from these chunks. The problem was that reading the chunks one after the other from the pickle file generated an extremely heavy file (the operation was stopped when the file size exceeded 150 Gigabytes!). 
Consequently, an alternative was proposed : the approach was to use only one chunk per pickle by reading the files of each year and combining them together. Then, we were able to generate a dataframe for each newspaper we were interested in, which whole quotations between 2015 and 2020.  


# Topic Detection

## Number of topics for each journal


Latent Dirichlet Allocation (LDA) is an unsupervised method which allow to create magically topics composed of specific words.
One has to specify the number of topics. To do so, the ideal number of topics for the newspaper has to be specified. We calculated the coherence score for different number of topics (from 2 to 10), the plots show the results. Then we have taken the number which corresponds to the highest score and we have plot the topics using PyLDAvis.

<body> 
<center> 
<h3> Determination of the number of topics for the New York Times </h3>
   <div id="includedContent1"></div>
   </center> 
</body> 

<p align="center">
  <img width="600" src="static/c_v_score_NYtimes.png">
</p>


<body> 
<center> 
<h3> Determination of the number of topics for Fox News </h3>
   <div id="includedContent1"></div>
   </center> 
</body> 

<p align="center">
  <img width="600" src="static/c_v_score_Fox.png">
</p>

Some observations can be made :
<ul>
  <li>The Coherence C_V predicts 3 topics for the New York Times and 9 topics for Fox news.</li>
<li> Whereas for Fox News, an increasing tendency is noticed, for New York times, the optimal number of topics is low and equals 3. One could think that Fox News speaks more about different subjects. But another analysis would be that actually New York times treats more about various subjects so it is hard to put them into several topics as there is a lot of them and it is hard to separate the words into clear topics.
 </li>
</ul>


## Visualisation of the number of topics

<body> 
<center> 
<h3> Topic Detection for the New York Times </h3>
   <div id="includedContent1"></div>
   </center> 
</body> 

<iframe src="static/LDAvis_prepared_NY_3topics.html" style="width: 1200px; height: 700px; border: 0px"></iframe>

<body> 
<center> 
<h3> Topic Detection for the Fox News </h3>
   <div id="includedContent1"></div>
   </center> 
</body> 

<iframe src="static/LDAvis_prepared_Fox_9topics.html" style="width: 1200px; height: 700px; border: 0px"></iframe>

## Comparison between topics for the New York Times and Fox News

Topic detection plots LDA:
Most salient words:
For NY times it is mostly democrat terms/ neutral terms: 
Fox News: republicans, border, anti, god, white
Democrat is a salient word for NY while Republicans is one for Fox.


# What can be said about the number behind the quotations ?

<table style="width:100%">
  <tr>
    <th></th>
    <th>p-value</th>
  </tr>
  <tr>
    <td>Fear</td>
    <td>0.496</td>
  </tr>
  <tr>
    <td>Happy</td>
    <td>0.105</td>
  </tr>  
  <tr>
  <td>Angry</td>
  <td>0.277</td>
</tr>
<tr>
  <td>Surprise</td>
  <td>0</td>
</tr>
   
<tr>
<td>Sad</td>
<td>0.231</td>
</tr>
   
<caption>p-value for the covid emotions for both newspapers
</caption>
   
   

</table>

<table style="width:100%">
  <tr>
    <th></th>
    <th>p-value</th>
  </tr>
  <tr>
    <td>Immigration</td>
    <td>0.000000e+00</td>
  </tr>
  <tr>
    <td>Terrorism</td>
    <td>0.000000e+00</td>
  </tr>  
  <tr>
  <td>Climate change</td>
  <td>2.331170e-01</td>
</tr>
<tr>
  <td>Abortion</td>
  <td>4.609667e-67</td>
</tr>
   
<tr>
<td>Religion</td>
<td>0.000000e+00</td>
</tr>
   
<tr>
 <td>Racism</td>
 <td>8.309947e-51</td>
</tr>
   
<caption>p-value for the covid emotions for both newspapers
</caption>

</table>

## Quotes counting

A part of the story told by our data is taken from the study of two newspapers, the New York Times and Fox news, from which the occurrences of quotations made by each newspaper was analysed. 
To begging with, the data showed that the New York Times had more quotations available in the Quotebank dataset than Fox news. The number of quotations found for the New York Times was of 894838 quotes compared to 708383 for Fox News. 
Then, by searching for some topics where it is known republicans and democrats have opposing opinions, the occurrences of certain topic-related quotations were analysed for each newspaper. 
This choice of quotations was done thanks to a selection of words that usually are employed when talking about the chosen topics. Besides, each word was mapped to the same, normalized form, by stripping affixes (words stemming) whenever possible. This allowed to cover a higher range of quotations that could be related to the chosen topics of immigration, terrorism, climate change, abortion, religion, racism. 
The first thing that could be noticed is that even though the number of quotations from the New York Times in the Quotebank dataset is larger than the one from Fox News, the later has, in general, more quotations about the selected topic. This behavior was observed for all topics, except for climate change where their normalized occurrences were similar (as shown in the plot number###). Here the normalization was done by dividing the number of quotations obtained, for each topic and each newspaper, by the total number of quotations of each newspaper. The percentage of immigration related quotes cited by the New York Times related to the total amount of quotes the New York Times cites is then, for example, obtained and can be compared to the corresponding quotes percentage from Fox News. 


<body> 
<center> 
<h3> Word normalization by stemming </h3>
   <div id="includedContent1"></div>
   </center> 
</body> 

<p align="center">
  <img width="600" src="static/words_updated.png">
</p>

Additionally, a t-test was done to search for a correlation between our results and as expected, only the p-value of topics related to climate change was higher than a significance level of 0.05 and thus have comparable means. 


<table style="width:100%">
  <tr>
    <th></th>
    <th>p-value</th>
  </tr>
  <tr>
    <td>Fear</td>
    <td>0.496</td>
  </tr>
  <tr>
    <td>Happy</td>
    <td>0.105</td>
  </tr>  
  <tr>
  <td>Angry</td>
  <td>0.277</td>
</tr>
<tr>
  <td>Surprise</td>
  <td>0</td>
</tr>
   
<tr>
<td>Sad</td>
<td>0.231</td>
</tr>
   
<caption>p-value for the covid emotions for both newspapers
</caption>
   
   

</table>
It seems here once again, that Fox News prefers to talk more about those topics that the New York Times, which consolidates the hypothesis elaborated in the topic detection section of this data story. Here, this could be maybe explained by the fact that the New York Times has other priorities than this sensitive themes. 

# Sentiment analysis

The sentiment analysis between the two journals has been done thanks to two libraries: NLTK and text2emotion. For the first one the function “SentimentIntensityAnalyzer” has been use, it helps determined if the sentiments of a text are positive or negative. On the other hand, text2emotion capture the intensity of these 5 emotions: fear, happiness, anger, surprise and sadness.
The dataset has been analysed in two forms: all the quotes by the NY times and Foxnews year by year, and the quotes from these two journals on certain subjects.

## Year by year analysis:

<body> 
<center> 
<h3> Comparison of negative sentiments between Foxnews and the NY times year by year with NLTK </h3>
   <div id="includedContent1"></div>
   </center> 
</body> 

<p align="center">
  <img width="600" src="static/SA_f1.png">
</p>

This analysis showed some consistency as each year (except for 2015), the quotes from Foxnews were more negative than the one from the NYtimes. For the emotions, text2emotion function found that the quotes from Foxnews had more surprise and sadness. The fear emotion is about equal for all years between the two journals except for 2015 and 2020 where the quotes from Foxnews have more of this emotion.

## By subject analysis:

Six subjects were analysed: immigration, terrorism, climate change, abortion, religion and racism. The ones that showed the most differences are immigration, terrorism and religion where positive and negative from NLTK but also fear, surprise and sadness had low pvalues when comparing the distribution of these for the two journals.

<body> 
<center> 
   <h3> Comparison of emotions about <b> immigration </b> between Foxnews and the NY times with text2emotion </h3>
   <div id="includedContent1"></div>
   </center> 
</body> 

<p align="center">
  <img width="600" src="static/SA_f2.png">
</p>

For climate change Foxnews was a lot more negative. The abortion and racism subjects did not show big differences.

<body> 
<center> 
<h3> Comparison of positive and negative sentiments about <b> climate change </b> between Foxnews and the NY times with NLTK </h3>
   <div id="includedContent1"></div>
   </center> 
</body> 

<p align="center">
  <img width="600" src="static/SA_f3.png">
</p>



# Conclusion

Bla Bla Bla




<b> Mettler Marc, Goulart Maia Manuela, M'Saada Sinda, Charroin François </b>
<br>
ADA, EPFL, December 2021
<br>
<a href="https://github.com/epfl-ada/ada-2021-project-therealabracadabra"><b>GitHub Repository</b></a>
•
<a href="https://github.com/mmettler21/political_analysis"> <b> Website Repository </b> </a>
<br>
<b>Theme </b>
<a href="https://github.com/chibicode/duo">duo</a>
<b>by </b>
<a href="https://github.com/chibicode">Shu Uesugi</a>
Title image 
<a href="https://github.com/chibicode/duo">duo</a>
<br>
Title image : [Pew Research Center, consulted the 17.12.2021](https://www.pewresearch.org/fact-tank/2021/11/22/both-republicans-and-democrats-prioritize-family-but-they-differ-over-other-sources-of-meaning-in-life/)




<a href="https://github.com/epfl-ada/ada-2021-project-therealabracadabra" class="github-corner"><svg width="80" height="80" viewBox="0 0 250 250" style="fill:#151513; color:#fff; position: absolute; top: 0; border: 0; right: 0;">
        <path d="M0,0 L115,115 L130,115 L142,142 L250,250 L250,0 Z"></path>
        <path d="M128.3,109.0 C113.8,99.7 119.0,89.6 119.0,89.6 C122.0,82.7 120.5,78.6 120.5,78.6 C119.2,72.0 123.4,76.3 123.4,76.3 C127.3,80.9 125.5,87.3 125.5,87.3 C122.9,97.6 130.6,101.9 134.4,103.2" fill="currentColor"
            style="transform-origin: 130px 106px;" class="octo-arm"></path>
        <path
            d="M115.0,115.0 C114.9,115.1 118.7,116.5 119.8,115.4 L133.7,101.6 C136.9,99.2 139.9,98.4 142.2,98.6 C133.8,88.0 127.5,74.4 143.8,58.0 C148.5,53.4 154.0,51.2 159.7,51.0 C160.3,49.4 163.2,43.6 171.4,40.1 C171.4,40.1 176.1,42.5 178.8,56.2 C183.1,58.6 187.2,61.8 190.9,65.4 C194.5,69.0 197.7,73.2 200.1,77.6 C213.8,80.2 216.3,84.9 216.3,84.9 C212.7,93.1 206.9,96.0 205.4,96.6 C205.1,102.4 203.0,107.8 198.3,112.5 C181.9,128.9 168.3,122.5 157.7,114.1 C157.9,116.9 156.7,120.9 152.7,124.9 L141.0,136.5 C139.8,137.7 141.6,141.9 141.8,141.8 Z"
            fill="currentColor" class="octo-body"></path>
    </svg></a>
<style>
    .github-corner:hover .octo-arm {
        animation: octocat-wave 560ms ease-in-out
    }

    @keyframes octocat-wave {

        0%,
        100% {
            transform: rotate(0)
        }

        20%,
        60% {
            transform: rotate(-25deg)
        }

        40%,
        80% {
            transform: rotate(10deg)
        }
    }

    @media (max-width:500px) {
        .github-corner:hover .octo-arm {
            animation: none
        }

        .github-corner .octo-arm {
            animation: octocat-wave 560ms ease-in-out
        }
    }

    #ada { background:none;border:none;color:white }
</style>

<script>
function includeHTML() {
  var z, i, elmnt, file, xhttp;
  /* Loop through a collection of all HTML elements: */
  z = document.getElementsByTagName("*");
  for (i = 0; i < z.length; i++) {
    elmnt = z[i];
    /*search for elements with a certain atrribute:*/
    file = elmnt.getAttribute("w3-include-html");
    if (file) {
      /* Make an HTTP request using the attribute value as the file name: */
      xhttp = new XMLHttpRequest();
      xhttp.onreadystatechange = function() {
        if (this.readyState == 4) {
          if (this.status == 200) {elmnt.innerHTML = this.responseText;}
          if (this.status == 404) {elmnt.innerHTML = "Page not found.";}
          /* Remove the attribute, and call this function once more: */
          elmnt.removeAttribute("w3-include-html");
          includeHTML();
        }
      }
      xhttp.open("GET", file, true);
      xhttp.send();
      /* Exit the function: */
      return;
    }
  }
}
</script>

<script>
includeHTML();
</script>


