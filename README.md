#codigos-del-TIF
#programa de metodo de montecarlo en integrales definidas y tres en raya 
%matplotlib inline
from scipy import random
import numpy as np
import matplotlib.pyplot as plt
a=0
b=np.pi
N=(1000)
integral=0.0
def func(x):
    return np.sin(x)
answer = (b-a)/float(N)*integral 
areas= []
for i in range(N):
    xrand= np.zeros(N)
    for i in range(len(xrand)):
        xrand[i]= random.uniform(a,b)
        integral= 0.0
    for i in range(N):
        integral += func(xrand[i])
    answer= (b-a)/float(N)*integral
    areas.append(answer)
plt.title("Distribucion de las áreas calculadas")
plt.hist(areas, bins =20, ec='black')
plt.xlabel("Areas")








#Programa de 3 en raya 

import time
import random
import os
def inicio_juego():
    print("****BIENVENIDO****")
    time.sleep(1)
    while True:
        ficha = input("Seleccione ficha: X / O\n")
        ficha = ficha.upper()
        if ficha=="X":
            humano="X"
            ordenador="O"
            break
        elif ficha=="O":
            humano="O"
            ordenador="X"
            break
        else:
          print("Por favor introduce una ficha posible. ")
    return(humano,ordenador)      
#Creacion del Tablero 

def tablero():
  print("tres en raya / TIC TAC TOE")
  print()
  print("        |        |        ")
  print("1   {}   |2   {}   |3   {}       ".format(matriz[0],matriz[1],matriz[2]))
  print("        |        |        ")

  print("        |        |        ")
  print("4   {}   |5   {}   |6   {}       ".format(matriz[3],matriz[4],matriz[5]))
  print("        |        |        ")

  print("        |        |        ")
  print("7   {}   |8   {}   |9   {}       ".format(matriz[6],matriz[7],matriz[8]))
  print("        |        |        ")



def empate (matriz):
  empate=True
  i=0
  while (empate==True and i<9):
    if matriz[i]==" ":
        empate=False 
    i=i+1
  return empate

def victoria(matriz):
    if  (matriz[0]==matriz[1]==matriz[2]!=" " or matriz[3]==matriz[4]==matriz[5]!=" " or matriz[6]==matriz[7]==matriz[8]!=" " or
        matriz[0]==matriz[3]==matriz[6]!=" " or matriz[1]==matriz[4]==matriz[7]!=" " or matriz[2]==matriz[5]==matriz[8]!=" " or
        matriz[0]==matriz[4]==matriz[8]!=" " or matriz[2]==matriz[4]==matriz[6]!=" "):
        return True 
    else:
        return False

def movimiento_jugador():
    while True: 
        posiciones=[0,1,2,3,4,5,6,7,8]
        casilla=int(input("Seleccione una casilla: "))
        if casilla not in posiciones:
            print("Casilla no disponible")
        else:
            if matriz[casilla-1]==" ":
                matriz [casilla-1]=humano
                break
            else:
                print("Casilla no disponible")

def movimiento_ordenador():
    posiciones=[0,1,2,3,4,5,6,7,8]
    casilla=9
    parar=False

    for i in posiciones:
        copia=list(matriz)
        if copia[i]==" ":
            copia[i]=ordenador
            if victoria(copia)==True:
                casilla=i
    if casilla==9: 
        for j in posiciones:
            if copia[j]==" ":
              copia[j]=humano
              if victoria(copia)==True:
                  casilla=j
    if casilla==9:
        while(not parar):
            casilla=random.randint(0,8)
            if matriz[casilla]==" ":
                parar=True
    matriz[casilla]=ordenador

while True:
    matriz= [" "]*9
    os.system("cls") #limpiar pantalla al comienzo de cada partida
    humano,ordenador=inicio_juego()
    partida=True
    ganador=0

    while partida:
        ganador=ganador+1
        os.system("cls")
        tablero()

        if victoria(matriz):
            if ganador%2==0:
                print("**Gana el jugador**")
                print("**Fin del juego**")
                print("\n Reiniciando... ")
                time.sleep(5)
                partida=False
            else:
                print("**Gana el ordenador**")
                print("**Fin del juego**")
                print("\n Reiniciando... ")
                time.sleep(5)
                partida=False
        elif empate(matriz):
            print("**Empate**")
            print("**Fin del juego**")
            print("\n Reiniciando... ")
            time.sleep(5)
            partida=False
        elif ganador%2==0:
            print("El ordenador esta pensando")
            time.sleep(3)
            movimiento_ordenador()
        else:
            movimiento_jugador()


















