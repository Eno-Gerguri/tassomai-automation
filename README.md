<p align="center">
  <a><img src="src/images/logo.png"</a>
  <h3 align="center">Automate your Tassomai!</h3>
  <p align="center">
    Ever bored of doing Science homework 5 days a week on Tassomai? Well... you came to the right place!
    <br />
    <br />
    <a href="https://github.com/Gloryness/tassomai-automation/issues">Report Bug</a>
    ·
    <a href="https://github.com/Gloryness/tassomai-automation/issues">Request Feature</a>
    ·
    <a href="https://github.com/Gloryness/tassomai-automation/pulls">Send a Pull Request</a>
  </p>
</p>
  
# Installation

Python 3.8+ recommended.

Install required modules which is all listed in `requirements.txt`

Clone the repo using git:
```bash
$ git clone https://github.com/Gloryness/tassomai-automation.git
```
OR:
- <a href="https://github.com/Gloryness/tassomai-automation/raw/master/exe/Tassomai%20Automation.zip">Download the .exe version</a>

# How To Use
- Enter path to geckodriver (Firefox webdriver)
- Enter Tassomai username
- Enter Tassomai password
- You can provide options such as 'Only do a maximum of X quizes' or 'Finish when daily/bonus goal complete'.
- Start Automation!
- At the end of the automation, it will provide stats such as if daily/bonus goal is complete, the time it took, amount of correct/incorrect answers and the total quizes complete.

**NOTE: Credentials are only stored to `info.json` in AppData/Local/tassomai-automation to auto-fill them in each time you run the GUI.**

# Tip
If you want... there are command line options that are available!
All you need to do is:
```bash
$ "Tassomai Automation".exe -h
  -h, --help                              Print this help message and exit
  -x EXECUTABLE, --executable=EXECUTABLE  Path to webdriver (geckodriver.exe)
  -u USERNAME, --username=USERNAME        Email for Tassomai
  -p PASSWORD, --password=PASSWORD        Tassomai Password
  --no-stats                              Do not show the stats when finished.
  --close                                 Close when finished.
  --max-quizes=NUMBER                     Maximum number of quizes to do
  --start                                 Automatically start the automation
  --gui-frameless                         Make the GUI hidden but still runs in the background.
  --frameless                             Make firefox frameless
  --no-daily                              Do not finish when daily goal is complete.
  --bonus                                 Finish when bonus goal is complete.
```
for a full list of commands.

This is very useful for running it as soon as you turn your PC on!

# How It Works
- Due to multiple attemps of unsuccessfully trying to use the `requests` libary to automate tassomai, the `selenium` libary is used instead.

1. It will enter the user's credentials, wait until the start quiz button has been found and then click on that element to start the quiz.

2. It will detect if a video has been offered and if so then click 'No thanks', this is the same with the stats part which is placed before the video.

3. Now we are at the quiz, it has to detect if we've seen this question before by reading `answers.json` in `AppData/Local/tassomai-automation`

4. If so, then loop through all boxes  (the 4 available answers), and if the processed text of the box is equal to the stored answer then we know which box it's in, therefore can use this data to click the correct box.

5. Otherwise, if the question isn't found in `answers.json` then it will call a function that answers a random box by listing all the boxes and using the `random` libary to choose one in the list to click it and return if it's correct or not.

6. If the answer was correct or not, it will call a function to find the correct answer. We do this by looping through all the boxes, and if the boxes `background-color` css property is equal to green - `rgb(201, 240, 195)`, then store `{question: answer}` in `answers.json`.

7. This is all for 1 question. It will do this X times (depending on how many sections there are in the quiz)

8. At the end of the quiz, it will grab the dictionary in `answers.json` and store it online <a href="https://github.com/Gloryness/tassomai-automation/blob/master/answers.json">here.</a>

**Currently as of 13/11/20 at 19:57 PM GMT, 1280 questions have been answered!**

# Overview
<img src="src/images/Tassomai Automation.jpg">
