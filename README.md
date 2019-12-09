# SmartRegEx Python Module

# About
The SmartRegEx is an automatic and extensible parser of regex.
You can initialize SmartRegEx with parseable text and SmartRegEx.parsed returns all matched patterns with matched outputs.
SmartRegEx.capabilities returns a JSON object of all the rule keys and regexes, which can be extended or changed for new rules parsing.

# To get started in Python code, simply import the module

from smartregex import SmartRegex

Then initialize the parser with input text
```    smart = SmartRegex(input_text)```

Automatic parsing of the text against the smart regex capabilities:    
```    smart.parsed```

Check if text has any rule data matching emails rule:
```    smart.has('emails')```

To get started, run
```     # python3 main.py test.txt```
This will run the SmartRegEx logic on input text file test.txt

A sample test text file is:
```
Here is my address:
1 Main St 
Boston, MA 02111 

IP range: 1.2.3.4/20 
Hex color: #ffffff 
UK Phone: 0208 123 1234 
International Phone: +31(0)235256677 

IP: 1.2.3.4 
IPv6: ::1 
MAC address: 00:0a:95:9d:68:16 
To: andrei@oprisan.com 
From: support@apple.com 
Subject: Appointment Dec 27th 2019 at 4:30PM 
Body: Call us at 1(800)-555-4444x321 or email us at prize@apple.com to claim your $1,000,000.00 prize!
```

A sample output of main.py test.txt is:
```
Reading from file test.txt
1. Raw Text is here:
('Here is my address:\n'
 '1 Main St \n'
 'Boston, MA 02111 \n'
 '\n'
 'IP range: 1.2.3.4/20 \n'
 'Hex color: #ffffff \n'
 'UK Phone: 0208 123 1234 \n'
 'International Phone: +31(0)235256677 \n'
 '\n'
 'IP: 1.2.3.4 \n'
 'IPv6: ::1 \n'
 'MAC address: 00:0a:95:9d:68:16 \n'
 'To: andrei@oprisan.com \n'
 'From: support@apple.com \n'
 'Subject: Appointment Dec 27th 2019 at 4:30PM \n'
 'Body: Call us at 1(800)-555-4444x321 or email us at prize@apple.com to claim '
 'your $1,000,000.00 prize!')
2. Initiated SmartRegex parsed results:
{'amount': ['$1,000,000.00'],
 'dates': ['3.4/20', 'Dec 27th 2019'],
 'emails': ['andrei@oprisan.com', 'support@apple.com', 'prize@apple.com'],
 'hex_colors': ['#ffffff'],
 'ip_range': ['1.2.3.4/20', '1.2.3.4'],
 'ips': ['1.2.3.4', '1.2.3.4'],
 'ipv6s': ['::1'],
 'links': ['oprisan.com', 'apple.com', 'apple.com'],
 'mac_address': ['00:0a:95:9d:68:16'],
 'phone': ['0208 123 1234', '235256677', '1(800)-555-4444'],
 'phone_expanded': ['1(800)-555-4444x321'],
 'street': ['1 Main St'],
 'times': ['68:16', '4:30PM'],
 'zip': ['02111']}
3. Checking specific elements:
3.a. Checking for emails:
['andrei@oprisan.com', 'support@apple.com', 'prize@apple.com']
3.b. Checking for street address:
['1 Main St']
3.c. Checking for dates:
['3.4/20', 'Dec 27th 2019']
```

To run all unit tests, run
```     # python3 test.py```

A fully passing test output should look like this:
```
test_link (__main__.TestLinks) ... ok
test_email (__main__.TestEmails) ... ok
test_date (__main__.TestDates) ... ok
test_time (__main__.TestTimes) ... ok
test_ip (__main__.TestIP) ... ok
test_ipv6 (__main__.TestIPv6) ... ok
test_phone (__main__.TestPhone) ... ok
test_zip (__main__.TestZipCodes) ... ok
test_amount (__main__.TestAmount) ... ok
test_street (__main__.TestStreet) ... ok
test_hex_color (__main__.TestHexColors) ... ok

----------------------------------------------------------------------
Ran 11 tests in 0.036s

OK
```
