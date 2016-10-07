# Scrapy-sqlite-item-exporter

Export items to sqlite3 database crawled by scrapy 1.2.0

# How to use


1. Place `exporters.py` in the same folder as `settings.py`
2. In settings.py, add the following line:

    FEED_EXPORTERS = {
        'sqlite': 'exporters.SqliteItemExporter',
    }

3. In `items.py` define the item according to the following pattern:

    class QuotesItem(scrapy.Item):
        txt = scrapy.Field() # column #1
        author = scrapy.Field() # column #2
        sqlite_keys = ["txt", "author"] 

4. In terminal,$ scrapy crawl <spider name> -o sqlite.db -t sqlite
