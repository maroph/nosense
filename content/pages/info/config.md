+++
date = '2025-08-30T16:26:00+02:00'
draft = false
title = 'Hugo Site Configuration'
tags = ['hugo']
+++

## Hugo
I use [Hugo](https://gohugo.io/) to build my site with the
[beautifulhugo](https://github.com/halogenica/beautifulhugo)
theme.

```
$ hugo new site nosense_hugo
$ cd nosense_hugo
$ mkdir content/pages content/posts static/images/
$ git init
$ git submodule add https://github.com/halogenica/beautifulhugo themes/beautifulhugo
$ echo "theme = 'beautifulhugo'" >> hugo.toml
```

### Status/Update of the theme
```
$ git submodule status
e69e25d4ca0d3c737f0677995d2bf9541ffb4926 themes/beautifulhugo (heads/master)
```

```
$ git submodule update
```

### Clone the Repository
```
$ git clone --recurse-submodules https://github.com/maroph/nosense.git

## Additions
### File robots.txt
```
$ touch static/robots.txt
$ chmod 640 static/robots.txt

# content of file robots.txt
$ cat static/robots.txt
User-agent: *
Disallow: /
```

### Directory .well-known
```
mkdir -p static/.well-known
chmod 750 static/.well-known
```

#### File .well-known/security.txt
```
$ chmod 640 static/.well-known/security.txt
$ cat static/.well-known/security.txt
Contact: mailto:maroph@pm.me
Expires: 2025-12-31T22:59:00.000Z
Preferred-Languages: de, en, nl
Canonical: https://maroph.github.io/nosense/.well-known/security.txt
-----BEGIN PGP SIGNATURE-----

iQIzBAEBCgAdFiEEA5j4H/oU4tBbTbZpE11zypMCpZcFAmiuuUUACgkQE11zypMC
pZe81Q/+KhzkNFmDGUx5+WNcHsuhWvNLJR70MgM1+6ZFAV9ETWk8nhzwloKfB3TG
vJ/1RteGKoq5yWTudL7snz5WKyiHsMJjghAXpREkK5I4Y1RWMLZifNK87ICyiyMQ
7VKW5Aw9ItD45pOfSoRyS7gWsKqROFz9W9OS+6cxkSABAkrtrUR6mPHpoV0H27Ru
mddhZ2dzPQtkXkgDMoXMSL22VT4rKndHdnzgw8bmuW4JjzB1YviyPeopFChAIi+p
ytt06aKrsbe7mehwQUCqMLgjD0uTg6F5FXhR6cnu6FWDBWN53a4sIUMa3ywPOZ8+
6deodKS4IgV37VFVQfB6LB447xRmk/26Mh/yG1uy0F4KzLvXP8efXUQjLQHbbct8
Id9tMWn4jwtVSXihbUbD76p1PuFECaJtXOCXJT5x8h1YpFAPsyr08JkuhTKHJwNk
FgBz7ji4VmRVHCw5BMFytaXqyDJCxS9Fbz2Wju555ZxcEk6G3knmDecQXrq7xku4
mMCDJWfEL9EM0k9cwwTdLtqJw2rkFheo2OVrqbtbzszTeBFtjcBva80AYn0Q/ft5
rECPmFN9k5KXHyZ45dKOHxKrDe7CUmPk6hqBdHMVoekMkW+RGQfmjZGRYoSJcg2u
CYI1/dMAAULGW6Jd/sNla1GZSGeyHFAWmdfvfK0Y4FLNFoJ9T+Y=
=Muuk
-----END PGP SIGNATURE-----
```

#### File .well-known/webfinger
**Not used at the moment.**

```
$ curl https://mastodon.social/.well-known/webfinger?resource=acct%3Amaroph%40mastodon.social >./static/.well-known/webfinger
$ chmod 640 ./static/.well-known/webfinger
$ cat ./static/.well-known/webfinger
{"subject":"acct:maroph@mastodon.social","aliases":["https://mastodon.social/@maroph","https://mastodon.social/users/maroph"],"links":[{"rel":"http://webfinger.net/rel/profile-page","type":"text/html","href":"https://mastodon.social/@maroph"},{"rel":"self","type":"application/activity+json","href":"https://mastodon.social/users/maroph"},{"rel":"http://ostatus.org/schema/1.0/subscribe","template":"https://mastodon.social/authorize_interaction?uri={uri}"},{"rel":"http://webfinger.net/rel/avatar","type":"image/png","href":"https://files.mastodon.social/accounts/avatars/111/708/673/709/924/092/original/55d984c54f10241d.png"}]}
```

### Custom header/footer files
* layouts/partials/head_custom.html
* layouts/partials/footer_custom.html

The beautifulhugo theme supports custom header/footer files. I use this
files to make some small changes to the theme layout.

#### File head_custom.html
```
<style>
body {
  background: #fcfcfc;
}
.pages-heading, .posts-heading {
  text-align: center;
}
</style>
```

#### File footer_custom.html
```
<div style="display: block; margin: 5px;">
License: <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank">CC-BY 4.0</a>
</div>
```

