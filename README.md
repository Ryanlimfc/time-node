# time-node

#import modules
import os
os.chdir('/home/pi/Desktop/lcd')
import lcd
lcd.lcd_init()
import time

def timer():
    millisecond=0
    second = 0
    minute = 0
    hour = 0
    display = ''

#while running, if the milliseconds reach 10 then seconds tick over to 1
#if the seconds reach 60 then the minutes tick over to 1 etc.
# all runs within a loop while true
while True:
    millisecond +=1
    if millisecond ==9:
        millisecond = 0
    second = second + 1
    if second==59:
        second = 0
    minute = minute + 1
    if minute == 59:
        minute=0
    hour = hour + 1

#calls on the function and the while loop by arranging the variables in a tuple
#displaying that tuple with the python join function, allowing a mixture of text and variables within one string
tup = " ", hour,":", minute, ":", second, ":", millisecond
display = ''.join(map(str, tup))
lcd.lcd_string(display,2)
time.sleep(0.099)

