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


# PARTIE MANU :  What can be said about the number behind the quotations ?

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

## WORDS ????

We selected some words that we thought they can differentiate democrats and republicans and we analyze their frequency of apparencies in the Quotebank. We notice that even though the number of quotations from the New York Times in the Quotebank dataset is larger than the one from Fox News <b> (mettre NUMBER !!!!!!!!!!!!!) </b>, the later has more quotations about those topics than the other one, except for climate change where their occurrences are similar. From this we can maybe elaborate a first hypothesis that Fox News gives a higher importance to sensitive topics. 

<body> 
<center> 
<h3> Word normalization by stemming </h3>
   <div id="includedContent1"></div>
   </center> 
</body> 

<p align="center">
  <img width="600" src="static/words_updated.png">
</p>

A t-test was done to search for a correlation between our results and as expected, only the p-value of topics related to climate change was higher than 0.05 <b> (ALPHA !!!!!!!!!!!!!) </b> and thus their means are comparable. This could be maybe explained by the fact that the New York Times has other priorities. 


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


# Example image

<p style="text-align:center;"><img src="static/images/ccdf.png"></p>


# Table example


<table style="width:100%">
  <tr>
    <th>Social Network</th>
    <th>Data</th>
  </tr>
  <tr>
    <td>Twitter</td>
    <td>3 millions of tweets from 4k users</td>
  </tr>
  <tr>
    <td>Stack Overflow</td>
    <td>1 million of comments from 22k of users</td>
  </tr>
  <tr>
    <td>Weibo</td>
    <td>40k posts from 431 users </td>
  </tr>
  <tr>
    <td>Reddit</td>
    <td>272k comments from french subreddit</td>
  </tr>
</table>

# HTML example

<html> 
  <head> 
    <script src="jquery.js"></script> 
    <script> 
    $(function(){
      $("#includedContent1").load("static/Lda_Fox.html"); 
    });
    </script> 
  </head> 

  <body> 
  <center> 
  <h3> Comparison between the distribution of posts during the day across our platforms </h3>
     <div id="includedContent1"></div>
     </center> 
  </body> 
</html>

# Retour à la ligne, exemple

Based on the graphs, some observations can be made:
<ul>
  <li><b>Usage drops across all platforms at night</b>, and increases in the morning.</li>
  <li>While for <b>Twitter and Weibo</b>, usage continues to increase during the day and lowers at night, starting at around 9pm, the trend seems to differ for Reddit and Stack Overflow. For these platforms, <b>the activity drops earlier</b>, at around 2pm for Reddit and 3pm for Stack Overflow.</li>
  <li>Stack Overflow is a work-oriented platform, these observations are in line with the usage we expect. The <b>users are mainly active during work hours (9pm-5am)</b>. We can even see little drops at lunch time. </li>
  <li>The same remark as the previous one can be made about Reddit even if it can be surprising considering that it is a social network that contains all kinds of contents. </li>
</ul>

# Table 2, example

<table style="width:100%">
<caption>Distribution of the posts/hour disregarding the day of the week
</caption>
  <tr>
    <th></th>
    <th>00-06am</th>
    <th>06-12am</th>
    <th>12am-06pm</th>
    <th>06-12pm</th>
  </tr>
  <tr>
    <td>Twitter</td>
    <td>15.2%</td>
    <td>19.2%</td>
    <td>28.3%</td>
    <td>37.3%</td>
  </tr>
  <tr>
    <td>Stack Overflow</td>
    <td>7.5%</td>
    <td>29.7%</td>
    <td>40.7%</td>
    <td>22.1%</td>
  </tr>  
  <tr>
  <td>Weibo</td>
  <td>9.3%</td>
  <td>23.1%</td>
  <td>32.2%</td>
  <td>35.4%</td>
</tr>
<tr>
  <td>Reddit</td>
  <td>6.7%</td>
  <td>28.9%</td>
  <td>39.5%</td>
  <td>24.9%</td>
</tr>

</table>

# HTML, Example 2


After having studied the activity related to the posts and comments, let's dive into the users' activity.

<html> 
  <head> 
    <script src="jquery.js"></script> 
    <script> 
    $(function(){
      $("#includedContent3").load("static/Lda_Fox.html"); 
    });
    </script> 
  </head> 

  <body> 
  <center> 
  <h3> Comparison between the distribution of active users during the day across our platforms </h3>
     <div id="includedContent3"></div>
     </center> 
  </body> 
</html>

The distribution of active users by time of day and day of the week <b>does not differ dramatically to the posts</b>. We can still note a few interesting observations. For Twitter the number of active users <b>does not increase as fast as the number of tweets during the day</b>. It seems that people tend to tweet more at the end of the day. For Stack OverFlow,<b> the peaks in number of comments correspond to the peak in active users</b>. Finally for Weibo, trends are very similar across both of the distributions.

# Conclusion

Bla Bla Bla


<ul>
  <li><b>Mettler Marc, Goulart Maia Manuela, M'Saada Sinda, Charroin François</b></li>
  <li>EPFL - ADA 2021 - December 2021</li>
  <li>Our [GitHub Repository]('https://github.com/epfl-ada/ada-2021-project-therealabracadabra') </li>
  <li>["Website Repository"](https://github.com/mmettler21/political_analysis) </li>
  <li>[Theme duo](https://github.com/chibicode/duo), by [Shu Uesugi](https://github.com/chibicode) </li>
  <li>[GitHub Repository](https://github.com/epfl-ada/ada-2021-project-therealabracadabra) </li>
</ul>



Mettler Marc, Goulart Maia Manuela, M'Saada Sinda, Charroin François
<br>
<button id="ada"><b>ADA</b></button>, EPFL, December 2021
<br>
<a href="https://github.com/epfl-ada/ada-2021-project-therealabracadabra"><b>GitHub Repository</b></a>
•
<a href="https://github.com/mmettler21/political_analysis"> <b> Website Repository </b> </a>
<br>
<b>Theme </b>
<a href="https://github.com/chibicode/duo">duo</a>
<b>by </b>
<a href="https://github.com/chibicode">Shu Uesugi</a>




<br>
<footer style="background-color: #d32f2f>
    <div class="container">
        <div class="row ">
            <div class="col text-white text-center">
                <p>
                    <br>
                    Mettler Marc, Goulart Maia Manuela, M'Saada Sinda, Charroin François
                    <br>
                    <button id="ada"><b>ADA</b></button>, EPFL, December 2021
                    <br>
                    <a href="https://github.com/epfl-ada/ada-2021-project-therealabracadabra"><b>GitHub Repository</b></a>
                    •
                    <a href="https://github.com/mmettler21/political_analysis"> <b> Website Repository </b> </a>
                    <br>
                    <b>Theme </b>
                    <a href="https://github.com/chibicode/duo">duo</a>
                    <b>by </b>
                    <a href="https://github.com/chibicode">Shu Uesugi</a>
                    <br>
                </p>
            </div>
        </div>
    </div>

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


