# sound_to_text_mp3
import speech_recognition as sr
recognizer = sr.Recognizer()
with sr.Microphone() as source:
    recognizer.adjust_for_ambient_noise(source)
    print("Say something!")
    audio = recognizer.listen(source)
try:
    text = recognizer.recognize_google(audio)
    print("You said: " + text)
except sr.UnknownValueError:
    print("I couldn't understand what you said.")
except sr.RequestError:
    print("I couldn't connect to the Google Speech Recognition service.")
# text_to_sound
import pyttsx3
engine = pyttsx3.init()
engine.setProperty('voice', 'en-us')
engine.setProperty('rate', 150)
engine.setProperty('volume', 1.0)
engine.say('hello')
engine.save_to_file("hello", 'sound.mp3')
engine.runAndWait()
