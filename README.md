[https://apify.com/epctex/goodreads-scraper](https://apify.com/epctex/goodreads-scraper?fpr=yhdrb)

# Actor - Goodreads Scraper

## Goodreads scraper

Since Goodreads doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Goodreads data scraper supports the following features:

-   Search any keyword - You can search any keyword you would like to have and get the results

-   Scrape lists - Scrape any list that you'd like to get from Goodreads

-   Scrape shelf - You can check the shelves and scrape the information of the newest updates.

-   Scrape genres - If you want to get the most read books on a certain category or anything related to the genres, just type the URL.

-   Scrape book detail - Scrape very detailed information for each of the books that you'd like to get.

-   Scrape reviews of a book - Scrape all of the reviews from a book optionally.

## Bugs, fixes, updates, and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/goodreads-scraper/issues).

## Setup & Usage

You can see how this actor works in these videos:

### Using Search

[![Apify - Goodreads Scraper - Using Search](https://img.youtube.com/vi/7rpRBlIE--o/0.jpg)](https://www.youtube.com/watch?v=7rpRBlIE--o)

You can check the output of this example [here](https://api.apify.com/v2/datasets/AVTdGvcS2iOjDgAaV/items?clean=true&format=json).

### Using Start URLs

[![Apify - Goodreads Scraper - Using Start URLs](https://img.youtube.com/vi/ProePJ_1pwA/0.jpg)](https://www.youtube.com/watch?v=ProePJ_1pwA)

You can check the output of this example [here](https://api.apify.com/v2/datasets/yiZ9wm15WMTdmdH8L/items?clean=true&format=json).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Goodreads that should be visited. Possible fields are:

- `search`: (Optional) (String) Keyword that you want to search on Goodreads.

- `startUrls`: (Optional) (Array) List of Goodreads URLs. You should only provide a news list, jobs list, or detailed URLs.

- `includeReviews`: (Optional) (Boolean) This will add all the reviews that Goodreads provides inside the book object. Please keep in mind that the time and resources the actor uses will increase proportionally by the number of reviews.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. Default is `Infinite`. This applies to all `search` requests and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as an argument and returns an object with data.

- `customMapFunction`: (Optional) (String) Function that takes each object's handle as an argument and returns the object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to scrape over a specific listing URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that is explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor is optimized to run blazing fast and scrape many listings as possible. Therefore, it forefronts all listing detail requests. If the actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.03-0.05 compute units.

### Goodreads Scraper Input example

```json
{
    "startUrls": [
        "https://www.goodreads.com/search?utf8=%E2%9C%93&query=stephen",
        "https://www.goodreads.com/book/show/41865.Twilight",
        "https://www.goodreads.com/list/show/99918.Cassie_s_Cover_of_the_Year_2016",
        "https://www.goodreads.com/shelf/show/art",
        "https://www.goodreads.com/genres/most_read/christian-fiction",
        "https://www.goodreads.com/author/list/1221698.Neil_Gaiman"
    ],
    "includeReviews": false,
    "proxy": {
        "useApifyProxy": true
    },
    "endPage": 5,
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
  "bookId": 58408830,
  "url": "https://www.goodreads.com/book/show/58408830-the-lazarus-men",
  "image": "https://images-na.ssl-images-amazon.com/images/S/compressed.photo.goodreads.com/books/1624462365i/58408830.jpg",
  "title": "The Lazarus Men by Christian Warren Freed | GoodreadsLoading interface...Loading interface...",
  "authorName": "Christian Warren Freed",
  "authorUrl": "https://www.goodreads.com/author/show/8137590.Christian_Warren_Freed",
  "authorAbout": "<br />Christian W. Freed was born in Buffalo, N.Y. more years ago than he would like to remember. After spending more than 20 years in the active-duty US Army he has turned his talents to writing. Since retiring, he has gone on to publish over 25 military fantasy and science fiction novels, as well as his memoirs from his time in Iraq and Afghanistan, a children's book, and a pair of how to books focused on indie authors and the decision making process for writing a book and what happens after it is published. <br /><br />His first published book (Hammers in the Wind) has been the #1 free book on Kindle 4 times and he holds a fancy certificate from the L Ron Hubbard Writers of the Future Contest. Ok, so it was for 4th place in one quarter, but it's still recognition from the largest fiction writing contest in the world. And no, he's not a scientologist. <br /><br />Passionate about history, he combines his knowledge of the past with modern military tactics to create an engaging, quasi-realistic world for the readers. He graduated from Campbell University with a degree in history and a Masters of Arts degree in Digital Communications from the University of North Carolina at Chapel Hill. <br /><br />He currently lives outside of Raleigh, N.C. and devotes his time to writing, his family, and their two Bernese Mountain Dogs. If you drive by you might just find him on the porch with a cigar in one hand and a pen in the other. You can find out more about his work by following him on social media: <br />Facebook: <a target=\"_blank\" rel=\"noopener nofollow\" href=\"https://www.facebook.com/ChristianFreed\">https://www.facebook.com/ChristianFreed</a> <br />Twitter:<br /> @ChristianWFreed <br />Instagram: <a target=\"_blank\" rel=\"noopener nofollow\" href=\"http://www.instagram.com/christianwarrenfreed/\">www.instagram.com/christianwarrenfreed/</a> <br /><br />Website: <a target=\"_blank\" rel=\"noopener nofollow\" href=\"https://christianwfreed.com/\">https://christianwfreed.com/</a> <br /><br />Join his mailing list for new releases, updates, and upcoming events: <a target=\"_blank\" rel=\"noopener nofollow\" href=\"http://subscribepage.com/warfighterbooks\">http://subscribepage.com/warfighterbooks</a><br /><br /><br />Books by Christian Warren Freed<br /><br />The Forgotten Gods Tales<br />#1 Dreams of Winter<br />#2 The Madman on the Rocks<br />#3 Anguish Once Possessed<br />#4 Through Darkness Besieged<br />#5 Under Tattered Banners<br />#6 A Time For Tyrants<br />An Hour of Wolves- short story<br /><br />The Northern Crusade<br />#1 Hammers in the Wind<br />#2 Tides of Blood and Steel<br />#3 A Whisper After Midnight<br />#4 Empire of Bones<br />#5 The Madness of Gods and Kings<br />#6 Evens Gods Must Fall<br /><br />The Histories of Malweir (all stand alones)<br />#1 Armies of the Silver Mage<br />#2 The Dragon Hunters<br />#3 Beyond the Edge of Dawn<br /><br />Immortality Shattered<br />#1 Law of the Heretic<br />#2 The Bitter War of Always<br />#3 The Land of Wicked Shadows<br /># Storm Upon the Dawn<br /><br />The Children of Never (stand alone)<br />Where Have all the Elves Gone? (stand alone)<br />One of Our Elves is Missing<br />The Lazarus Men (stand alone)<br />Repercussions: A Lazarus Men Agenda #2<br />A Long Way From Home: My Time in Iraq and Afghanistan 2002-2006<br />Coward's Truth: A Novel of the Heart Eternal<br />Tomorrow's Demise: The Extinction Campaign<br />Tomorrow's Demise: Salvation<br />",
  "rating": 4.23,
  "numberOfRatings": 919,
  "numberOfReviews": 35,
  "reviews": [
    {
      "author": "Stjepan Cobets",
      "userUrl": "https://www.goodreads.com/user/show/44823204-stjepan-cobets",
      "rating": 4,
      "html": "My rating 3.6<br><br>Book The Lazarus Men by Christian Warren Freed is a solid sci-fi novel set in the future where Humankind has reached the stars. In the book, the author draws us into a world full of conspiracy in which those who have everything they want even more because human greed for power is sometimes too great. In this whirlwind of events, accidentally finds Gerald LaPlante ordinary man who is a worker at the landing station on Earth. He is witness to the murder that has happened and after that, he has to save his life. As he will later learn about these events, many secret organizations are involved and they all want him dead because he has something they are looking for. The story varies from excellent to good, and sometimes stories, where should expand, is too little developed, but all in all a good story. I am convinced that all fans of sci-fi will be satisfied.",
      "text": "My rating 3.6Book The Lazarus Men by Christian Warren Freed is a solid sci-fi novel set in the future where Humankind has reached the stars. In the book, the author draws us into a world full of conspiracy in which those who have everything they want even more because human greed for power is sometimes too great. In this whirlwind of events, accidentally finds Gerald LaPlante ordinary man who is a worker at the landing station on Earth. He is witness to the murder that has happened and after that, he has to save his life. As he will later learn about these events, many secret organizations are involved and they all want him dead because he has something they are looking for. The story varies from excellent to good, and sometimes stories, where should expand, is too little developed, but all in all a good story. I am convinced that all fans of sci-fi will be satisfied.",
      "numOfLikes": 40,
      "date": "July 20, 2018",
      "shelves": [
        "indie",
        "science-fiction"
      ]
    },
  ],
  "description": "It is the 23rd century. Humankind has reached the stars, building a tentative empire across a score of worlds. Earth's central government rules weakly as several worlds continue their efforts toward independence. Shadow organizations hide in the midst of the political infighting. Their manifestations of power and influence are beholden only to the highest bidder. The most powerful/insidious/secret of these, The Lazarus Men, has existed for decades, always working outside of morality's constraints. Led by the enigmatic Mr. Shine, their agents are hand selected from the worst humanity has to offer and available for the right price. Gerald LaPlant lives an ordinary life on Old Earth. That life is thrown into turmoil on the night he stumbles upon the murder of what appears to be a street thief. Fleeing into the night, Gerald finds himself caught in a war between the Lazarus Men and Roland McMasters, an extremely powerful man dissatisfied with the current regime and with designs on ruling his own empire.",
  "buyLinks": [
    "https://www.amazon.com/gp/product/B09L2CPT2L/ref=x_gr_bb_kindle?caller=Goodreads&tag=x_gr_bb_kindle-20",
    "http://www.amazon.com/gp/product/1365417077/ref=x_gr_bb_amazon?ie=UTF8&tag=x_gr_bb_amazon-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=1365417077&SubscriptionId=1MGPYB6YW3HWK55XCGG2",
    "https://www.amazon.com/s?k=The+Lazarus+Men&i=audible&ref=x_gr_w_bb_audible-20&tag=x_gr_w_bb_audible-20",
    "https://www.barnesandnoble.com/w/?ean=9781365417078",
    "http://affiliates.abebooks.com/c/64613/77416/2029?u=http%3A%2F%2Fwww.abebooks.com%2Fservlet%2FSearchResults%3Fisbn%3D1365417077",
    "https://click.linksynergy.com/fs-bin/click?id=GwEz7vxblVU&subid=&offerid=361251.1&type=10&tmpid=9309&u1=x_gr_w_bb&RD_PARM1=https%3A%2F%2Fwww.kobo.com%2Fus%2Fen%2Fsearch%3FQuery%3D9781365417078",
    "https://geo.itunes.apple.com/us/book/isbn9781365417078?at=11lvdC&mt=11&ls=1",
    "https://play.google.com/store/search?q=9781365417078&c=books&PCamrefID=bookpage&PAffiliateID=10lHMS",
    "http://www.bookdepository.com/search?searchTerm=1365417077&search=Find+book&a_aid=goodreads",
    "http://click.linksynergy.com/fs-bin/click?id=GwEz7vxblVU&subid=&offerid=189673.1&type=10&tmpid=939&&u1=x_gr_w_bb&RD_PARM1=http%3A%2F%2Fwww.alibris.com%2Fbooksearch%3Fkeyword%3D1365417077",
    "https://www.chapters.indigo.ca/en-ca/home/search/?keywords=9781365417078",
    "http://www.tkqlhce.com/ob117vpyvpxCFFFKMHLCEDHLGHKECEFMIGDFFHJDDD?url=http%3A%2F%2Fwww.betterworldbooks.com%2FThe+Lazarus+Men-H0.aspx%3FSearchTerm%3D1365417077",
    "https://www.indiebound.org/book/9781365417078",
    "https://prf.hn/click/camref:1101ljNE7/pubref:1365417077/destination:https://www.thriftbooks.com/browse/?b.search=1365417077"
  ],
  "bookFormat": "Paperback",
  "numberOfPages": 242,
  "firstPublishedDate": "January 1, 1970",
  "publishedDate": "June 1, 2021",
  "publishedBy": "Warfighter Books",
  "Original Title": null,
  "ISBN": "1365417077",
  "Edition Language": null,
  "Series": null,
  "Characters": [],
  "Literary Awards": []
}
```

## Contact
Please visit us through [epctex.com](https://epctex.com) to see all the products that are available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
