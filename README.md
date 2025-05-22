# Tony_Guider.py
I have made my first project which is a bot called Tony which can provide you sites as well as songs (only some for now). I have also added newsAPI which will give you the latest news going around at that time.  All thanks to CodewithHarry to help me with making this project. I have made it as simple as possible. Hope you like it.
# I want to thank CodewithHarry to make me understand  this project and help me write this code.
# This is the project "Tim Guider" which will provide you with all the things as asked such as opening sites and songs(few are included in this project). 
# I couldn't make a function which included songs only which when asked can from the musicLibrary(which I had created) because of some code issue.
# I have included news which i created using API Key.
# I could have also added OpenAI(using the API abd pip) but I didn't because I wanted to keep it simple at start.
#Including OpenAI can make him (Tim) ask anything and he'll tell everything related to the topic asked.It will be like asking the same thing to google
import speech_recognition as sr # My API Key for news related == 0469742f7ef04b338b69dfa9d32b20fc
import webbrowser
import pyttsx3
import requests
# import musicLibrary
recognizer = sr.Recognizer()
engine = pyttsx3.init()
newsapi = "0469742f7ef04b338b69dfa9d32b20fc"

def speak(text):
    engine.say(text)
    engine.runAndWait()

def processcommand(c): # I have included both-sites as well as some songs
    c = c.lower()
    #sites
    if "open google" in c:
        webbrowser.open("https://www.google.com")
    elif "open groww" in c:
        webbrowser.open("https://groww.com")
    elif "open angelone" in c:
        webbrowser.open("https://angelone.com")
    elif "open x" in c:
        webbrowser.open("https://x.com")
    elif "open instagram" in c:
        webbrowser.open("https://instagram.com")
    elif "open facebook" in c:
        webbrowser.open("https://facebook.com")
    elif "open youtube" in c:
        webbrowser.open("https://youtube.com")
    elif "open news" in c:                           # I have used both news open from the browser as well as the API Key one.  
        webbrowser.open("https://news.com")          # you this as a secondary source.
    elif "open stock market" in c:
        webbrowser.open("https://www.moneycontrol.com")
        #songs
    elif "play sunflower" in c:
        webbrowser.open("https://youtu.be/ApXoWvfEYVU?si=xPmzkHWENfTafMGR")
    elif "play skylines"in c:
      webbrowser.open("https://youtu.be/rkUm3-4J2m4?si=U1_LfAUautGJsKhM",)  
    elif "play logic" in c:
        webbrowser.open("https://youtu.be/cycUHgg0zzU?si=7FxoBa-8BPkmTsu_") 
    elif "play lonley road" in c:
        webbrowser.open("https://youtu.be/b6-JNeXxN3s?si=mLU6WFxeGtubIq6E") 
    elif "play circles" in c:
        webbrowser.open("https://youtu.be/wXhTHyIgQ_U?si=T0BpjFNfp9PkC1xL") 
    elif "news" in c:
        r = requests.get("https://newsapi.org/v2/everything?q=keyword&apiKey=0469742f7ef04b338b69dfa9d32b20fc")
    
    if r.status_code == 200: # this code I have taken from chatgpt.
        data = r.json()
        articles = data.get("articles", [])
        for i, article in enumerate(articles, 1):
            print(f"{i}. {article['title']}")
    else:
        print("Failed to fetch news:", r.status_code)

# other related code which i have written.... which can be used.
    # else:
        # speak("I couldn't understand what you said")   # Exeception
    
    # elif "open chatgpt" in c:
    #     webbrowser.open("https://chat.openai.com")    
    # elif c.startswith("play"):
    #      parts = c.split(" ", 1)
    # if len(parts) > 1:
    #     song = parts[1].strip()
    #     link = musicLibrary.music.get(song)
    #     if link:
    #         webbrowser.open(link)
    #     else:
    #         speak("Song not found.")
    # else:
    #     speak("Please specify a song name.")

if __name__ == "__main__":
    name = input("Please enter your full name: ")
    speak(f"Hello,{name} welcome to Tim guider")
    
    speak("Initializing Tim...")
    recognizer = sr.Recognizer()

    while True:
        try:
            with sr.Microphone() as source:
                print("Ask Something...")
                audio = recognizer.listen(source, timeout=5)
                print("Recognizing...")
                command = recognizer.recognize_google(audio)
                print(f"You said: {command}")

                if "exit" in command.lower():
                    speak("Goodbye!")
                    break
           
            processcommand(command)

        except sr.WaitTimeoutError:
            print("Listening timed out while waiting for phrase.")
        except sr.UnknownValueError:
            print("Sorry, I couldn't understand the audio.")
        except sr.RequestError as e:
            print(f"Could not request results from Google Speech Recognition service; {e}")
        except Exception as e:
            print(f"An error occurred: {e}")

# elif c.startswith("play"):#and len(c.split()) > 1:
        # song = c.lower().split(" ")[1]
        # link = musicLibrary.music[song]
        # webbrowser.open(link) #if link else speak("Song not found.")

# else:
#        speak("Please say the song name after 'play'.")

#     elif c.lower().startswith("play"):
#         song = c.lower().split(" ")[1] # this will for example take the first song from the file which we have placed music and then it will lower the song name and then will split both the 'play' and the 'song' anf then take the first one i.e the song 
#         link = musicLibrary.music(song)
#         webbrowser.open(link)
#     else:
#        speak("Sorry, I didn't understand the command.")

# gender = input("Please enter your gender: ")#strip().lower()

    # if gender == 'female':
    #     speak(f"Hello, {name}, welcome to the Tim Assistant.")
    # else:
    #     speak(f"Hello,{name}, welcome to the Tim Assistant.")

#  with sr.Microphone() as source:
#                  print("Ask Something...")
#                 audio = recognizer.listen(source, timeout=5)
#                 print("Recognizing...")
#                 command = recognizer.recognize_google(audio)
#             # if (command.lower() =="Tim"): if you want to say his name the use this command 
#                 # print("Yes")
#             #ith sr.Microphone() as source:
#                 # print("Ask Something...")
#             # audio = recognizer.listen(source)
#             #command = recognizer.recognize_google(audio) and then ask something     
#                 print(f"You said: {command}")

#                 if "exit" in command.lower():
#                     speak("Goodbye!")
#                     break
