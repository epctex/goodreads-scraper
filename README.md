# Actor - Goodreads Scraper

## Goodreads scraper

Since Goodreads doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Goodreads data scraper supports the following features:

- Search any keyword - You can search any keyword you would like to have and get the results

- Scrape lists - Scrape any list that you'd like to get from Goodreads

- Scrape shelf - You can check the shelves and scrape the information of the newest updates.

- Scrape genres - If you want to get most read books on a certain category or anything related the genres, just type the url.

- Scrape book detail - Scrape a very detailed information for each of the book that you'd like to get.


## Bugs, fixes, updates and changelog
This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/tugkan/goodreads-scraper/issues).

### Incoming Changes
- Implement to get the reviews from each book.


## Input Parameters

The input of this scraper should be JSON containing the list of pages on Goodreads that should be visited. Required fields are:

| Field | Type | Description |
| ----- | ---- | ----------- |
| startUrls | Array | (optional) List of Goodreads URLs. You should only provide news list, jobs list or detail URLs |
| search | String | (optional) Keyword that you want to search on Goodreads. |
| endPage | Integer | (optional) Final number of page that you want to scrape. Default is `Infinite`. |
| maxItems | Integer | (optional) You can limit scraped products. This should be useful when you search through the big subcategories.|
| proxy | Object | Proxy configuration |
| extendOutputFunction | String | (optional) Function that takes a JQuery handle ($) as argument and returns object with data |
This solution requires the use of **Proxy servers**, either your own proxy servers or you can use <a href="https://www.apify.com/docs/proxy">Apify Proxy</a>.

##### Tip
When you want to have a scrape over a specific listing URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.


### Compute Unit Consumption
The actor optimized to run blazing fast and scrape many as listings as possible. Therefore, it forefronts all listing detail requests. If actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.03-0.05 compute units.

### Goodreads Scraper Input example
```json
{
  "startUrls":[
    "https://www.goodreads.com/search?utf8=%E2%9C%93&query=stephen",
    "https://www.goodreads.com/book/show/41865.Twilight",
    "https://www.goodreads.com/list/show/99918.Cassie_s_Cover_of_the_Year_2016",
    "https://www.goodreads.com/shelf/show/art",
    "https://www.goodreads.com/genres/most_read/christian-fiction"
  ],
  "proxy":{
    "useApifyProxy": true
  },
  "endPage":5,
  "maxItems": 100
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Goodreads Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Goodreads actor.

## Scraped Goodreads Properties
The structure of each item in Goodreads listings looks like this:

### Book Detail

```json
{
  "url": "https://www.goodreads.com/book/show/41865.Twilight",
  "image": "https://i.gr-assets.com/images/S/compressed.photo.goodreads.com/books/1361039443l/41865.jpg",
  "title": "Twilight",
  "authorName": "Stephenie Meyer",
  "authorUrl": "https://www.goodreads.com/author/show/941441.Stephenie_Meyer",
  "authorAbout": "Stephenie Meyer is the author of the bestselling Twilight series, The Host, and The Chemist. Twilight was one of 2005's most talked about novels and within weeks of its release the book debuted at #5 on The New York Times bestseller list. Among its many accolades, Twilight was named an \"ALA Top Ten Books for Young Adults,\" an Amazon.com \"Best Book of the Decade So Far,\" and a Publishers Weekly Bes\n  Stephenie Meyer is the author of the bestselling Twilight series, The Host, and The Chemist. Twilight was one of 2005's most talked about novels and within weeks of its release the book debuted at #5 on The New York Times bestseller list. Among its many accolades, Twilight was named an \"ALA Top Ten Books for Young Adults,\" an Amazon.com \"Best Book of the Decade So Far,\" and a Publishers Weekly Best Book of the Year. Meyer graduated from Brigham Young University with a degree in English Literature. She lives in Arizona with her husband and three sons.\n  ...more",
  "rating": 3.61,
  "numberOfRatings": 5186290,
  "numberOfReviews": 106938,
  "description": "About three things I was absolutely positive.First, Edward was a vampire.Second, there was a part of him—and I didn't know how dominant that part might be—that thirsted for my blood.And third, I was unconditionally and irrevocably in love with him.Deeply seductive and extraordinarily suspenseful, Twilight is a love story with bite.\n  About three things I was absolutely positive.First, Edward was a vampire.Second, there was a part of him—and I didn't know how dominant that part might be—that thirsted for my blood.And third, I was unconditionally and irrevocably in love with him.Deeply seductive and extraordinarily suspenseful, Twilight is a love story with bite.\n  ...more",
  "buyLinks": [
    "https://www.goodreads.com/buy_buttons/12/follow?book_id=41865&page_type=book&page_type_id=41865&ref=x_gr_w_bb_sout&sub_page_type=show&tag=x_gr_w_bb_sout-20",
    "https://www.goodreads.com/book_link/follow/10?book_id=41865&page_type=book&page_type_id=41865&ref=x_gr_w_bb_audible&source=dropdown&sub_page_type=show",
    "https://www.goodreads.com/book_link/follow/3?book_id=41865&page_type=book&page_type_id=41865&source=dropdown&sub_page_type=show",
    "https://www.goodreads.com/book_link/follow/1027?book_id=41865&page_type=book&page_type_id=41865&source=dropdown&sub_page_type=show",
    "https://www.goodreads.com/book_link/follow/2102?book_id=41865&page_type=book&page_type_id=41865&source=dropdown&sub_page_type=show",
    "https://www.goodreads.com/book_link/follow/8036?book_id=41865&page_type=book&page_type_id=41865&source=dropdown&sub_page_type=show",
    "https://www.goodreads.com/book_link/follow/4?book_id=41865&page_type=book&page_type_id=41865&source=dropdown&sub_page_type=show",
    "https://www.goodreads.com/book_link/follow/882?book_id=41865&page_type=book&page_type_id=41865&source=dropdown&sub_page_type=show",
    "https://www.goodreads.com/book_link/follow/5?book_id=41865&page_type=book&page_type_id=41865&source=dropdown&sub_page_type=show",
    "https://www.goodreads.com/book_link/follow/9?book_id=41865&page_type=book&page_type_id=41865&source=dropdown&sub_page_type=show",
    "https://www.goodreads.com/book_link/follow/107?book_id=41865&page_type=book&page_type_id=41865&source=dropdown&sub_page_type=show",
    "https://www.goodreads.com/book_link/follow/7?book_id=41865&page_type=book&page_type_id=41865&source=dropdown&sub_page_type=show"
  ],
  "bookFormat": "Paperback",
  "numberOfPages": 501,
  "Original Title": "Twilight",
  "ISBN": "0316015849",
  "Edition Language": "English",
  "Series": "The Twilight Saga #1",
  "Characters": "Edward Cullen, Jacob Black, Laurent, Renee, Bella Swan...more, Billy Black, Esme Cullen, Alice Cullen, Jasper Hale, Carlisle Cullen, Emmett Cullen, Rosalie Hale, Charlie Swan, Mike Newton, Jessica Stanley, Angela Weber, Tyler Crowley...less",
  "Literary Awards": "Georgia Peach Book Award (2007), Buxtehuder Bulle (2006), Kentucky Bluegrass Award for 9-12 (2007), Prijs van de Kinder- en Jeugdjury Vlaanderen (2008), Books I Loved Best Yearly (BILBY) Awards for Older Readers (2009)\n                      ...more\n                          West Australian Young Readers' Book Award (WAYRBA) for Older Readers (2008), Garden State Book Award for Fiction (Grades 9-12) (2008), South Carolina Book Award for Young Adult Book Award (2008), Grand Canyon Reader Award for Teen Book (2008), Maryland Black-Eyed Susan Book Award for High School (2008), Golden Sower Award for Young Adult (2009), Nevada Young Readers' Award for Young Adult Category  (2007), The Flume: New Hampshire Teen Reader's Choice Award (2007), Pennsylvania Young Readers' Choice Award for Young Adult (2009), Rhode Island Teen Book Award (2007), Evergreen Teen Book Award (2008), Michigan Library Association Thumbs Up! Award Nominee (2006), Teen Read Award Nominee for Best All-Time-Fave (2010), Deutscher Jugendliteraturpreis Nominee for Preis der Jugendjury (2007), Iowa High School Book Award (2008), Eliot Rosewater Indiana High School Book Award (2008), Lincoln Award (2008), Literaturpreis der Jury der jungen Leser for Cover (2007), Prix Et-lisez-moi (2008), Missouri Gateway Readers Award (2008)\n...less"
}
```
