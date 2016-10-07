# Scrapy-sqlite-item-exporter

Export items to sqlite3 database crawled by scrapy 1.2.0

# How to use

## Step 1
I assume you have a Scrapy project already. If not, create one:
```bash
$ scrapy startproject projectname
```

## Step 2
Place `exporters.py` in the same folder as `settings.py`

## Step 3
In settings.py, add the following line:
``` python
FEED_EXPORTERS = {
    'sqlite': 'exporters.SqliteItemExporter',
}
```

## Step 4
3. In `items.py` define the item according to the following pattern:
``` python
class QuotesItem(scrapy.Item):
    txt = scrapy.Field() # column #1
    author = scrapy.Field() # column #2
    sqlite_keys = ["txt", "author"] 
```

## Step 5
Start crawling:
```bash
$ scrapy crawl <spider name> -o sqlite.db -t sqlite
```
