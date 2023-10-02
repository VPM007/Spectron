import pyttsx3  # pip install pyttsx3
import datetime
import speech_recognition as sr  # pip install SpeechRecognition
import wikipedia
import smtplib
import webbrowser as wb
import os

engine = pyttsx3.init() 


def speak(audio):
    engine.say(audio)
    engine.runAndWait()


def time():
    Time = datetime.datetime.now().strftime("%I:%M:%S")
    speak("the current time is")
    speak(Time)


def date():
    year = int(datetime.datetime.now().year)
    month = int(datetime.datetime.now().month)
    date = int(datetime.datetime.now().day)
    speak("the current date is")
    speak(date)
    speak(month)
    speak(year)


def wish():
    speak("Welcome Boss")
    time()

    date()
    hour = datetime.datetime.now().hour
    if 6 <= hour < 12:
        speak("Good Morning Boss")
    elif 12 <= hour < 18:
        speak("Good Afternoon Boss")
    elif 18 <= hour < 24:
        speak("Good Evening Boss")
    else:
        speak("Good Night Boss")

    speak("How Can I help You")


def takecommand():
    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening....")
        r.pause_threshold = 1
        audio = r.listen(source)

    try:
        print("Recognizing...")
        query = r.recognize_google(audio, language='en-in')
        print(query)

    except Exception as e:
        print(e)
        speak("Say This Again Please")
        return "None"
    return query


def sendmail(to, content):
    server = smtplib.SMTP('smtp.outlook.com', 587)
    server.ehlo()
    server.starttls()
    server.login('manoj2151999@outlook.com', 'manoj0007')
    server.sendmail('manoj2151999@outlook.com', to, content)
    server.close()


if __name__ == "__main__":
    wish()
    while True:
        query = takecommand().lower()
        if 'time' in query:
            time()
        elif 'date' in query:
            date()
        elif 'wikipedia' in query:
            speak("Searching...")
            query = query.replace("wikipedia", "")
            result = wikipedia.summary(query, sentences=2)
            print(result)
            speak(result)
        elif 'sendmail' in query:
            try:
                speak("what Should I Say.?")
                content = takecommand()
                to = 'manoj2151999@gmail.com'
                sendmail(to, content)
                speak("I am sent the mail")
            except Exception as e:
                print(e)
                speak("unable to send the mail")

        elif 'search on chrome' in query:
            speak("What can i search ?")
            chromepath = 'C:\Program Files (x86)\Google\Chrome\Application\chrome.exe'
            search = takecommand().lower()
            wb.get(chromepath).open_new_tab(search + '.com')

        elif 'who are you' in query:
            speak("i am spectron")
        elif "who created you" in query:
            speak("Mr.Manoj Kumar Google CEO")

        elif 'logout' in query:
            speak("logouting...")
            os.system("shutdown /l")

        elif 'shutdown' in query:
            speak("shutdowning...")
            os.system("shutdown /s /t l")

        elif 'restart' in query:
            speak("restarting...")
            os.system("shutdown /r /t l")

        elif 'play song' in query:
            speak("Enjoy the song Boss")
            songs_dir = 'C:\music'
            songs = os.listdir(songs_dir)
            os.startfile(os.path.join(songs_dir, songs[0]))

        elif 'offline' in query:
            speak("Bye Boss")
            quit()