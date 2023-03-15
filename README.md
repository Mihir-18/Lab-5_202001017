# Lab-5_202001017

Static Analysis of code using Static analysis tools

Github Repo used: https://github.com/qxresearch/qxresearch-event-1

File in the Repository:

1) app.py
2) jarvis.py

<h2> app.py errorneous code </h2>


    def block_websites(start_hour, end_hour):
    while True:
        if (
            dt(dt.now().year, dt.now().month, dt.now().day, start_hour)
            < dt.now()
            < dt(dt.now().year, dt.now().month, dt.now().day, end_hour)
       ):
 
	
	
<h2> app.py error snippet using mypy tool </h2>
  
  app.py:15: error: unexpected indent  [syntax]                                                                                                                        		Found 1 error in 1 file (errors prevented further checking)
  

<h2> jarivs.py errorneous code </h2>

```python
import pyttsx3  #pip install pyttsx3
import datetime  #module
import speech_recognition as sr
import wikipedia
import smtplib
import webbrowser as wb
import os  #inbuilt
import pyautogui
import psutil  #pip install psutil
import pyjokes  # pip install pyjokes
import requests, json  #inbuilt

engine = pyttsx3.init()
engine.setProperty('rate', 190)
voices = engine.getProperty('voices')
engine.setProperty('voice', voices[1].id)
engine.setProperty('volume', 1)


#change voice
def voice_change(v):
    x = int(v)
    engine.setProperty('voice', voices[x].id)
    speak("done sir")


#speak function
def speak(audio):
    engine.say(audio)
    engine.runAndWait()


#time function
def time():
    Time = datetime.datetime.now().strftime("%H:%M:%S")
    speak("The current time is")
    speak(Time)
 ``` 
  

<h2>  jarvis.py error snippet using mypy tool </h2>
	
	C:\Users\student\Downloads\qxresearch-event-1-master\qxresearch-event-1-master>mypy jarvis.py
	jarvis.py:1: error: Cannot find implementation or library stub for module named "pyttsx3"  [import]
	jarvis.py:1: note: See https://mypy.readthedocs.io/en/stable/running_mypy.html#missing-imports
	jarvis.py:3: error: Cannot find implementation or library stub for module named "speech_recognition"  [import]
	jarvis.py:4: error: Cannot find implementation or library stub for module named "wikipedia"  [import]
	jarvis.py:8: error: Library stubs not installed for "pyautogui"  [import]
	jarvis.py:8: note: Hint: "python3 -m pip install types-PyAutoGUI"
	jarvis.py:8: note: (or run "mypy --install-types" to install all missing stub packages)
	jarvis.py:9: error: Library stubs not installed for "psutil"  [import]
	jarvis.py:9: note: Hint: "python3 -m pip install types-psutil"
	jarvis.py:10: error: Cannot find implementation or library stub for module named "pyjokes"  [import]
	jarvis.py:11: error: Library stubs not installed for "requests"  [import]
	jarvis.py:11: note: Hint: "python3 -m pip install types-requests"
	Found 7 errors in 1 file (checked 1 source file)
	
	

<h2> jarvis.py error snippet using flake8 tool </h2>
	
	
	C:\Users\student\Downloads\qxresearch-event-1-master\qxresearch-event-1-master>flake8 jarvis.py
	jarvis.py:1:17: E262 inline comment should start with '# '
	jarvis.py:2:18: E262 inline comment should start with '# '
	jarvis.py:3:1: F401 'speech_recognition as sr' imported but unused
	jarvis.py:4:1: F401 'wikipedia' imported but unused
	jarvis.py:5:1: F401 'smtplib' imported but unused
	jarvis.py:6:1: F401 'webbrowser as wb' imported but unused
	jarvis.py:7:1: F401 'os' imported but unused
	jarvis.py:7:12: E262 inline comment should start with '# '
	jarvis.py:8:1: F401 'pyautogui' imported but unused
	jarvis.py:9:1: F401 'psutil' imported but unused
	jarvis.py:9:16: E262 inline comment should start with '# '
	jarvis.py:10:1: F401 'pyjokes' imported but unused
	jarvis.py:11:1: F401 'requests' imported but unused
	jarvis.py:11:1: F401 'json' imported but unused
	jarvis.py:11:16: E401 multiple imports on one line
	jarvis.py:11:24: E262 inline comment should start with '# '
	jarvis.py:20:1: E265 block comment should start with '# '
	jarvis.py:27:1: E265 block comment should start with '# '
	jarvis.py:33:1: E265 block comment should start with '# '
	jarvis.py:39:1: W391 blank line at end of file

<h2> Analysis of both tools mypy and flake8 </h2>
	
mypy

		- mypy application only shows error till then first syntax then it does no shows any existing errors.
	 	- It does not shows any error even if the variables are not declared.
		- mypy also shows error if any function is not declared in any specific code styles but ideally it should not show such errors for any specific style as a user can practice any style he prefer.

flake8
		
		- It also does not shows any error even if the variables are not declared.
		- It shows error if comment in added in same line as code but actually there should ne be any error thrown for this.
		- It also shows errors till first line of synatx error , ideally it should show all thew errors even after syntax error is detected.
		
