<p align="center">
  <a><img src="src/images/logo.png"</a>
  <h3 align="center">Automate your Tassomai homework!</h3>
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
  
# How To Use
- Enter path to geckodriver (Firefox webdriver)
- Enter Tassomai username
- Enter Tassomai password
- You can provide options such as 'Only do a maximum of X quizes' or 'Finish when daily/bonus goal complete'.
- Start Automation!

# How It Works
- Due to multiple attemps of unsuccessfully trying to use the `requests` libary to automate tassomai, the `selenium` libary is used instead.
1. It will enter the user's credentials, wait until the start quiz button has been found and then click on that element to start the quiz.
2. It will detect if a video has been offered and if so then click 'No thanks', this is the same with the stats part which is placed before the video.
3. Now we are at the quiz, it has to detect if we've seen this question before by reading `answers.json` in `AppData/Local/tassomai-automation`
4. If so, then loop through all boxes, and if the processed text of the box is equal to the stored answer then we know which box it's in, therefore can use this data to click the correct box.
