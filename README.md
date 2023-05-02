# Actor - Newsweek Scraper

## Newsweek scraper

Since Newsweek doesn't provide a good and free API, this actor should help you to retrieve data from it.

The Newsweek data scraper supports the following features:

-   Retrieve information from any article - You can get title, description, publish or update dates, body of the article and many other things!

-   Scrape articles from topics - If you are looking for the articles of a topic, you are in the right place.

-   Get articles from categories - Immediately retrieve all the articles of any category. Blazing fast!

-   Retrieve all the articles of an author - Have a favorite author? You can get all the articles of the author.

-   Search for anything - You can search and retrieve all the articles in newsweek.

## Bugs, fixes, updates and changelog

This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/newsweek-scraper/issues).

## Input Parameters

The input of this scraper should be JSON containing the list of pages on Newsweek that should be visited. Possible fields are:

- `search`: (Optional) (String) Keyword that you want to search on Newsweek.

- `startUrls`: (Optional) (Array) List of Newsweek URLs. You should only provide topic, category, author, search or article detail URL.

- `endPage`: (Optional) (Number) Final number of page that you want to scrape. Default is `Infinite`. This is applies to all `search` request and `startUrls` individually.

- `maxItems`: (Optional) (Number) You can limit scraped items. This should be useful when you search through the big lists or search results.

- `proxy`: (Required) (Proxy Object) Proxy configuration.

- `extendOutputFunction`: (Optional) (String) Function that takes a JQuery handle ($) as argument and returns object with data.

- `customMapFunction`: (Optional) (String) Function that takes each objects handle as argument and returns object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Tip

When you want to have a scrape over a specific list URL, just copy and paste the link as one of the **startUrl**.

If you would like to scrape only the first page of a list then put the link for the page and have the `endPage` as 1.

With the last approach that explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the `endPage` parameter as 6 then you'll have the 5th and 6th pages only.

### Compute Unit Consumption

The actor optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detail requests. If actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.01-0.09 compute units.

### Newsweek Scraper Input example

```json
{
  "startUrls":[
    "https://www.newsweek.com/ron-desantis-abortion-six-week-bill-2024-1794367",
    "https://www.newsweek.com/topic/climate-change",
    "https://www.newsweek.com/authors/jon-jackson",
    "https://www.newsweek.com/search/site/?q=biden",
    "https://www.newsweek.com/education"
  ],
  "maxItems":10,
  "endPage":1,
  "search":"donald trump",
  "proxy":{
    "useApifyProxy":true
  }
}
```

## During the Run

During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified.
When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with failure state and output an explanation of what is wrong.

## Newsweek Export

During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any languague (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Newsweek actor.

## Scraped Newsweek Properties

The structure of each item in Newsweek looks like this:

### Article Detail

```json
{
	"type": "article",
	"url": "https://www.newsweek.com/ron-desantis-abortion-six-week-bill-2024-1794367",
	"category": "U.S.",
	"title": "Ron DeSantis Abortion Law Might Be Fatal Error for His Presidential Chances",
	"author": "Ewan Palmer",
	"authorTitle": "",
	"publishedDate": "2023-04-14T08:04:05-04:00",
	"updatedDate": "2023-04-14T14:04:27-04:00",
	"description": "Polls have frequently suggested voters do not support strict abortion bans as the Florida governor and potential 2024 hopeful signs six-week ban.",
	"body": "Florida Governor Ron DeSantis may have severely damaged his White House ambitions even before his campaign is officially launched after he signed a bill that would ban most abortions after six weeks.DeSantis, who has yet to announce he is running for president in 2024 but is strongly rumored to do so soon, signed the Heartbeat Protection Act [SB 300] late on Thursday night. It prohibits abortions once a heartbeat is detected, something that can occur after six weeks.The move to ban abortions could be seen as a risky move for DeSantis as he attempts to drum up support across the country to mount a presidential campaign.With recent polls showing former President Donald Trump extending his lead over DeSantis in a potential contest for the 2024 Republican presidential nomination, DeSantis may calculate that taking a strong anti-abortion stance will help him with the conservative wing of the party.However, that position may work against him in a general election given that polls have consistently suggested that the general public does not support strict abortions bans. In March, a University of North Florida poll of Florida voters found 75 percent of respondents either \"somewhat\" or \"strongly opposed\" a six-week ban, including 61 percent of Republican voters.\"DeSantis needs to win the Republican nomination first, before even thinking about how his six-week 'heartbeat bill' might play in the 2024 general,\" Thomas Gift, an associate professor who heads the Center on U.S. Politics at University College London, told Newsweek.\"Given the lead that Trump's amassed, proving his conservative credentials on abortion may [be] a de facto requirement to stay competitive.\"But regardless of who's coronated the Republican contender for the White House, abortion will be on the ballot again next year, and it's hard to see it not benefiting Democrats up and down the ballot.\"A Pew Research Center poll, conducted in March last year, found that 61 percent of U.S. adults believed abortion should be legal in all or most cases, while 37 percent thought abortion should be illegal in all or most cases. Other polls have found that, while abortion rights resonate strongly for Democrats, Republicans remain sharply focused on inflation, and the economy is a top issue for most voters.DeSantis signed the bill restricting abortion after the Republican supermajorities in the Florida House and Senate voted to approve SB 300.\"We are proud to support life and family in the state of Florida,\" DeSantis said in a statement while releasing a photo of him signing the bill at his desk. \"I applaud the Legislature for passing the Heartbeat Protection Act that expands pro-life protections and provides additional resources for young mothers and families.\"DeSantis, re-elected governor by a large margin last November, has spent the past few years putting himself at the center of the culture wars with his bills targeting LGBTQ+ and education policies, with abortion another topic he appears willing to show he also takes a hardline stance on.SB 300 is not an outright abortion ban and does contain some exceptions, including to save a woman's life. In the case of rape or incest, an abortion is permitted up to 15 weeks if the woman can provide documentation such as a restraining order or a police report.Democrats and abortion rights groups who condemn DeSantis for signing the six-week abortion bill note that the governor may be hindering his White House ambitions by introducing such a bill.White House Press Secretary Karine Jean-Pierre called the ban \"extreme and dangerous\" and said it \"flies in the face of fundamental freedoms and is out of step with the views of the vast majority of the people of Florida and of all the United States.\"Anna Eskamani, a Democratic member of the Florida House of Representatives, called DeSantis a \"coward\" for signing the bill late at night on Thursday.\"He just signed into law an extreme 6 week abortion ban at 10:45pm &amp; behind closed doors. He doesn't want you to know that he just banned abortion but we're going to do everything we can to make sure his extreme agenda doesn't make it to the White House,\" Eskamani tweeted.Mini Timmaraju, president of NARAL Pro-Choice America, said that DeSantis is \"stooping to new lows\" to try and win the 2024 GOP primary by signing the six-week abortion ban, which will ultimately harm him should he win the Republican presidential candidacy.\"He should have listened in November [midterms] when voters made it clear they don't support abortion bans&mdash;he can count on hearing it again when he's on the ballot next,\" Timmaraju said.The push to ban abortions after six weeks is in line with other Republican states that have taken steps to restrict the procedure after the Supreme Court voted to overturn Roe v. Wade last June. South Carolina also attempted to ban abortions after six weeks, but the decision was overruled by the Supreme Court in January.Whether SB 300 comes into effect is dependent on the legal challenges to a previous bill signed by the governor in April 2022 which prohibits abortion after 15 weeks, which is due to appear before the state Supreme Court.Despite the criticism, Mike Beltran, a Republican member of the Florida House of Representatives, suggested that the six-week abortion bill is a compromise for DeSantis.\"I favor an outright ban on abortion,\" Beltran told The New York Times. \"This is a compromise. For every person who thinks this goes too far, there are folks who feel that it doesn't go far enough.\"DeSantis' office has been contacted via email for further comment.",
	"keywords": [
		"Ron DeSantis",
		"Abortion",
		"Florida",
		"GOP",
		"2024 Election",
		"Donald Trump"
	],
	"images": [
		{
			"url": "https://d.newsweek.com/en/full/2222554/ron-desantis-abortion-law-error-campaign.jpg?w=1600&h=900&l=47&t=54&q=88&f=cc88012fa0f4224967f73dd05f39e39c",
			"caption": "Florida Gov. Ron DeSantis (R-FL) speaks at Hillsdale College on April 6, 2023 in Hillsdale, Michigan. DeSantis spoke earlier in the day at a GOP breakfast in Midland, Michigan"
		},
		{
			"url": "https://d.newsweek.com/en/full/2222554/ron-desantis-abortion-law-error-campaign.jpg?w=1600&h=1200&l=47&t=54&q=88&f=e92a4fe16c05dddf77646e1580622bcc",
			"caption": "Florida Gov. Ron DeSantis (R-FL) speaks at Hillsdale College on April 6, 2023 in Hillsdale, Michigan. DeSantis spoke earlier in the day at a GOP breakfast in Midland, Michigan"
		},
		{
			"url": "https://d.newsweek.com/en/full/2222554/ron-desantis-abortion-law-error-campaign.jpg?w=1600&h=1600&l=47&t=54&q=88&f=33f0632627b8870d6d91473b49377c86",
			"caption": "Florida Gov. Ron DeSantis (R-FL) speaks at Hillsdale College on April 6, 2023 in Hillsdale, Michigan. DeSantis spoke earlier in the day at a GOP breakfast in Midland, Michigan"
		}
	],
	"videos": [
		{
			"name": "Florida Gov. DeSantis Signs 6-Week Abortion Ban Into Law",
			"description": "Florida Governor Ron DeSantis has signed a 6-week abortion ban into law. The legislation will ban abortion at 6 weeks but will create exemptions for rape and incest up to 15 weeks of pregnancy. The Bill SB 300 dubbed the “Heartbeat Protection Act” passed in the GOP-led state House with a 70-40 vote. The law will make it a felony for doctors that “actively participate” in the procedure.",
			"url": "https://video.newsweek.com/transcoder/480p/2771/desantis-1681463391.m3u8"
		}
	],
	"topics": [
		"Ron DeSantis",
		"Abortion",
		"Florida",
		"GOP"
	],
	"html": "<div class=\"article-videoplayer hidden-print\"><div class=\"videocontent-wrapper\"><div class=\"videocontent\"><div id=\"close_fusion_jwplayer\" style=\"display:none\"></div><div class=\"tvplayer\" id=\"tvplayer\"></div></div></div></div> <script>doFir.push(function(){jQuery.extend(Drupal.settings, {\"fusion_jwplayer\":{\"preslate\":0,\"autostart\":true,\"autostart_embed\":0,\"title\":\"Florida Gov. DeSantis Signs 6-Week Abortion Ban Into Law\",\"init\":true,\"site\":\"Newsweek\",\"bg\":\"#FF0500\",\"unblocker\":\"\",\"unblocker_ad\":\"\",\"mediaid\":\"554217\",\"playlist\":\"https://d.newsweek.com/widget/play-list?nid=554217&items=3&v=11681488772\",\"mobileautoplay\":1,\"autoplay_viewable\":0,\"mobilesticky\":1,\"displaytitle\":0,\"debug\":0,\"vpaidmode\":\"insecure\",\"repeat\":0,\"allowAd\":true,\"stretching\":\"fill\",\"duration\":\"54\",\"vfile\":\"https://g.newsweek.com/sys/js/07bba1a9c30c8f01d28d980808d6b064.js?v=1681488772\",\"video_image\":\"https://d.newsweek.com/en/full/2222200/picture-video.jpg?w=400&h=225&q=50&f=3a11e058c2eddaefa9321cc562841e4a\",\"resolutionDefault\":\"480p\",\"resolutionDefaultM\":\"240p\"}});});</script> <script>doFir.push(function(){Drupal.behaviors.fusionJWPlayer.init()})</script> <div class=\"social-share flex-xs flex-wrap ai-c ar23-social-share\"><div class=\"block-title ar23-block-title\">Share</div>\n<a href=\"https://www.facebook.com/sharer/sharer.php?u=https://www.newsweek.com/ron-desantis-abortion-six-week-bill-2024-1794367\" class=\"genericon genericon-facebook-alt\" rel=\"noopener\" target=\"_blank\"><span class=\"element-invisible\">Share on Facebook</span></a>\n<a href=\"https://twitter.com/intent/tweet?text=Ron+DeSantis+abortion+law+might+be+fatal+error+for+his+presidential+chances+https://www.newsweek.com/ron-desantis-abortion-six-week-bill-2024-1794367\" class=\"genericon genericon-twitter\" rel=\"noopener\" target=\"_blank\"><span class=\"element-invisible\">Share on Twitter</span></a>\n<a href=\"https://www.linkedin.com/shareArticle?mini=true&amp;url=https%3A%2F%2Fwww.newsweek.com%2Fron-desantis-abortion-six-week-bill-2024-1794367&amp;title=Ron+DeSantis+abortion+law+might+be+fatal+error+for+his+presidential+chances\" class=\"genericon genericon-linkedin\" rel=\"noopener\" target=\"_blank\"><span class=\"element-invisible\">Share on LinkedIn</span></a><a href=\"http://reddit.com/submit?url=https://www.newsweek.com/ron-desantis-abortion-six-week-bill-2024-1794367&amp;title=Ron+DeSantis+abortion+law+might+be+fatal+error+for+his+presidential+chances\" class=\"genericon genericon-reddit\" rel=\"noopener\" target=\"_blank\"><span class=\"element-invisible\">Share on Reddit</span></a><a class=\"genericon genericon-flipboard\" data-flip-widget=\"shareflip\" href=\"https://flipboard.com\" rel=\"nofollow noopener\"><span class=\"element-invisible\">Share on Flipboard</span></a>"
}
```
