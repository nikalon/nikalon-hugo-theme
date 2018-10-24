# Nikalon Hugo Theme
Lightweight and responsive theme designed for blogs. It uses minimal resources to make load times faster for slower connections.

# Requirements
This theme was designed against **Hugo v0.49.2 extended**. Your installation of Hugo requires support for Saas/SCSS pipelines. Please follow the instructions for your platform [here](https://gohugo.io/getting-started/installing/).

# Create posts
This theme expects your posts to be located in `content/post`. An example of a post you can create is `content/post/my-new-post.md`

Whenever you want to create a new post you can issue the command `hugo new post/new-post.md` where *new-post.md* can be the name you want. Your post will be located in `content/post/new-post.md` and you can start writing it.

# Post variables
By default this theme will generate a webpage with a title and text content for every single post you create. You can alter the way the posts are shown by setting a few variables in the [front matter](https://gohugo.io/content-management/front-matter).

## Article picture
A picture is worth a thousand words. You can set an image to be displayed in the list of articles and the article itself.

Define a **cover** parameter in the front matter of your article. The value has to be a relative URL to the picture.

For example, say you have a picture stored in `static/img/super-duper-picture.png` that you want to use. In your front matter you can set it this way:

```
cover: "img/super-duper-picture.png"
```

## Author
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

## Tags
Tags are a way to group different articles based on the same topic.

To add tags to your article add the following parameter in the front matter:

```
tags: ["technology", "arts", "music"]
```

# Customization
There are some sections of the page that you can customize to your own needs by replacing HTML blocks or setting some extra variables in `config.toml`

## Copyright
You can customize the copyright notice however you want. Create `layouts/partials/copyright.html` and put whatever you want.

You can put a custom [Creative Commons](https://creativecommons.org/choose/) copyright by copying and pasting the generated HTML there.

## Footer links
Modify `config.toml` to add the following variable:

```
[params]
  footerLinks = ["about", "contact", "post"]
```

You can add as many pages in the **footerLinks** variables as you want. But keep in mind that this theme expects that you have those pages created.

In the example above it's expected to have the following pages created or otherwise the links will not be created:

```
content/about/_index.md
content/contact/_index.md
content/post/_index.md
```
