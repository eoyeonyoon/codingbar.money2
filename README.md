# codingbar.money2
# 股票資料爬蟲程式

這是一個用於爬取台灣證券交易所（TWSE）股票交易資料的程式。程式使用 Python，並使用 `requests` 庫來向 TWSE 的網站發送 HTTP 請求以獲取股票交易資料。程式還使用 `xml.etree.ElementTree` 庫來解析設定文件 `setting.xml`。

## 如何使用

1. 創建一個 `setting.xml` 檔案，並根據需求填寫以下參數：

```xml
<params>
    <url>https://www.twse.com.tw/rwd/zh/afterTrading/STOCK_DAY</url>
    <excelName>統一202101_202306</excelName>
    <startYear>2021</startYear>
    <startMonth>01</startMonth>
    <endYear>2023</endYear>
    <endMonth>06</endMonth>
    <stockNo>1216</stockNo>
</params>
```
執行 main.py 檔案，程式將讀取 setting.xml 設定，根據設定的起始年月和結束年月，以及股票代號，爬取相應的股票交易資料。

## 主要功能

讀取 setting.xml 設定檔，包括要爬取的起始年月、結束年月、股票代號等資訊。
根據設定的起始年月和結束年月生成一個日期列表，用於指定要爬取的日期範圍。
使用 requests 庫向 TWSE 的網站發送 HTTP 請求，獲取股票交易資料的 JSON 格式數據。
將獲取的 JSON 數據解析，提取每日的股票交易資訊，並將這些資訊填充到 Excel 工作表中。
為 Excel 工作表添加欄位名稱並填充數據。

## 注意事項

程式將每次爬取後的數據存儲在一個 Excel 檔案中，檔名由 excelName 參數指定，請確保該檔名為有效的 Excel 檔案名稱。
在發送 HTTP 請求時，程式使用 time.sleep(3) 延遲 3 秒，以避免對目標伺服器造成過多請求，請根據需要進行調整。

## 注意事項

請確保你的 Python 環境中安裝了所需的庫，你可以使用以下命令來安裝所需的庫：

```
pip install requests openpyxl
```
