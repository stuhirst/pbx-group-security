# pbx-group-security

This is the source code for the https://pbx-group-security.com

# Dev notes

* Static website generation using [Hugo](https://gohugo.io)
* based on the [Hugo Universal Theme](https://themes.gohugo.io/hugo-universal-theme/)

# Build

* Install [Go](https://golang.org/)
* Install [Hugo](https://gohugo.io/getting-started/installing/)
* Install [Node.js](https://nodejs.org/en/download/)

Clone or fork this repo and run npm install:

```
>git clone https://github.com/project-cx/pbx-group-security
>cd pbx-group-security
>npm install
```

# Run

```
>hugo serve
```
Go to http://localhost:1313

# Test

Coming soon!

# Building Static Assets with Gulp

```
>gulp -T
...
--js
--css
--images
--- default
    --js
    --css
    --images
...
>gulp images
...
```
