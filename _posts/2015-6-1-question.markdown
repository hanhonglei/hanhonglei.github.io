---
layout: post
title:  Qestions about building blog website use Jekyll
date:   2015-6-1 15:52:37 -0400
categories: article
---
<!--more-->

## Steps to set up personal blog website in Github

Install Jekyll and related environments follow the instruction strictly [here](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/).

Before finally call build function of Jekyll, you should follow these steps to let it run successfully on Windows system.


1. Add your repository name with organization to your **_config.yml**, like: repository: henry/henrydf.github.io. See it from [here](https://github.com/jekyll/jekyll/issues/4705)

2. About "GitHub Metadata warning", you should follow these steps as describe in [this site](https://www.hieule.info/programming/fix-errors-github-metadata-ssl-certificate-running-jekyll-serve/):

	2.1 GitHub Metadata is a gem required by Jekyll. We need a GitHub personal token to make it work. Follow the excellent guide on GitHub to create a token, copy it to a safe place.
Now, create new environment variable in your system named `JEKYLL_GITHUB_TOKEN` with the value pasted from the created token. 

	2.2 Now, down load the .pem file from [here](https://curl.haxx.se/ca/cacert.pem). Then, create another environment variable called `SSL_CERT_FILE` pointing to the location of downloaded .pem file.

You can also check [this video](https://www.youtube.com/watch?v=1bQqkyvH5ps) out.

## Create contents of the blog website

The Github pages blog system is heavily based on the Github repository. Any new posted posts should be placed in _posts folder, and give a specific file name date `YYYY-MM-DD-name-of-post.markdown`.

Any posted articles will be automatically updated by Github pages after you push them to your Github repository.

## Grab particular posts in the blog website

If you want to collect some particular posts in a page, code work wouldn’t be avoided.
The code below will collect all posts have category type poem, and the post date will also be rendered:

{% highlight liquid %}
{% raw %}
<ul>
	{% for post in site.posts %} 
		{% if post.categories contains 'poem' %}
		<li>
			<a href="{{ post.url }}">{{ post.title }}</a>
			<span>({{ post.date | date:"%Y-%m-%d" }})</span>
			{{ post.excerpt }}
		</li>
		{% endif %} 
	{% endfor %}
</ul>
{% endraw %}
{% endhighlight %}

## Keep update of the resource
You should always update functions to keep your Jekyll resources up to date.

If you followed our setup recommendations and installed Bundler, run `bundle update github-pages` or simply `bundle update` and all your gems will update to the latest versions.

If you don't have Bundler installed, run `gem update github-pages`

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-85986843-1', 'auto');
  ga('send', 'pageview');

</script>

