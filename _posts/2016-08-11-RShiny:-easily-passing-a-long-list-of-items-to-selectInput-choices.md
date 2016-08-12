---
layout: post
title: Shiny&#58 easily passing a long list of items to selectInput choices
tags: [Blog]
---
Recently, I'm working on R Shiny to design a Web App. I found the example of selectInput shown on [Shiny Reference](http://shiny.rstudio.com/reference/shiny/latest/selectInput.html){:target="_blank"} is not helpful once we have a list of items like [this](/gytcrt.github.io/public/files/countries.txt){:target="_blank"}.

Are we gonna list all the items one by one?

```r
selectInput("country", "Countries:",
            c("Afghanistan" = "AF",
              "Albania" = "AL",
              "Algeria" = "DZ"))
```
NO WAY:)

Here we'd better read the countries and their abbreviations as a data frame and pass them to selectInput choices as a list.

```r
# Read the countries and their abbreviation as data frame
countries.list <- read.table("countries.txt", header = FALSE, sep = "|",
                             stringsAsFactors = FALSE, quote = "",
                             col.names = c("abbr", "country"))
# Make the data frame as a list
choice.country <- as.list(countries.list$abbr)
names(choice.country) <- countries.list$country

# Pass the list to selectInput choices
selectInput("country", "Countries:",
            choices=choice.country)
```

It's more decent!
