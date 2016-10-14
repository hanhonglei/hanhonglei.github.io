---
layout: post
title:  Qestions about building blog website use Jekyll
date:   2016-10-13 15:52:37 -0400
categories: jekyll update
---
- 1. Add your repository name with organization to your _config.yml, like: repository: henry/henrydf.github.io. See it from [here](https://github.com/jekyll/jekyll/issues/4705)

- 2. About "GitHub Metadata warning", you should follow these steps as describe in [this site](https://www.hieule.info/programming/fix-errors-github-metadata-ssl-certificate-running-jekyll-serve/):

	- 2.1 GitHub Metadata is a gem required by Jekyll. We need a GitHub personal token to make it work. Follow the excellent guide on GitHub to create a token, copy it to a safe place.
Now, create new environment variable in your system named JEKYLL_GITHUB_TOKEN with the value pasted from the created token. 

	- 2.2 Now, down load the .pem file from [here](https://curl.haxx.se/ca/cacert.pem). Then, create another environment variable called SSL_CERT_FILE pointing to the location of downloaded .pem file.

--

With the steps above, I resolved my problems with Jekyll server command. If you try and find any trouble with them, please let me know by leaving comments at the bottom of the post.

You can also check [this video](https://www.youtube.com/watch?v=1bQqkyvH5ps) out.