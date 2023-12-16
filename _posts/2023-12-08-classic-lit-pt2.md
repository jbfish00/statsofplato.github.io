---
layout: post
title:  "Classic Fiction of the World: Data Visualizations (IN PROGRESS)"
author: Jacob B. Fisher
description: "Insights on the Top 500 Novels" 
image: "assets/images/Plato Among Books.png"
---

## Introduction
Welcome to part 2 of our exploration through classic fiction of the world! In our [previous post](https://jbfish00.github.io/statsofplato.github.io/2023/12/07/classic-lit-pt1.html), we breifly discussed why one might want to look at data on classic literature. You'll remember that we scraped data from the [OCLC Library 100 List](https://www.oclc.org/en/worldcat/library100/top500.html) and the [List of best-selling books](https://en.wikipedia.org/wiki/List_of_best-selling_books) Wikipedia page then cleane and combined that data with data provided by Shane Sherman of [https://thegreatestbooks.org/](https://thegreatestbooks.org/). 

In this post, we will explore that data visually to see if we can answer questions such as:

-Where are the most popular books in the world from?
-When were these books written?
-Who are the most prolific authors of the books that are considered classics?


## Visualizations

# Country Data
Countries and Their Ranks in Literature:

I wanted to illustrate countries and their best ranked book that they produced. A scatter plot seems like an odd choice, but I couldn't figure out any better way to show this. Despite the simplicity of this graph, a lot of information is packed in it. Of course we see each country and the best rank one of their books achieves, but in this we see which countries dominate certain intervals of the ranking system. 

For example, since Russia's best book is ranked 22, that means that the three countries listed before it (Spain, United Kingom, and United States) are the only countries with books ranked from 1-21. Looking out to the top 50, only seven countries produced all of the top 50 books, since Italy, listed eighth, has its best ranked book at 53.

![Country with best rank](/statsofplato.github.io/assets/lit_EDA/Country_with_best_rank.png)

Mapping Literary Proliferation:

The impetus for this project was to get a macro view of great world fiction. The below choropleth map highlights the global distribution of literary works. Note that the scale here is a log scale to better distinguish differences between countries on the lower end of the scale. The United States, Britain, France, Columbia, Russia, Germany, and Canada each stand out as producing a higher number of books on this top 500 list. This visualization not only illustrates the concentration of literary production in these regions but also raises questions about the factors contributing to such disparities. This and other visuals we will see later caused me to ponder on possible language bias in the data. WorldCat claims that its list consolidates lists of libraries around the world, though it isn't hard to imagine most of their data still coming from libraries in the United States.

![Map](/statsofplato.github.io/assets/lit_EDA/Map_plot.png)

Bestsellers by Country:

When looking at all bestseller data, it is important to keep in mind that the term "bestseller" is determined solely on whether or not it was on Wikipedia's bestseller list. I noted in my previous post that Wikipedia acknowledges that some books may have sold tens of millions of copies, but because they have no reliable data, those books are omitted. These include such books as *The Lord of the Rings* trilogy. Thus most books that are classified as bestsellers are more modern.  

The United States and the United Kingdom take the lead by a significant margin, likely due to the widespread influence of the English language and the global reach of their cultural products. Yet, the presence of countries like Nigeria and Afghanistan on the graph brings to light the rich narratives emerging from different cultural contexts, which may signal a Western desrire for a great variety in literary tradition.

![Bestsellers by Country](/statsofplato.github.io/assets/lit_EDA/Bestsellers_by_country.png)



![Top Authors](/statsofplato.github.io/assets/lit_EDA/Top_authors.png)
![Rank and Author](/statsofplato.github.io/assets/lit_EDA/Rank_distribution_boxplot_Top_10_Authors.png)

![Rank Genre Boxplot](/statsofplato.github.io/assets/lit_EDA/Rank_genre_boxplots.png)
![Genre by Decade](/statsofplato.github.io/assets/lit_EDA/books_by_genre_by_decade.png)


## Summary

## Conclusion


#The visualizations you chose previously along with commentary and insights.
#A summary of the most intriguing findings from your data and how the EDA
#A concluding statement.


<p style="text-align: center"><em>“Ignorance, the root and stem of every evil.”
― Plato</em></p>
