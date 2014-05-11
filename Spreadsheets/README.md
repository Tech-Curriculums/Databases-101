## Spreadsheets

While no where near as scalable, for smaller projects as well as projects in which 
you would like to incorporate colleagues who are familiar with the spreadsheet environment,
You may consider uploading the data to a spreadsheet (perhaps even a shared spreadsheet).

Consider these for the other extreme of the spectrum: when data is really small, and where accessibility
of the data is paramount.

In this segment, we'll learn the basics of working with these visual data-homes, quickly review functions,
pivot-tables, and how to do more with the platform for cloud-spreadsheets from Google.


## Hacking the spreadsheet into a public database

Code as seen on hacker news from:
http://www.mattcutts.com/blog/write-google-spreadsheet-from-python/

```python
import time
import gdata.spreadsheet.service

email = 'youraccount@gmail.com'
password = 'yourpassword'
weight = '180'
# Find this value in the url with 'key=XXX' and copy XXX below
spreadsheet_key = 'pRoiw3us3wh1FyEip46wYtW'
# All spreadsheets have worksheets. I think worksheet #1 by default always
# has a value of 'od6'
worksheet_id = 'od6'

spr_client = gdata.spreadsheet.service.SpreadsheetsService()
spr_client.email = email
spr_client.password = password
spr_client.source = 'Example Spreadsheet Writing Application'
spr_client.ProgrammaticLogin()

# Prepare the dictionary to write
dict = {}
dict['date'] = time.strftime('%m/%d/%Y')
dict['time'] = time.strftime('%H:%M:%S')
dict['weight'] = weight
print dict

entry = spr_client.InsertRow(dict, spreadsheet_key, worksheet_id)
if isinstance(entry, gdata.spreadsheet.SpreadsheetsList):
  print "Insert row succeeded."
else:
  print "Insert row failed."
```


## References and Further Reading

Code as seen on hacker news from:
http://www.mattcutts.com/blog/write-google-spreadsheet-from-python/
