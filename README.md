honbasho
========

Archive [Grand Sumo](http://www.sumo.or.jp/en/) tournament
highlights, as they are _removed_ :sob: before each new tournament. 

Usage
-----

Update config file, e.g.:

```
[
    "201501": {
	"source": "http://www.sumo.or.jp/en/honbasho/topics/ko_torikumi15/list",
	"date": "3 Feb 2015",
	"title": "Hatsu 2015 (January) Grand Sumo Highlights",
	"archive": "honbasho-2015-hatsu"
    }, ...
]
```

Crawl and Download:

```shell
# get highlights metadata
$ crawl.py {selector} > data.json

# download movies and text
$ download.py {dest} data.json

# make HTML index
$ index.py data.json {selector} > highlights.html

```

Upload to Internet Archive (may use [siznax/iatools](https://github.com/siznax/iatools))

```shell
$ iatools/s3upload.py {item} data.json -m "mediatype:movies" "collection:opensource_media"
$ iatools/s3upload.py {item} highlights.html
$ iatools/s3upload.py {item} *.mp4
```

Update archived highlights on `gh-pages` branch.

See https://siznax.github.io/honbasho

Enjoy!

@siznax
