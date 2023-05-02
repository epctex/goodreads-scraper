# Actor - Google Play Scraper

## Google Play scraper

Since Google Play doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Google Play data scraper supports the following features:

-   Get all the reviews instantly - You can search any keyword you would like to have and get the results

-   Any language, any region - Scrape any list that you'd like to get from Google Play

-   Search any keyword - You can search any keyword you would like to have and get the results

-   Get all apps from any developer - You can check the shelves and scrape the information of the newest updates.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/google-play-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Google Play that should be visited. Possible fields are:

- `startUrls`: (Optional) (Array) List of Google Play URLs. You should only provide search, developer page, or  application page URLs.

- `includeReviews`: (Optional) (Boolean) This will add all the reviews that Google Play provides into the app objects. Please keep in mind that the time and resources the actor uses will increase proportionally by the number of reviews..

- `endReviewsPage`: (Optional) (Number) Final number of reviews page that you want to scrape. Default is `Infinite`. This only limits out the reviews pages.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

If you want to scrape reviews of an application which contains a lot, using `endReviewsPage` is strongly suggested. Even though the actor has the capability to scrape all of them, the total resource consumption will proportionally increase and might be too much.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detail requests. If actor doesn't block very often it'll scrape 100 apps in less than a minute with ~0.001-0.003 compute units.

### Google Play Scraper Input example

```json
{
  "startUrls":[
    "https://play.google.com/store/search?q=hello&c=apps&hl=tr&gl=US",
    "https://play.google.com/store/apps/developer?id=Mattel163+Limited",
    "https://play.google.com/store/apps/details?id=com.tinybuildgames.helloneighbor&hl=tr&gl=US"
  ],
  "includeReviews":true,
  "endReviewsPage":1,
  "proxy":{
    "useApifyProxy":true
  }
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Google Play Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Google Play actor.

## Scraped Google Play Properties

The structure of each app in Google Play looks like this:

### App Detail

```json
https://api.apify.com/v2/datasets/fQ8QnvDv3BkHQfHlk/items?clean=true&format=json
```
