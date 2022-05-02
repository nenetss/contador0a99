###contador0a99
contador de 0 a 99 usando ESP32 em mikropython com o display de 7 segmentos

from machine import Pin
from time import sleep

#Definir a função de cada pino que for usado

segmentoA = Pin(32, Pin.OUT)
segmentoB = Pin(33, Pin.OUT)
segmentoC = Pin(25, Pin.OUT)
segmentoD = Pin(26, Pin.OUT)
segmentoE = Pin(27, Pin.OUT)
segmentoF = Pin(14, Pin.OUT)
segmentoG = Pin(12, Pin.OUT)

display1   = Pin(23, Pin.OUT)
display2   = Pin(22, Pin.OUT)

zerar     = Pin(34, Pin.IN)
sensor    = Pin(35, Pin.IN)

#Inicializar as variáveis

def unidade(num):
  segmentoA.value(digito[num][7])
  segmentoB.value(digito[num][6])
  segmentoC.value(digito[num][5])
  segmentoD.value(digito[num][4])
  segmentoE.value(digito[num][3])
  segmentoF.value(digito[num][2])
  segmentoG.value(digito[num][1])

def dezena(num2):
  segmentoA.value(digito[num2][7])
  segmentoB.value(digito[num2][6])
  segmentoC.value(digito[num2][5])
  segmentoD.value(digito[num2][4])
  segmentoE.value(digito[num2][3])
  segmentoF.value(digito[num2][2])
  segmentoG.value(digito[num2][1])




contador = 0   


digito = [[0,0,1,1,1,1,1,1],  # Número 0 
         [0,0,0,0,0,1,1,0],           # Número 1
         [0,1,0,1,1,0,1,1],           # Número 2
         [0,1,0,0,1,1,1,1],           # Número 3
         [0,1,1,0,0,1,1,0],           # 4
         [0,1,1,0,1,1,0,1],           # 5
         [0,1,1,1,1,1,0,1],           # 6
         [0,0,0,0,0,1,1,1],           # 7
         [0,1,1,1,1,1,1,1],           # 8
         [0,1,1,0,0,1,1,1]]           # 9

quociente = 0
resto = 0

#Agora vamos montar o programa principal
#O objetivo é criar um contador de peças

while(True):
  if(sensor.value() == 0 and contador < 99):
    contador = contador + 1
    while(sensor.value() == 0):
      {}
    print(contador)
  elif(zerar.value() == 0):
    contador = 0
    
  display1.value(1)
  display2.value(1)

  unidade(quociente)

  display2.value(0)
  sleep(0.01)

  display2.value(1)
 
  dezena(resto)
  display1.value(0)
  
 

  quociente = contador % 10
  resto = contador // 10
  
  
  https://wokwi.com/projects/330186173403103826


