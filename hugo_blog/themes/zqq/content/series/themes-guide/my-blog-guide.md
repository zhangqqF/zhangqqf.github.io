+++
author = "zhangqq"
title = "Blog guide"
date = "2023-11-06"
description = "Guide to my blog"
tags = ["guide"]
+++

## Jekyll

For windows:
- Install [Ruby]()
- Install Jekyll
	```
	gem install jekyll
	```
	
### Create a bolg
```
jekyll new myblog
```
```
cd myblog
```
```
jekyll serve
```


## Hugo

Download [hugo](https://github.com/gohugoio/hugo/releases). Choose `hugo_extended_0.120.3_windows-amd64` which not need to install. And add the path of hugo to environment variables.

Download the puppet theme on [Hugo Themes](https://themes.gohugo.io/).



### Create a blog

1. Create a new site.

   ```
   hugo new site myblog
   ```

2. Enter the myblog directory.

   ```
   cd myblog
   ```

3. Pull the puppet theme to the local.

   ```
   git clone git@github.com:McShelby/hugo-theme-puppet.git themes/puppet
   ```

4. Cut the files in the `exampleSite` directory of the puppet theme to which's root directory, and delete the `exampleSite` folder.

5. Launch hugo server

   ```
   hugo server -t puppet --buildDrafts
   ```

6. Look at the site `http://localhost:1313/`.

### My blog

- Rename the puppet theme folder as zqq, and modify the *theme="puppet"* to *theme="zqq"* in the file `config.toml` as meanwhile.
- Modify the title in the file `hugo.toml`
- config.toml
	- menu
	- sidebar
	- params
	- social
	- friends
- Questions
	- Remove the hyperlink located up-left
	- How to set the fonts
	- Add jianshu to the social
- Build my blog
	```
	hugo -t zqq
	```
	A folder of public is appear in the root directory of the blog.
	Push all the files in the public folder to the github pages.
