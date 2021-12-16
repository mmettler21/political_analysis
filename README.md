# Data story of the real Abrac'ada'bra

## Introduction

### Abstract

Donald Trump banned from twitter; this sentence should be familiar to you. In the last ten years, there has been an explosion of polemical phrases of all kinds. Most of the well-known newspapers have picked up these quotations and put them in their columns, and not only from Twitter... Thanks to the framework *Quobert*, developed by Robert West and others, we have a dataset of millions of quotations on hand coming from different newspapers between 2015 to 2020. The million-dollar question was the next one, what can we proceed with such a dataset?

To point out some interesting facts about these quotations, we have decided that we are going to focus on three main reading axes. Before doing this, the key step is to read the entire dataset. Once this has been done, we can then much easily play with our data! The three focus we picked out are about topic detection, speakers, and sentimental analysis. Once we analyse the quotations with those guidelines, the goal is to make comparisons between newspapers affiliated with Democrats or Republicans, and to see if there is an affiliation between the quotations reported in the newspapers and their political positioning. Since there was plenty of different newspaper, we decided to focus initially on only two newspapers, whose political views were well known.



This project aims at studying the political affiliation of some newspapers based on the dataset set given from 2015 to 2020. The main idea is to choose some newspapers that have a known and clear positioning and then study some “key parameters” through the dataset to check if they support or correlate with our statement (political affiliation). The parameters would have to be defined from the beginning according to the journal’s beliefs. The objective being to analyse which parameters (linguistic differences, topics spoken about, personalities cited, …) would allow to make a difference between them. Once a link is made between “parameters” and newspaper positioning, a second goal would be to repeat this work on other journals, less known or not, and see if we could determine their political affiliation. Thus, the idea is to produce a clear framework that would allow to compare newspapers and state their political affiliation.

## Research questions

Many questions have to be studied before defining the method. First, some journals have “centered” opinions or shaded positioning. That is why, the focus will be made on polarized newspapers, which will make it easier to study and define the parameters. 

plotly.offline.plot(fig,filename='images/Lda_Fox.html',config={'displayModeBar': False})

<body> 
<center> 
<h3> Comparison between the distribution of posts during the day across our platforms </h3>
   <div id="includedContent1"></div>
   </center> 
</body> 

<p align="center">
  <img width="600" src="images/Percent_quotations.png">
</p>

<script>
<p align="center">
  <img width="600" src="images/brouillon.png">
</p>
 </script>

A first question would be: What are the main topics on which the newspaper diverge and do not agree? This one would have to be checked upstream, and then further developed using the dataset.

<p align="center">
  <img width="600" height="200" src="images/brouillon.png">
</p>

A second one would be to make a sentimental analysis of the quotations used in the newspapers and observe if there's any clear difference depending on the political affiliation. This [paper](https://engineering.stanford.edu/magazine/article/what-different-about-how-democrats-and-republicans-talk-online) analyzing the differences between both parties, which had studied tweets from Republicans and Democrats, showed that both don’t use the same sentiments when discussing about guns shooting and also depending on the shooter race.

<a href="https://www.statista.com/chart/21328/party-affiliation-by-news-source/" title="Infographic: Party Affiliation Defines News Sources | Statista"><img src="https://cdn.statcdn.com/Infographic/images/normal/21328.jpeg" alt="Infographic: Party Affiliation Defines News Sources | Statista" width="50%" height="auto" align="center" style="width: 50%; height: auto !important; max-width:960px;-ms-interpolation-mode: bicubic;"/></a>

A third research question would be to verify whether the newspapers cite more public figures which share their opinions.
Another questions would be to study if there's any linguistic and semantic difference between the newspapers. As in this study about computational semantics of language, which showed that Democrats use more modal verbs compared to Republicans to call for action.

A fourth approach would be to determine the importance of certain topics, depending on the political position of the journals. This would be done by looking at the percentage of quotes using a certain vocabulary. 

Another question would be to verify if our study which will be based only on quotations is accurate or not.

![This is an image](https://myoctocat.com/assets/images/base-octocat.svg)

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


