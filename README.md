
How to Update the App code for your Convention
===============================================

1. Copy this spreadsheet as a template http://bit.ly/iosched_template
	* this was derived from my effort to get this working with the IEEE MASS 2010 conference where I happened to be at while working on this.

** or **

1. Create a google spreadsheet with 3 sub-sheets, titled: sessions, speakers, sandbox.
1. add the following columns to "sessions" worksheet: 
	* sessiondate, sessiontime, room, product, track, sessiontype, sessiontitle, tags, sessionspeakers, speakers, sessionabstract, sessionrequirements, sessionlink, sessionhashtag, fulllink, youtubelink, pdflink, moderatorlink, waveid, wavelink
	* (sessionlink MUST be filled in and unique!)
1. add the following columns to the "speakers" worksheet: 
	* speakertitle, speakercompany, speakerabstract, speakerldap
1. add the following columns to the "sandbox" worksheet: 
	* companyname, companylocation, companydesc, companyurl, productdesc, companylogo, companypod, companytags

** then **
 
1. Publish the worksheet as an atom stream: 
	* click Share->Publish as a web page->Sheets to publish "all sheets"
	* grab the atom URL.
1. edit src/org/acmelab/android/apps/iosched/service/SyncService.java 
	* change WORKSHEETS_URL to be the atom URL from step 1 up above, but in this format:
	* http://spreadsheets.google.com/ + feeds/worksheets + your_spreadsheet_key + public/basic
1. replace images in res/drawables, etc with your conventions logos.
1. edit xml files in res/xml/ (blocks, tracks, rooms, sessions, etc) to reflect your conference. 


How to Compile and test app with Ant
===============================
1. cd into root src directory and run "ant debug".  This will create app apk and sign it with debug key.
1. test it on your phone or virtual device with adb install name-of-debug-app.apk


About the Original App
=========================
Google I/O is a developer conference held each year with two days of deep technical content featuring over 90 sessions, more than 5,000 developers, and over 180 demonstrations from developers showcasing their technologies.

This project is the Android app for the conference, including these features and more:

Conference schedule with calendar-block overview.
Detailed session info that is full-text searchable.
Info about companies in the Developer Sandbox.
Star sessions and Sandbox companies.
Conference map and take notes on sessions.
