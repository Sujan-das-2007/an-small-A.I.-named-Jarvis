# an-small-A.I.-named-Jarvis
The name of this ai is Jarvis.I am a 14 year old boy from Kolkata(India). I have just started to code a few months ago. I was inspired by CodeWithHarry(youtuber) & Tony Stark(a fictional character). So, I created this. any suggestion will be appreciated. 
code:::::
import pyttsx3 #pip install pyttsx3
import speech_recognition as sr #pip install speechRecognition
import datetime
from gpiozero import CPUTemperature
import wikipedia #pip install wikipedia  
import psutil
import webbrowser
import time
import requests, json
import random
import os
import pyautogui
# import wave
import smtplib
# import subprocess
#from pygame import mixer


engine = pyttsx3.init('sapi5')
voices = engine.getProperty('voices')
# print(voices[1].id)
engine.setProperty('voice', voices[0].id) # voices[0]->for david.. voices[1]->for ZIRA

def creator():
    first_name="Sujan"
    last_name="Das"


def speak(audio):
    engine.say(audio)
    engine.runAndWait()



def wishMe():
    hour = int(datetime.datetime.now().hour)
    if hour>=0 and hour<12:
        speak("Good Morning!")

    elif hour>=12 and hour<18:
        speak("Good Afternoon!")   

    else:
        speak("Good Evening!")  

    speak("I am Jarvis at your service Boss. ")  
def wishMe2():
    speak("hello Sujan")      

def takeCommand():
    #It takes microphone input from the user and returns string output
            # r= raw_input()

    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        r.pause_threshold = 1.5
        audio = r.listen(source)

    try:
        print("Recognizing...")    
        query = r.recognize_google(audio, language='en-in')
        print(f"Boss said: {query}\n")
        speak('Sure ')

    except sr.UnknownValueError:
        # print(e)    
        print("Say that again please...")  
        return "None"
    return query

def sendEmail(to, content):
    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.ehlo()
    server.starttls()
    server.login('yourE-mail@gmail.com', 'app specific key')
    server.sendmail('yourE-mail@gmail.com', to, content)
    server.close()

if __name__ == "__main__":
    r1=random.randint(1,2)
    if r1==1:
      wishMe()
    else :
      wishMe2() 
    while True:
    # if 1:
            
        pass_Key = "sujan2007"
        query = takeCommand()
        #.lower()
        # Logic for executing tasks based on query
        if 'wikipedia' in query:
            speak('Searching Wikipedia...')
            query = query.replace("wikipedia", "")
            results = wikipedia.summary(query, sentences=2)
            speak("According to Wikipedia")
            print(results)
            speak(results)
        
        elif "how are you" in query:
            if psutil.virtual_memory.percent() <= 50 & psutil.cpu_percent() <= 60:
                speak("I am completly good")
            elif (
                psutil.virtual_memory.percent()
                >= 51 & psutil.virtual_memory.percent()
                <= 70 & psutil.cpu_percent()
                >= 61
            ):
                speak(
                    f"I am well but there is a bit issue with my memory{psutil.virtual_memory()}{psutil.cpu_percent()}"
                )
        elif 'diagnostic' in query:
              speak("sure but pass key first ",)
              inpt=input() 
              if inpt==pass_Key:
                speak(psutil.virtual_memory())
                speak(psutil.cpu_percent())    

        # elif 'how are you' in query:
        #     speak("I am fine.")
        elif 'open youtube' in query:
            webbrowser.open("https://www.youtube.com/")
        elif 'open Youtube' in query:
            webbrowser.open("https://www.youtube.com/")

        elif 'open google' in query:
            webbrowser.open("https://www.google.com/")
        elif 'open Google' in query:
            webbrowser.open("https://www.google.com/")

        elif 'open stackoverflow' in query:
            webbrowser.open("https://stackoverflow.com/")   
        elif 'open Stackoverflow' in query:
            webbrowser.open("https://stackoverflow.com/")   

        elif 'search' in query:
            speak("what are the key words")
            keyWords=takeCommand()
            webbrowser.open(f"https://www.google.com/search?q={keyWords}&oq={keyWords}&aqs=chrome.0.69i59j69i60.4247j0j1&sourceid=chrome&ie=UTF-8")

        elif 'music' in query:
            webbrowser.open("link....")

        elif 'text' in query:
          try:
           speak("whom should i text??")
           whom=takeCommand()
           speak("what should i say")
           message=takeCommand()
        #    break_out=takeCommand()
           if 'cancel' in whom:
               continue
           elif 'cancel' in message:
               continue 
           elif 'default' in whom:
               whom="S Das" 
           pyautogui.hotkey('win')
           pyautogui.write('WhatsApp Desktop')   
           pyautogui.hotkey('enter',interval=5)  
        #    time.sleep(10)
           pyautogui.hotkey('ctrl','f')
           pyautogui.write(whom)
           pyautogui.hotkey('enter')  
           pyautogui.write(message)
           pyautogui.hotkey('enter')
          except Exception as excper:
               speak('sorry unable to do this at this time. Exception is',excper)
 
        elif 'next' in query:
            pyautogui.hotkey('alt','tab')
            pyautogui.hotkey('shift','n')  
            pyautogui.hotkey('alt','tab')                        
        elif 'the time' in query:
            strTime = datetime.datetime.now().strftime("%H:%M:%S")    
            speak(f"Sir, the time is {strTime}")

        elif 'open code' in query:
            speak("may i know the pass key")
            passKey=input()
            passKey_trimmed=passKey.replace(" ","")
            if pass_Key==passKey:
               codePath = "C:\\Users\\Sujan Das\\Desktop\\jarvis\\Edith.py"
               os.startfile(codePath)
            else:
                speak("sorry but i don't have the permission to show u the code unless u say the right pass key")
                exit()

        elif 'temperature' in query:
            webbrowser.open("https://www.google.com/search?q=whether+conditions+near+me&oq=whether+conditions+near+me&aqs=chrome..69i57.20255j0j1&sourceid=chrome&ie=UTF-8")  

        elif 'jarvis are you there' in query:  #just for fun
            speak("Always at your service boss")    

        elif 'are you there' in query: #just for fun
            speak("always at your service boss")    
        elif 'jarvis are you in' in query:    #just for fun
            speak("yep") 
        elif 'are you in' in query:    #just for fun
            speak("yo! to help you") 
        
        elif 'jarvis exit' in query:
            exit()
        elif 'Jarvis exit' in query:
            exit()
        elif 'J exit' in query:
            exit()
        elif 'j exit' in query:
            exit()
        elif 'email name' in query:
            try:
                speak("What should I say?")
                content = takeCommand()
                to = "whom-u-want-to-send@gmail.com"    
                sendEmail(to, content)
                speak("Email has been sent!")
            except Exception as e:
                print(e)
                speak("Sorry sir. I am not able to send this email") 
