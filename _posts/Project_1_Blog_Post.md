## Welcome to the blog!


If you've ever searched for an Airbnb to stay at on that big vacation or exciting business trip, you'll probably have found that prices can sometimes seem a bit...random.
How come two appartments that look the same in the same neighbourhood can have a price difference of $40 per night? Or have you ever felt you're paying extra to be a few blocks closer to downtown?
Have ypu ever wondered where these prices are actually coming from?

We recently got our hands on several data sets for properties and stays in Airbnbs in both Boston and Seattle. The data goes back to SOME TIME, and give us lots of detail about the properties and what guests said abot them.

IN this post we're going to look at a few questions:

1) Is there a difference in price between rainy Seattle and Boston, the home of MIT?
2) What are people saying about their stays in Boston and Seattle
3) When it comes to price, is it really all about location, location, location? Are downtown properties that much more expensive than those further out.
4) What are the most important factors in deciding the price per night of an Airbnb? How well can we predict the price from the data we have on a place?

MIGHT NEED TO REPHRASE THESE QUESTIONS

To answer our first question, let's look at average prices per night for stays in Seattle and Boston. While an average night in Seattle costs $127, a stay in Boston will cost $173 on average.

How can we explain this difference? To start off, we can compare the reviews that guests have left about their stays. To do this we took data on just over 151,000 reviews left on
properties in Seattle and Boston. We can see that the most common words used for stays in each city were:

TABLE

The top four words are almost the same for both cities! Guests in Boston are more likely to refer directly to the apartment itself in their review and are more likely to mention the location. 
Meanwhile guests at Seattle properties mentioned cleanliness and the host more often. 

While the list of most common words tells us what guests were talking about, it doesn't tell us what they were saying. To be a bit more information we can look at the most common collections of words.

TABLE

What does this tell us? Well, while the order of the phrases is different for each city, the phrases in question are the same!
So while properties in Seattle might be more likely to be within walking distance of attractions, it looks like the actual experience of staying at an Airbnb in either city is quite similar.

If that's the case then maybe answering the second two questions can shed some more light on the price difference.

Q2 HERE
To get a better idea of the factor affecting the price of Airbnb stays we're goimg to look at data on NUMBER of listings put up on Airbnb during DATE.
This data tells us a lot of detail about the properties, their amenities, the host and the area. With this we will run a model that will predict the price and use this to give us an idea of how much each factpor affects the price per night of Airbnb stays.
One of the factors we've included in this model is a variable that just tells us if the property is in Boston or Seattle. This will tell us if there's a 'Boston effect' when other variables are held constant.

So what do the results tell us? BY and large the results are not surprising; bigger properties, where the guest gets the whole place to themselves, with lots of amenities and the host is a superhost can be predicted to be more expensive than other properties.
Most interestingly for us is the finding that even with other factors accounted for, there is a difference between price in the two cities. This means that the exact same property would attract $40 per night more in Boton than it would in Seattle.


So maybe the difference in price has somwthing to do with the cities themselves. To explore this a bit, let's look at how prices differer across the two cities.
Below are two figures showing the price bands and locations of listings in Seattle, and then Boston.

FIGURES

Firstly, let's consider the map of Seattle. In the centre of the map we have an empty space showing Lake Union and in the bottom left we have a separate cluster of properties that are in or around the North Admiral area.
What stands out from this map? If we look at the district around Lake Union - especially those to the south - there appears to be a lot of properties in the $150 to $250 price range.
However, there doesn't appear to be much of a pattern beyond this. These central districts still have plenty of properties that are prices either higher or lower than the $150-$250 range. Furthermore, if we look further outwards
properties further from the centre don't appear to show much of a pattern, with properties on the edge of town being just as likely to be in the highest of lowest price bands (an exception to this is the in the bottom right of the map 
around the North Beacon Hill area, where properties tend to be in the lower price bands).

![Boston Map](/LDurham89.github.io/docs/assets/Boston_Map.png)

The map of Boston shows that the vast majority of listings are south of the Charles River, with a few properties showing up in the Cambridge district.
Unlike in Seattle we can see a really tight cluster of properties costing over $250 dollars per night. This cluster seems to centre on Back Bay and spills into surrounding areas. 
We can then see that as we move away from this area, more properties in the cheaper price bands show up and we see fewer of the most expensive properties.
How do we makle sense of this? Back Bay appears to be a vibrant area in itself but also inbetween other centres. For example, in Back Bay Airbnb guests can easily reach
Cambridge (home of M.I.T) in the north, the Downtown and Financial District to the East and the universities to the West.

Put together these suggest that Boston city centre commands a higher premium than the Seattle centre, with a central cluster in Boston that is tighter and with more expensive properties t
