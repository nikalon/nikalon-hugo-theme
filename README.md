# Nikalon Hugo Theme
Lightweight and responsive theme designed for blogs. It uses minimal resources to make load times faster for slower connections.

## Table of contents
* [Requirements](#requirements)
* [Setting up](#setting-up)
* [Create posts](#create-posts)
* [Post variables](#post-variables)
* [Customization](#customization)
* [Translations](#translations)

## Requirements
This theme was designed against **Hugo v0.49.2 extended**. Your installation of Hugo requires support for Saas/SCSS pipelines. Please follow the instructions for your platform [here](https://gohugo.io/getting-started/installing/).

## Setting up
To apply this theme to your Hugo website follow this instructions. Clone or get a fresh copy of this repository.

```
git clone https://github.com/nikalon/nikalon-hugo-theme
```

Now copy the root directory named **nikalon-hugo-theme** and paste it into the **themes** directory from your Hugo website project.

We're almost done! Now we need to set some things up. Open **config.toml** from your website project and set the **theme** variable to **nikalon-hugo-theme** like the following example:

```
theme = "nikalon-hugo-theme"
```

### [OPTIONAL] Enable syntax highlighting
You can skip this part if you don't need to display code blocks into your website. Set the following variables into **config.toml** to enable code highlighting:
```
pygmentsCodefences = true
pygmentsUseClasses = true
pygmentsOptions = "linenos=table"
```

And now you're done! Enjoy this theme. If you run into any issue report it to the [project's home page](https://github.com/nikalon/nikalon-hugo-theme/issues).

## Create posts
This theme expects your posts to be located in `content/post`. An example of a post you can create is `content/post/my-new-post.md`

Whenever you want to create a new post you can issue the command `hugo new post/new-post.md` where *new-post.md* can be the name you want. Your post will be located in `content/post/new-post.md` and you can start writing it.

## Post variables
By default this theme will generate a web page with a title and text content for every single post you create. You can alter the way the posts are shown by setting a few variables in the [front matter](https://gohugo.io/content-management/front-matter).

* ### Article picture
A picture is worth a thousand words. You can set an image to be displayed in the list of articles and the article itself.

Define a **cover** parameter in the front matter of your article. The value has to be a relative URL to the picture.

For example, say you have a picture stored in `static/img/super-duper-picture.png` that you want to use. In your front matter you can set it this way:

```
cover: "img/super-duper-picture.png"
```

* ### Author
By default every post will show **Anonymous** as the author of the post unless you configure it in your front matter.

Set an **author** parameter and set it to the name of the author.

For example, if you want to make **Foo Bass** as the author of the article you can set it this way:

```
author: "Foo Bass"
```

**Recommendation:** If you want to fill in the author automatically every time you create a new post add the following parameter in `config.toml`

```
[params]
  author = "Foo Bass"
```

The next time you issue the command `hugo new post/new-post.md` the author will be filled for you.

* ### Tags
Tags are a way to group different articles based on the same topic.

To add tags to your article add the following parameter in the front matter:

```
tags: ["technology", "arts", "music"]
```

## Customization
There are some sections of the page that you can customize to your own needs by replacing HTML blocks or setting some extra variables in `config.toml`

* ### Copyright
You can customize the copyright notice however you want. Create `layouts/partials/copyright.html` and put whatever you want.

You can put a custom [Creative Commons](https://creativecommons.org/choose/) copyright by copying and pasting the generated HTML there.

* ### Footer links
Modify `config.toml` to add the following variable:

```
[params]
  footerLinks = ["about", "contact", "post"]
```

You can add as many pages in **footerLinks** as you want. But keep in mind that this theme expects that you have those pages created.

In the example above it's expected to have the following pages created or otherwise the links will not be created:

```
content/about/_index.md
content/contact/_index.md
content/post/_index.md
```
## Translations
Currently only english and spanish languages are officially supported. However, it doesn't stop you from using this theme for your native tongue. If you need it you can add support for a new language or override the current text lines that are bundled with this theme.

The next steps summarize how to add support for a new language or override an existing one:

### 1. Create localization file
In the root of your project create a directory named `i18n`. Inside that folder create a file named as the acronym for your language (`en.toml` for english, `it.toml` for italian, etc).

### 2. Copy strings
Now open the file `themes/nikalon-theme/i18n/en.toml`, copy all the contents and paste into the file that you created previously.

### 3. Translate!
You're going to see the following structure:

```
[AllTags]
other = "All tags"

[Tags]
other = "Tags"
```

What you have to change is the value of `other`. For example, if you want to translate the string **"All tags"** into french you have to write something like:

```
[AllTags]
other = "Toutes les étiquettes"
```

### **[Optional]** Translate / Override months

As of Hugo v0.51 there's still no support for localized dates. It means that the months are not translated automatically. If you want to display dates with the name of the months you'll have to translate it.

Create the directory `data/i18n`. Next copy the file `themes/nikalon-theme/data/i18n/months.json` and paste into the directory that you've just created. When you open the file you're going to see the following structure:

```
{
    "es": {
        "1": "Enero",
        "2": "Febrero",
        "3": "Marzo",
        ...
    }
}
```

You can override the months for spanish or create the translations for a new language. To do the latter add an object named as the file that you created in step 1. 

For example, if you want to add the translation for italian the structure should be this:

```
{
    "es": {
        "1": "Enero",
        "2": "Febrero",
        "3": "Marzo",
        ...
    },
    "it": {
        "1": "Gennaio",
        "2": "Febbraio",
        "3": "Marzo",
        ...
    }
}
```
Make sure to access the months that you've just created in the file that you created in step 1. In `PublishDate` you have yo add this syntax to translate the months into your language:

```
{{ index $.Site.Data.i18n.months.es (printf \"%d\" .PublishDate.Month) }}
```

Take a look into `themes/nikalon-theme/i18n/es.toml` as reference.
