###contador0a99
contador de 0 a 99 usando ESP32 em mikropython com o display de 7 segmentos

#Importar as bibliotecas de definições do pinos e biblioteca do tempo


from *machine* import Pin
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

contador = 0    # Contador de peças (0 até 9)
contador2 = 0

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
    
  segmentoA.value(digito[quociente][7])
  segmentoB.value(digito[quociente][6])
  segmentoC.value(digito[quociente][5])
  segmentoD.value(digito[quociente][4])
  segmentoE.value(digito[quociente][3])
  segmentoF.value(digito[quociente][2])
  segmentoG.value(digito[quociente][1])
  display2.value(0)
  sleep(0.01)
  display1.value(1)
  sleep(0.01)
  display2.value(1)
  segmentoA.value(digito[resto][7])
  segmentoB.value(digito[resto][6])
  segmentoC.value(digito[resto][5])
  segmentoD.value(digito[resto][4])
  segmentoE.value(digito[resto][3])
  segmentoF.value(digito[resto][2])
  segmentoG.value(digito[resto][1])
  display1.value(0)
  sleep(0.01)
  display1.value(1)

  

  quociente = contador % 10
  resto = contador // 10


