# Intrepid

A personal price tracker that watches products across e-commerce sites and sends notifications when prices are captured.

## Language

**Tracked Product**:
A product on a specific e-commerce site that the user has registered to watch for price changes.
_Avoid_: ScrapeTarget, Target

**Price Snapshot**:
An immutable record of a Tracked Product's title and price captured at a specific point in time.
_Avoid_: ScrapedData, ScrapeData

**Product ID**:
The site-specific identifier used to locate a product. Format varies by site: an ASIN for Amazon, a product name for Amazon via Google Shopping, a URL slug for Go Outdoors.
_Avoid_: SKU

**Price Check**:
A single run of the scraper against one Tracked Product. A successful Price Check produces a Price Snapshot.
_Avoid_: Scrape, Scraping run

**Notification**:
A Pushover message sent after a successful Price Check when the Tracked Product has notifications enabled. Fires on every successful check — not conditional on a price change or threshold.
_Avoid_: Alert

**Source**:
The identifier for which website and scraping strategy to use for a Tracked Product. One of `amz` (Amazon direct), `amz-g` (Amazon via Google Shopping), or `go_od` (Go Outdoors).
_Avoid_: Site

## Example dialogue

> "I added a new Tracked Product for the tent on Go Outdoors — Source is `go_od`, Product ID is `family-tent-123456`."
> "When will the first Price Check run?"
> "Next time the scraper runs. It'll produce a Price Snapshot and send a Notification if I've got that enabled."
> "And if the scraper can't find the price?"
> "No Snapshot is saved and no Notification is sent. It logs a warning and saves the raw HTML for debugging."
