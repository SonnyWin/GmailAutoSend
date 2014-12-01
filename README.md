GmailAutoSend
=============

This is an auto send e-mail via <b>Google Sheets</b> which will access <b>Gmail</b> and reading <b>Draft</b> messages' subject to control the time of delivery (i.e.: 5 pm, 1/1,   etc.).

<b>Google Sheets</b> is awesome and I want to share my script when learning it.

This script is designed to update sheet with only necessary history changes (check before updating). 

Steps to Use
============
1. Make new or use existing <b>Google Sheets</b>
2. Go to <b>Tools</b> | <b>Script editor...</b>
3. Paste the text from <b>script.txt</b> into the editor
4. <b>Optional:</b> Modify three functions below at bottom part for the sheet name (default: <i>"Auto Email"</i>), change second parameter into true at <i>runPrepareSheet</i> for <b>mm/dd/yyyy</b> date format.
  - <i>runPrepareSheet</i>
  - <i>loopCheckingDraftMessages</i>
  - <i>loopCheckingTestSubjects</i>
5. Run <i>runPrepareSheet</i> function and allow script to access your <b>Gmail</b> accounts
6. <b>Optional:</b> Go to the sheet and change the paramter cells with green background, unhide rows 1-8 for showing advanced parameters
7. At script editor, click the <b>"Current script's trigger"</b> and set up method below with every 30 minutes or even every minute recurrence
  - <i>loopCheckingDraftMessages</i>
8. <b>Optional:</b> Add some subject tests to see their resulting delivery date/time and run function below.
  - <i>loopCheckingTestSubjects</i>
9. Go to <b>Gmail</b> and make a draft message with schedule inside brackets, it will be sent automatically and history will be kept in the sheet and in <b>Trash</b> at <b>Gmail</b><br>
   <b>Ex.:</b> Subject is <i>"Test draft which will be sent automatically in 5 minutes (+0:5)"</i>

Format
======
 <b>Schedule:</b> <i>( Date | Date Time | Time Date | Time)</i><br>
 <b>Date:</b> <i>Number [ / Number [ / Number ] ]</i><br>
 <b>Time:</b> <i>[ @ | + ] Number [ : Number [ : Number ] ] [ AM | PM ]</i><br>

Date is in <b>dd/mm/yyyy</b> format by default.

Examples
========
<table>
  <tr><td><i>(1/1 0:0)</i></td><td>    Send at midnight at 1st Jan</td></tr>
  <tr><td><i>(24)</i></td><td>         Send at 24th of the month</td></tr>
  <tr><td><i>(24/12)</i></td><td>      Send at 24th of December</td></tr>
  <tr><td><i>(20:00)</i></td><td>      Send at 20:00 of the day</td></tr>
  <tr><td><i>(+1:30)</i></td><td>      Send at 1 hour 30 minutes after the draft creation time</td></tr>
  <tr><td><i>(25@11pm)</i></td><td>    Send at 23:00, 25th of the month</td></tr>
  <tr><td><i>[15)</i></td><td>         Send at 15th of the month</td></tr>
  <tr><td><i>(1/2)</i></td><td>        Send at 1st February</td></tr>
</table>

Notes
=====
  - When date/time has past and already more than 1 day (except diff. month) or 1 hour behind, then day/month will be added by 1.
  - There is a safety check which will not send draft message within 5 minutes even the scheduled date/time is below 5 minutes. This is due to the nature to write subject before body and unfinished draft will still be read by this script. 
  - Make experiment at column <b>N</b> under <i>"Test Subject"</i>

Donation
========

I accept donation below. Thank you!

<a href="https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=LYAG8ESEQFDM2&lc=AU&item_name=GmailAutoSend&currency_code=AUD&bn=PP%2dDonationsBF%3abtn_donateCC_LG%2egif%3aNonHosted"><img src="https://www.paypalobjects.com/en_AU/i/btn/btn_donateCC_LG.gif"></a>
