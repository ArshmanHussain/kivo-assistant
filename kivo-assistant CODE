import speech_recognition as sr
import webbrowser
import pyttsx3
import pywhatkit 


recognizer = sr.Recognizer()
engine = pyttsx3.init()

# Optional: Set voice and speaking rate
voices = engine.getProperty('voices')
engine.setProperty('voice', voices[0].id)  # Change index if needed
engine.setProperty('rate', 180)

music_folder = "C:/Users/YourName/Music"

def speak(text):
    engine.say(text)
    engine.runAndWait()

def processcommand(c):
  if "open google" in c.lower():
    webbrowser.open('https://google.com')
    speak("Opening Google")
  elif "open facebook" in c.lower():
    webbrowser.open('https://facebook.com')
    speak("Opening facebook")
  elif  "open youtube" in c.lower():
    webbrowser.open('https://youtube.com')
    speak("Opening youtube")
  elif  "open vscode" in c.lower():
    webbrowser.open('https://code.visualstudio.com/')
    speak("Opening VS code")
  elif "play song" in c.lower():
      song_name = c.replace("play song", "",).strip() 
      #song_name = c.replace("play song", "pal pal",).strip()
      #song_name = c.replace("play song", "jhol",).strip()
      if song_name:
            speak(f"Playing {song_name} on YouTube")
            pywhatkit.playonyt(song_name)
  else:
    speak('sorry I did not understand the command')

    
if __name__=="__main__":  
    speak('initializing kivo...')

    while True:
     # listen for the wake up word 'kivo'
     # obtain audio for the microphone

     #r= sr.Recognizer()
    
     # it recognize speech using google
     print('recognizing...')
     try:
        with sr.Microphone() as source:
         print("Listening...")
         audio = recognizer.listen(source, timeout=10, phrase_time_limit=5)
        
        word= recognizer.recognize_google(audio)
        print(f"Heard: {word}")
        if 'kivo' in word.lower():
           speak("yes sir")
           print("kivo is active now")
           # listen for command
           with sr.Microphone() as source:
            audio = recognizer.listen(source)
            command=recognizer.recognize_google(audio)
            processcommand(command)


     except sr.WaitTimeoutError:
            print("Listening timed out.")
     except sr.UnknownValueError:
            print("Sorry, I didn't catch that.")
     except sr.RequestError as e:
            print(f"Could not request results from Google; {e}")
     except Exception as e:
          print(f"An error occurred: {e}")
