---
title: Embedding Media In Html
template: post
subtitle: "From object to iframe "
excerpt: getting the hang of embedding things into your web pages
date: 2022-04-19T20:11:27.517Z
image: blob:https://enthusiastic-spinach-93724.stackbit.app/ce89ffeb-e9be-44e2-9ecc-c64c1027acae
thumb_image: blob:https://enthusiastic-spinach-93724.stackbit.app/ce89ffeb-e9be-44e2-9ecc-c64c1027acae
image_position: right
show_author_bio: false
cmseditable: true
---

<!--StartFragment-->

# From object to iframe

By now you should really be getting the hang of embedding things into your web pages, including images, video and audio. At this point we'd like to take somewhat of a sideways step, looking at some elements that allow you to embed a wide variety of content types into your webpages: the [`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe), [`<embed>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed) and [`<object>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object) elements. `<iframe>`s are for embedding other web pages, and the other two allow you to embed PDFs, SVG, and even Flash — a technology that is on the way out, but which you'll still see semi-regularly.

| Prerequisites: | Basic computer literacy, [basic software installed](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/Installing_basic_software), basic knowledge of [working with files](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/Dealing_with_files), familiarity with HTML fundamentals (as covered in [Getting started with HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started)) and the previous articles in this module. |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Objective:     | To learn how to embed items into web pages using [`<object>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object), [`<embed>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed), and [`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe), like PDF documents and other webpages.                                                                                                                                                                               |

## [A short history of embedding](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies#a_short_history_of_embedding "Permalink to A short history of embedding")

A long time ago on the Web, it was popular to use **frames** to create websites — small parts of a website stored in individual HTML pages. These were embedded in a master document called a **frameset**, which allowed you to specify the area on the screen that each frame filled, rather like sizing the columns and rows of a table. These were considered the height of coolness in the mid to late 90s, and there was evidence that having a webpage split up into smaller chunks like this was better for download speeds — especially noticeable with network connections being so slow back then. They did however have many problems, which far outweighed any positives as network speeds got faster, so you don't see them being used anymore.

A little while later (late 90s, early 2000s), plugin technologies became very popular, such as [Java Applets](https://developer.mozilla.org/en-US/docs/Glossary/Java) and [Flash](https://developer.mozilla.org/en-US/docs/Glossary/Adobe_Flash) — these allowed web developers to embed rich content into webpages such as videos and animations, which just weren't available through HTML alone. Embedding these technologies was achieved through elements like [`<object>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object), and the lesser-used [`<embed>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed), and they were very useful at the time. They have since fallen out of fashion due to many problems, including accessibility, security, file size, and more. These days major browsers have stopped supporting plugins such as Flash.

Finally, the [`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) element appeared (along with other ways of embedding content, such as [`<canvas>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/canvas), [`<video>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video), etc.) This provides a way to embed an entire web document inside another one, as if it were an [`<img>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img) or other such element, and is used regularly today.

With the history lesson out of the way, let's move on and see how to use some of these.

## [Active learning: classic embedding uses](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies#active_learning_classic_embedding_uses "Permalink to Active learning: classic embedding uses")

In this article we are going to jump straight into an active learning section, to immediately give you a real idea of just what embedding technologies are useful for. The online world is very familiar with [YouTube](https://www.youtube.com/), but many people don't know about some of the sharing facilities it has available. Let's look at how YouTube allows us to embed a video in any page we like using an [`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe).

1. First, go to YouTube and find a video you like.
2. Below the video, you'll find a *Share* button — select this to display the sharing options.
3. Select the *Embed* button and you'll be given some `<iframe>` code — copy this.
4. Insert it into the *Input* box below, and see what the result is in the *Output*.

For bonus points, you could also try embedding a [Google Map](https://www.google.com/maps/) in the example:

1. Go to Google Maps and find a map you like.
2. Click on the "Hamburger Menu" (three horizontal lines) in the top left of the UI.
3. Select the *Share or embed map* option.
4. Select the Embed map option, which will give you some `<iframe>` code — copy this.
5. Insert it into the *Input* box below, and see what the result is in the *Output*.

If you make a mistake, you can always reset it using the *Reset* button. If you get really stuck, press the *Show solution* button to see an answer.

[Active learning classic embedding uses sample](https://yari-demos.prod.mdn.mozit.cloud/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies/_sample_.active_learning_classic_embedding_uses.html)

## [iframes in detail](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies#iframes_in_detail "Permalink to iframes in detail")

So, that was easy and fun, right? [`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) elements are designed to allow you to embed other web documents into the current document. This is great for incorporating third-party content into your website that you might not have direct control over and don't want to have to implement your own version of — such as video from online video providers, commenting systems like [Disqus](https://disqus.com/), maps from online map providers, advertising banners, etc. The live editable examples you've been using through this course are implemented using `<iframe>`s.

There are some serious [Security concerns](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies#security_concerns) to consider with `<iframe>`s, as we'll discuss below, but this doesn't mean that you shouldn't use them in your websites — it just requires some knowledge and careful thinking. Let's explore the code in a bit more detail. Say you wanted to include the MDN glossary on one of your web pages — you could try something like this:

```

```

Copy to Clipboard

This example includes the basic essentials needed to use an `<iframe>`:

- [`border: none`](https://developer.mozilla.org/en-US/docs/Web/CSS/border)

  If used, the `<iframe>` is displayed without a surrounding border. Otherwise, by default, browsers display the `<iframe>` with a surrounding border (which is generally undesirable).

- [`allowfullscreen`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-allowfullscreen)

  If set, the `<iframe>` is able to be placed in fullscreen mode using the [Fullscreen API](https://developer.mozilla.org/en-US/docs/Web/API/Fullscreen_API) (somewhat beyond the scope of this article.)

- [`src`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-src)

  This attribute, as with [`<video>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)/[`<img>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img), contains a path pointing to the URL of the document to be embedded.

- [`width`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-width) and [`height`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-height)

  These attributes specify the width and height you want the iframe to be.

- Fallback content

  In the same way as other similar elements like [`<video>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video), you can include fallback content between the opening and closing `<iframe></iframe>` tags that will appear if the browser doesn't support the `<iframe>`. In this case, we have included a link to the page instead. It is unlikely that you'll come across any browser that doesn't support `<iframe>`s these days.

- [`sandbox`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-sandbox)

  This attribute, which works in slightly more modern browsers than the rest of the `<iframe>` features (e.g. IE 10 and above) requests heightened security settings; we'll say more about this in the next section.

**Note:** In order to improve speed, it's a good idea to set the iframe's `src` attribute with JavaScript after the main content is done with loading. This makes your page usable sooner and decreases your official page load time (an important [SEO](https://developer.mozilla.org/en-US/docs/Glossary/SEO) metric.)

### [Security concerns](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies#security_concerns "Permalink to Security concerns")

Above we mentioned security concerns — let's go into this in a bit more detail now. We are not expecting you to understand all of this content perfectly the first time; we just want to make you aware of this concern, and provide a reference to come back to as you get more experienced and start considering using `<iframe>`s in your experiments and work. Also, there is no need to be scared and not use `<iframe>`s — you just need to be careful. Read on...

Browser makers and Web developers have learned the hard way that iframes are a common target (official term: **attack vector**) for bad people on the Web (often termed **hackers**, or more accurately, **crackers**) to attack if they are trying to maliciously modify your webpage, or trick people into doing something they don't want to do, such as reveal sensitive information like usernames and passwords. Because of this, spec engineers and browser developers have developed various security mechanisms for making `<iframe>`s more secure, and there are also best practices to consider — we'll cover some of these below.

**Note:** [Clickjacking](https://developer.mozilla.org/en-US/docs/Glossary/Clickjacking) is one kind of common iframe attack where hackers embed an invisible iframe into your document (or embed your document into their own malicious website) and use it to capture users' interactions. This is a common way to mislead users or steal sensitive data.

A quick example first though — try loading the previous example we showed above into your browser — you can [find it live on GitHub](https://mdn.github.io/learning-area/html/multimedia-and-embedding/other-embedding-technologies/iframe-detail.html) ([see the source code](https://github.com/mdn/learning-area/blob/gh-pages/html/multimedia-and-embedding/other-embedding-technologies/iframe-detail.html) too.) Instead of the page you expected, you'll probably see some kind of message to the effect of "I can't open this page", and if you look at the *Console* in the [browser developer tools](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_are_browser_developer_tools), you'll see a message telling you why. In Firefox, you'll get told something like *The loading of "https://developer.mozilla.org/en-US/docs/Glossary" in a frame is denied by "X-Frame-Options" directive set to "DENY".*. This is because the developers that built MDN have included a setting on the server that serves the website pages to disallow them from being embedded inside `<iframe>`s (see [Configure CSP directives](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies#configure_csp_directives), below.) This makes sense — an entire MDN page doesn't really make sense to be embedded in other pages unless you want to do something like embed them on your site and claim them as your own — or attempt to steal data via [clickjacking](https://developer.mozilla.org/en-US/docs/Glossary/Clickjacking), which are both really bad things to do. Plus if everybody started to do this, all the additional bandwidth would start to cost Mozilla a lot of money.

#### Only embed when necessary

Sometimes it makes sense to embed third-party content — like youtube videos and maps — but you can save yourself a lot of headaches if you only embed third-party content when completely necessary. A good rule of thumb for web security is *"You can never be too cautious. If you made it, double-check it anyway. If someone else made it, assume it's dangerous until proven otherwise."*

Besides security, you should also be aware of intellectual property issues. Most content is copyrighted, offline and online, even content you might not expect (for example, most images on [Wikimedia Commons](https://commons.wikimedia.org/wiki/Main_Page)). Never display content on your webpage unless you own it or the owners have given you written, unequivocal permission. Penalties for copyright infringement are severe. Again, you can never be too cautious.

If the content is licensed, you must obey the license terms. For example, the content on MDN is [licensed under CC-BY-SA](https://developer.mozilla.org/en-US/docs/MDN/About#copyrights_and_licenses). That means, you must [credit us properly](https://wiki.creativecommons.org/wiki/Best_practices_for_attribution) when you quote our content, even if you make substantial changes.

#### Use HTTPS

[HTTPS](https://developer.mozilla.org/en-US/docs/Glossary/https) is the encrypted version of [HTTP](https://developer.mozilla.org/en-US/docs/Glossary/HTTP). You should serve your websites using HTTPS whenever possible:

1. HTTPS reduces the chance that remote content has been tampered with in transit,
2. HTTPS prevents embedded content from accessing content in your parent document, and vice versa.

HTTPS-enabling your site requires a special security certificate to be installed. Many hosting providers offer HTTPS-enabled hosting without you needing to do any setup on your own to put a certificate in place. But if you *do* need to set up HTTPS support for your site on your own, [Let's Encrypt](https://letsencrypt.org/) provides tools and instructions you can use for automatically creating and installing the necessary certificate — with built-in support for the most widely-used web servers, including the Apache web server, Nginx, and others. The Let's Encrypt tooling is designed to make the process as easy as possible, so there's really no good reason to avoid using it or other available means to HTTPS-enable your site.

**Note:** [GitHub pages](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Using_Github_pages) allow content to be served via HTTPS by default, so it is useful for hosting content. If you are using a different hosting provider and are not sure, ask them about it.

#### Always use the `sandbox` attribute

You want to give attackers as little power as you can to do bad things on your website, therefore you should give embedded content *only the permissions needed for doing its job.* Of course, this applies to your own content, too. A container for code where it can be used appropriately — or for testing — but can't cause any harm to the rest of the codebase (either accidental or malicious) is called a [sandbox](<https://en.wikipedia.org/wiki/Sandbox_(computer_security)>).

Unsandboxed content can do way too much (executing JavaScript, submitting forms, popup windows, etc.) By default, you should impose all available restrictions by using the `sandbox` attribute with no parameters, as shown in our previous example.

If absolutely required, you can add permissions back one by one (inside the `sandbox=""` attribute value) — see the [`sandbox`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe#attr-sandbox) reference entry for all the available options. One important note is that you should *never* add both `allow-scripts` and `allow-same-origin` to your `sandbox` attribute — in that case, the embedded content could bypass the [Same-origin policy](https://developer.mozilla.org/en-US/docs/Glossary/Same-origin_policy) that stops sites from executing scripts, and use JavaScript to turn off sandboxing altogether.

**Note:** Sandboxing provides no protection if attackers can fool people into visiting malicious content directly (outside an `iframe`). If there's any chance that certain content may be malicious (e.g., user-generated content), please serve it from a different [domain](https://developer.mozilla.org/en-US/docs/Glossary/Domain) to your main site.

#### Configure CSP directives

[CSP](https://developer.mozilla.org/en-US/docs/Glossary/CSP) stands for **[content security policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)** and provides [a set of HTTP Headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) (metadata sent along with your web pages when they are served from a web server) designed to improve the security of your HTML document. When it comes to securing `<iframe>`s, you can *[configure your server to send an appropriate `X-Frame-Options` header.](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options)* This can prevent other websites from embedding your content in their web pages (which would enable [clickjacking](https://developer.mozilla.org/en-US/docs/Glossary/Clickjacking) and a host of other attacks), which is exactly what the MDN developers have done, as we saw earlier on.

**Note:** You can read Frederik Braun's post [On the X-Frame-Options Security Header](https://blog.mozilla.org/security/2013/12/12/on-the-x-frame-options-security-header/) for more background information on this topic. Obviously, it's rather out of scope for a full explanation in this article.

## [The <embed> and <object> elements](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Other_embedding_technologies#the_embed_and_object_elements "Permalink to The <embed> and <object> elements")

The [`<embed>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed) and [`<object>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object) elements serve a different function to [`<iframe>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) — these elements are general purpose embedding tools for embedding external content, such as PDFs.

However, you are unlikely to use these elements very much. If you need to display PDFs, it's usually better to link to them, rather than embedding them in the page.

Historically these elements have also been used for embedding content handled by browser [plugins](https://developer.mozilla.org/en-US/docs/Glossary/Plugin) such as [Adobe Flash](https://developer.mozilla.org/en-US/docs/Glossary/Adobe_Flash), but this technology is now obsolete and is not supported by modern browsers.

If you find yourself needing to embed plugin content, this is the kind of information you'll need, at a minimum:

|                                                                                                              | [`<embed>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed)                                                                                                  | [`<object>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object)                                                                                                  |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [URL](https://developer.mozilla.org/en-US/docs/Glossary/URL) of the embedded content                         | [`src`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed#attr-src)                                                                                             | [`data`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object#attr-data)                                                                                            |
| *accurate* [media type](https://developer.mozilla.org/en-US/docs/Glossary/MIME_type) of the embedded content | [`type`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed#attr-type)                                                                                           | [`type`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object#attr-type)                                                                                            |
| height and width (in CSS pixels) of the box controlled by the plugin                                         | [`height`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed#attr-height) [`width`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/embed#attr-width) | [`height`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object#attr-height) [`width`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/object#attr-width) |
| names and values, to feed the plugin as parameters                                                           | ad hoc attributes with those names and values                                                                                                                                 | single-tag [`<param>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/param) elements, contained within `<object>`                                                   |
| independent HTML content as fallback for an unavailable resource                                             | not supported (`<noembed>` is obsolete)                                                                                                                                       | contained within `<object>`, after `<param>` elements                                                                                                                           |

Let's look at an `<object>` example that embeds a PDF into a page (see the [live example](https://mdn.github.io/learning-area/html/multimedia-and-embedding/other-embedding-technologies/object-pdf.html) and the [source code](https://github.com/mdn/learning-area/blob/gh-pages/html/multimedia-and-embedding/other-embedding-technologies/object-pdf.html)):

```

```

Copy to Clipboard

PDFs were a necessary stepping stone between paper and digital, but they pose many [accessibility challenges](https://webaim.org/techniques/acrobat/acrobat) and can be hard to read on small screens. They do still tend to be popular in some circles, but it is much better to link to them so they can be downloaded or read on a separate page, rather than embedding them in a webpage.

<!--EndFragment-->
