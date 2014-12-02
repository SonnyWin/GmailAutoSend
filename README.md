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
4. <b>Optional:</b> Modify the name of the sheet at three functions below (default is <i>"Auto Email"</i>). The new sheet will be used to store parameters, histories and tests.
  - <i>runPrepareSheet</i>
  - <i>loopCheckingDraftMessages</i>
  - <i>loopCheckingTestSubjects</i><br>
  <b>Note:</b> If you need to change date format into <b>mm/dd/yyyy</b>, change second parameter of <i>runPrepareSheet</i> into <b>true</b>.
    <i>prepareSheet("Auto Email", <b>true</b>);</i>
5. Run <i>installGmailAutoSend</i> function and allow script to access your <b>Gmail</b> account
    <b>Note:</b> Once installation is done, it will start checking all of your <b>Draft</b> messages in <b>Gmail</b> which will be sent when their subject is having same schedule pattern (numbers in brackets).
    It's recommended to archive/delete all your draft messages nor deleted before doing this task (unless you intend to send them using this script).
6. <b>Optional:</b> Add some subject tests to see their resulting delivery date/time and run <b>"Calculate test subjects"</b> under <b>"GmailAutoSend"</b> menu.
9. Go to <b>Gmail</b> and make a draft message with schedule inside brackets, it will be sent automatically and history will be kept in the sheet and in <b>Trash</b> at <b>Gmail</b><br>
   <b>Ex.:</b> Subject is <i>"Test draft which will be sent automatically in 5 minutes (+0:5)"</i>

GmailAutoSend Menu Explanations
===============================
<b>Calculate test subjects:</b> This will calculate the scheduled delivery from the test subjects at column <b>N</b>.<br>
<b>Re-install:</b> This will create the sheet if not yet existed, write default values for formattings to the sheet and set up menu and triggers when they are not exist.<br>
<b>E-mail me:</b> This will open a window with a link to make <b>Gmail</b> empty message into myself (<u>sonny.power.win@gmail.com</u>)<br>
<b>Open Github:</b> This will open a window with a link to go to <b>GitHub</b> page of this project (https://github.com/SonnyWin/GmailAutoSend).<br>

Parameters Explanations
=======================
Parameters are put in second column of rows <b>1</b>-<b>8</b>. Some were hidden and need to unhide for changing/viewing them.<br>
<b>Default time:</b> When the schedule is not specifying the time, this default time is used. This parameter needs to be written in text. Default: '10:00<br>
<b>Max history:</b> This is the number of rows when storing sent messages in <b>History</b> section at column <b>G</b>-<b>L</b>. When it's reaching the end of rows, it goes back up again. Default: 10<br>
<b>Active:</b> This is the indicator whether the auto sending is activated or not. To deactivate, put different text other than <b>"Yes"</b>. Default: Yes<br>
<b>Sheet update:</b> This is the maximum duration of scipt not updating the sheet when there is no necessary update. This parameter needs to be written in text. Default: '12:00<br>
<b>Subject begin:</b> This is a collection of characters which will be identified as the starting character of schedule. Default: ([{<br>
<b>Subject end:</b> This is a collection of characters which will be identified as the ending character of schedule. The start and end may not be in normal pair of brackets (or character), i.e.: <b>[</b> and <b>)</b> is acceptable. Default: )]}<br>
<b>Delivery safety gap:</b> This is the duration of locked draft since saved. When draft message is still open and typed at <b>Google</b>, it's actually saved and may be sent before draft is finished. This safety delay locking will prevent the sending until that duration is reached. This parameter needs to be written in text. Default: '00:05<br>
<b>Switch to MM/DD:</b> This is parameter to change the parser algorithm to become <b>mm/dd/yyyy</b> instead of <b>dd/mm/yyyy</b>. Default: No<br>


Format
======
 <b>Schedule:</b> <i>( Date | Date Time | Time Date | Time)</i><br>
 <b>Date:</b> <i>Number [ / Number [ / Number ] ]</i><br>
 <b>Time:</b> <i>[ @ | + ] Number [ : Number [ : Number ] ] [ AM | PM ]</i><br>

Date is in <b>dd/mm/yyyy</b> format by default. To change into <b>mm/dd/yyyy</b>, change second parameter into <b>true</b> at <i>runPrepareSheet</i> function and select <b>Re-install</b> (all parameters will be back to default).

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
