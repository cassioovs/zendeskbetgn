# BET Games Network Oficial Theme ⚽

This repo contains the Front End theme for Zendesk Platform running on the Zendesk Guide Platform API.

The theme is based of the default [Zendesk Copenhagen theme](https://github.com/zendesk/copenhagen_theme) which is designed to be responsive and accessible.

## Project structure

1. [`templates/`](#templates) - contains all markup.
2. [`style.css`](#styles) - contains all CSS.
3. [`script.js`](#scripts) - main script file.
4. [`assets/`](#assets-folder) - assets such as scripts or fonts.
5. [`manifest.json`](#manifest-file) - project metadata and settings.
6. [`settings/`](#settings-folder) - files to be used in settings in [`manifest.json`](manifest.json).

Other files and folders can be added to the project but will (to my knowledge) be ignored when importing.

### Templates

- Article page ([`article_page.hbs`](templates/article_page.hbs))
- Category page ([`category_page.hbs`](templates/category_page.hbs))
- Community post list page ([`community_post_list_page.hbs`](templates/community_post_list_page.hbs))
- Community post page ([`community_post_page.hbs`](templates/community_post_page.hbs))
- Community topic list page ([`community_topic_list_page.hbs`](templates/community_topic_list_page.hbs))
- Community topic page ([`community_topic_page.hbs`](templates/community_topic_page.hbs))
- Contributions page ([`contributions_page.hbs`](templates/contributions_page.hbs))
- Document head ([`document_head.hbs`](templates/document_head.hbs))
- Error page ([`error_page.hbs`](templates/error_page.hbs))
- Footer ([`footer.hbs`](templates/footer.hbs))
- Header ([`header.hbs`](templates/header.hbs))
- Home page ([`home_page.hbs`](templates/home_page.hbs))
- New community post page ([`new_community_post_page.hbs`](templates/new_community_post_page.hbs))
- New request page ([`new_request_page.hbs`](templates/new_request_page.hbs))
- Requests page ([`request_page.hbs`](templates/request_page.hbs))
- Search results page ([`search_results.hbs`](templates/search_results.hbs))
- Section page ([`section_page.hbs`](templates/section_page.hbs))
- Subscriptions page ([`subscriptions_page.hbs`](templates/subscriptions_page.hbs))
- User profile page ([`user_profile_page.hbs`](templates/user_profile_page.hbs))

### Styles

The styles that Zendesk Guide will read are in the [`style.css`](style.css) file located in the project root.

For development this project uses the CSS preprocessor [Sass](https://sass-lang.com/) with the `.scss` syntax where we split styles into [Sass partials](https://sass-lang.com/guide#topic-4). All the partials are put under the [`styles/`](styles/) folder and included in the [`index.scss`](styles/index.scss) which is then compiled to [`style.css`](style.css).

`styles/_partial.scss` 🡆 `styles/index.scss` 🡆 `style.css`

### Scripts

The main JavaScript file [`script.js`](script.js) is located in the project root and will be added in the document `<body>` of every page.

JavaScript that you do not think belong on all pages can be added inline in [templates](#templates) or added as regular `*.js` files in the [assets folder](#assets-folder) and then be included in the appropriate template(s).

### Assets folder

You can add assets as images and files to the [`assets/`](assets/) folder and use them in your CSS and templates, for example:

```
# template
{{asset 'cat-image.jpg'}}

# css
$assets-cat-image-jpg
```

The assets will be uploaded to Zendesk CDN (`theme.zdassets.com`). You can read more about assets [here](https://support.zendesk.com/hc/en-us/articles/115012399428).

### Manifest file

The [`manifest.json`](manifest.json) contains theme metadata and allows you to define a group of settings for your theme that can then be changed via the UI in theming center.
You can read more about the manifest file [here](https://support.zendesk.com/hc/en-us/articles/115012547687).

### Settings folder

If you have a `type` variable of `file`, you need to provide a default file for that variable in the [`settings/`](settings/) folder. This file will be used on the settings panel by default and users can upload a different file if they like.
For Example, if you'd like to have a variable for the background image of a section, the variable in your manifest file would look something like this:

```json
{
  ...
  "settings": [{
    "label": "Images",
    "variables": [{
      "identifier": "background_image",
      "type": "file",
      "description": "Background image for X section",
      "label": "Background image",
    }]
  }]
}
```

And this would look for a file inside the [`settings/`](settings/) folder named `background_image`.

## Prerequisites

Have installed on your machine:

[Ruby](https://www.ruby-lang.org/pt/downloads/)

[NodeJS](https://nodejs.org/en/download/?utm_source=blog)

[Ubuntu LTS](https://ubuntu.com/download/desktop)

[Zendesk CLI](https://developer.zendesk.com/documentation/apps/getting-started/using-zcli/)

[ZAT](https://developer.zendesk.com/documentation/apps/zendesk-app-tools-zat/zat-commands/)

Once you have ZAT setup make sure [Node.js](https://nodejs.org/) is installed and then use the below commands:

```bash
# install dependencies
npm install

# start the development server
npm start
```

## Developing

You can use your favorite IDE to develop and preview your changes locally in a web browser using the Zendesk Apps Tools (ZAT) which is installed as a Ruby gem. For more details, see [Previewing theme changes locally](https://support.zendesk.com/hc/en-us/articles/115012793547).

To avoid having to enter your Zendesk credentials every time you start your development environment you can create a `.zat` file in the project root which contains your credentials in json format, for example like this:

```json
{
  "subdomain": "wolrdwidecup",
  "username": "john.doe@bet-gn.com/token",
  "password": "YOUR_API_TOKEN"
}
```
## Deploy 

1. Create repository in Github
2. Git Clone your repo in local host and virtual host 

```bash
# Git Clone Local Machine
git clone https://github.com/{youruser}/{yourrepo}.git

# Open CLI LTS Ubutu and Git CLone in this virtual machine
git clone https://github.com/{youruser}/{yourrepo}.git
```
3. Install

```bash
# install dependencies
npm install

# start the development server
npm start
```

![image](https://user-images.githubusercontent.com/74793499/224885853-08e2214a-3935-4c5c-bda2-defe752000e1.png)

4. Git Push in Local Host Repo
5. Git Pull in Virtual Host LTS

6. Preview using ZAT Theme Preview in LTS

```bash
# Using ZAT Theme Preview
zat theme preview
```
![image](https://user-images.githubusercontent.com/74793499/224886491-d1983c5f-4639-4fc7-9521-3521150c9a2c.png)

```bash
# Open the preview in your browser

https://{yourdomain}.zendesk.com/hc/admin/local_preview/start
```
7. Enjoy :)

![image](https://user-images.githubusercontent.com/74793499/224886699-e4c3ea56-60b2-4c8b-968d-d50e18015d74.png)

![image](https://user-images.githubusercontent.com/74793499/224887669-d7d7e55f-0847-43bb-bf07-1317aae8b532.png)

![image](https://user-images.githubusercontent.com/74793499/224888058-7ab03c22-78dc-4554-8022-31713692044d.png)


## Attention points

1. Release access to your zendesk user for use via the CLI API 🡆 [Enable access](https://developer.zendesk.com/documentation/apps/getting-started/using-zcli/)

![image](https://user-images.githubusercontent.com/74793499/224887245-680c1c76-522a-4a2f-a2ea-0077a83b67c0.png)

2. Under no circumstances develop the project before uploading it to Zendesk

Zendesk has its own plugin that reduces the size of deploys.

If you develop outside, Zendesk will reject all projects larger than 30mb.

The recommendation here is to upload a clean project and push for development.





