# mailreport 
##### Python package for 
  - Sending autmoated mails in CSV/XLSX/TXT/HTML/EMAIL-BODY/HYPERLINKS formats. 
#
**mailreport** is a data module which is used for sending simple automated reports via mail.
### Installation
**mailreport** requires below packages **dependencies**:
*pandas, psycopg2, smtplib, email.mime.text, email.mime.multipart*

##### Installation Commands
To install the latest Pypi version, you’ll need to execute:

``` r
    pip install mailreport
    or
    python3 -m pip install mailreport
```

If instead you want to install the latest github master version:

``` r
    git clone https://github.com/nit567esh/mailreport.git
    cd <pkg_directory>
    python3 setup.py install
```
### Usages
**Functions:**
**Two functions can be used in this module**
```diff
- makeoutput: A user can pass different output format and report will be prepared as per provided format. Available formats are CSV/TXT/XLSX/HTML/HTML-TEXT/HYPERLINK. 
- sendmail: A user can send mail to target receptionist using this module by attaching files/HTML text/Hyperlinks/Normal text ext. 
```
*1. Send CSV(s)/TXT(s) Report*
```sh
>>> import mailreport as mr
>>> df_list = [dataframe1, dataframe2]
>>> mr.makeoutput(format_type='csv', df_list=[df_list[0], df_list[1]], file_list=['name1.csv','name2.csv'])
>>> sendmail(mailserver='gmail', 
    email='xxxxx@gmail.com',
    password = 'XXXX23CCVVXX',
    to = ['xxxxxx@gmail.com'],
    cc = None, 
    bcc = None, 
    subject = 'Updated Report XXXXX', 
    message = None, 
    messageHTML = "<html><html><body><p><b>Hi All,</b><br><br>Below is the attached updated report.<br><br><b>Regards,</b><b><br>Team Name</b></p></body></html>", 
    files = ['name1.csv','name2.csv'])
```
*2. Send EXCEL(.XLSX) Report*
```sh
>>> import mailreport as mr
>>> df_list = [dataframe1]
>>> mr.makeoutput(format_type='xlsx', df_list=[df_list[0]], workbook_name='name.xlsx', sheet_list = ['XXXX'])
>>> sendmail(mailserver='gmail', 
    email='xxxx@gmail.com',
    password = 'XXXX23CCVVXX',
    to = ['xxxxx@gmail.com'],
    cc = None, 
    bcc = None, 
    subject = 'Updated Report XXXXX', 
    message = None, 
    messageHTML = "<html><html><body><p><b>Hi All,</b><br><br>Below is the attached updated report.<br><br><b>Regards,</b><b><br>Team Name</b></p></body></html>", 
    files = ['name.xlsx'])
```
*2. Send More advance report i.e one import dataframe to email body(html text) & other as csv attachment*
```sh
>>> import mailreport as mr
>>> df_list = [dataframe1, dataframe2]
>>> mr.makeoutput(format_type='csv', df_list=[df_list[0],df_list[1]], file_list=['name1.csv','name2.csv'])
>>> df_as_html = mr.makeoutput(format_type='html_text', df_list=[df_list[1]])
>>> sendmail(mailserver='gmail', 
    email='xxxxxx@gmail.com',
    password = 'XXXX23CCVVXX',
    to = ['xxxxxxx@gmail.com'],
    cc = None, 
    bcc = None, 
    subject = 'Updated Report XXXXX', 
    message = None, 
    messageHTML = str("<html><html><body><p><b>Hi All,</b><br><br>Below is the attached updated report.<br>")+str(df_as_html)+str("<br><b>Regards,</b><b><br>Team Name</b></p></body></html>"), 
    files = ['name1.xlsx','name2.xlsx'])
```
**Note** - 
* We can only use csv/html_text/htmlfile/xlsx as format_type.
