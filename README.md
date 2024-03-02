# Google Indexing Script

Use this script to get your entire site indexed on Google in less than 48 hours. No tricks, no hacks, just a simple script and a Google API.

You can read more about the motivation behind it and how it works in this blog post https://seogets.com/blog/google-indexing-script

> [!IMPORTANT]  
> 1. Indexing != Ranking. This will not help your content/page rank on Google, it'll just let Google know about the existence of all your pages.
> 2. This script uses [Google Indexing API](https://developers.google.com/search/apis/indexing-api/v3/quickstart). While there is no absolute guarantee that every page will be indexed, recent tests conducted in December 2023 have shown a notably high success rate.

## Requirements

- Install [Node.js](https://nodejs.org/en/download)
- An account on [Google Search Console](https://search.google.com/search-console/about) with the verified sites you want to index
- An account on [Google Cloud](https://console.cloud.google.com/)

## Preparation

1. Follow this [guide](https://developers.google.com/search/apis/indexing-api/v3/prereqs) from Google. By the end of it, you should have a project on Google Cloud with the Indexing API enabled, a service account with the `Owner` permission on your sites.
2. Make sure you enable both `Google Search Console API` and `Web Search Indexing API` on your [Google Project ➤ API Services ➤ Enabled API & Services](https://console.cloud.google.com/apis/dashboard).
3. [Download the JSON](https://github.com/goenning/google-indexing-script/issues/2) file with the credentials of your service account and save it in the same folder as the script. The file should be named `service_account.json`


## Installation

### Using CLI

Install the cli globally on your machine.

```bash
npm i -g google-indexing-script
```

#### With `service_account.json` *(recommended)*

Create a `.gis` directory in your home folder and move the `service_account.json` file there.

```bash
mkdir ~/.gis
mv service_account.json ~/.gis
```

Run the script with the domain or url you want to index.

```bash
gis seogets.com
# or (long version)
google-indexing-script seogets.com
```

#### With environment variables

Open `service_account.json` and copy the `client_email` and `private_key` values.

Set the environment variables `GOOGLE_CLIENT_EMAIL` and `GOOGLE_PRIVATE_KEY` with the values you copied.

```bash
export GOOGLE_CLIENT_EMAIL="your-client-email"
export GOOGLE_PRIVATE_KEY="your-private-key"
```

Run the script with the domain or url you want to index.

```bash
gis seogets.com
```

#### With arguments *(not recommended)*

Open `service_account.json` and copy the `client_email` and `private_key` values.

Once you have the values, run the script with the domain or url you want to index, the client email and the private key.

```bash
gis seogets.com your-client-email your-private-key
```

### Using the repository

Clone the repository to your machine.

```bash
git clone https://github.com/goenning/google-indexing-script.git
cd google-indexing-script
```

Copy the `service_account.json` file to the repository folder.

```bash
mv /path/to/service_account.json .
```

Install the dependencies.

```bash
npm install
```

Run the script with the domain or url you want to index.

```bash
npm run index seogets.com
```

## Usage

1. Open a terminal and navigate to the folder where you cloned the repository
2. Ensure you are using an up-to-date Node.js version, with a preference for v20 or later. Check your current version with `node -v`.
3. Run `npm install` to install the dependencies
4. Run `npm run index <domain or url>` to index all the pages of your site.
- If your site is a `Domain` Property on GSC, then run it like `npm run index seogets.com`
- Otherwise, if it's a `URL Prefix` property, then run it like `npm run index https://seogets.com`
- When in doubt try both 😀

Here's an example of what you should expect:

![](./output.png)

**Important Notes:**

- Your site must have 1 or more sitemaps submitted to Google Search Console. Otherwise, the script will not be able to find the pages to index.
- You can run the script as many times as you want. It will only index the pages that are not already indexed.
- Sites with a large number of pages might take a while to index, be patient.

## 📄 License

MIT License

## 💖 Sponsor

This project is sponsored by [SEO Gets](https://seogets.com)

![](https://seogets.com/og.png)
