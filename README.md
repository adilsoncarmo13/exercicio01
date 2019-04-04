
## Exercícios

1. Uma empresa quer transmitir dados pelo telefone, mas está preocupada com a interceptação telefônica. Todos os seus dados são transmitidos  como inteiros de quatro dígitos. Ela pediu para que você escreva um programa que criptografe seus dados, para que eles possam ser transmitidos com mais segurança. Seu aplicativo deve ler um inteiro de quatro dígitos fornecidos pelo usuário e criptografá-lo da seguinte forma: substitua cada dígitos por (a soma desse dígitos mais 7) módulo 10. Em seguida, troque o primeiro dígito pelo terceiro e troque o segundo dígito pelo quarto e imprima o inteiro criptografado.


```python
numero = int(input('Numero: '))

digito4 = int(((numero % 10) + 7) % 10)
digito3 = int((((numero % 100) / 10) + 7) % 10)
digito2 = int((((numero % 1000) / 100) + 7) % 10)
digito1 = int((((numero % 10000) / 1000) + 7) % 10)

print(str(digito3) + str(digito4) + str(digito1) + str(digito2))

```

    Numero: 1234
    0189


2. Implemente a função par que retorna verdadeiro se um número inteiro passado como parâmetro for par ou falso caso ele seja ímpar. Teste seu programa chamando a função para verificar os números de 0 à 10.


```python
def par(numero):
    if numero % 2 == 0:
        return("Verdadeiro")
    else:
        return("Falso")
    
for i in range(11):
    print(str(i) + ' é par? ' + par(i))
```

    0 é par? Verdadeiro
    1 é par? Falso
    2 é par? Verdadeiro
    3 é par? Falso
    4 é par? Verdadeiro
    5 é par? Falso
    6 é par? Verdadeiro
    7 é par? Falso
    8 é par? Verdadeiro
    9 é par? Falso
    10 é par? Verdadeiro


3. Escreva um programa que leia 3 números inteiros referente ao comprimento dos lados de um triângulo e classifique como: triângulo equilátero, isósceles ou escaleno.


```python
lado1 = int(input('Lado1: '))
lado2 = int(input('Lado2: '))
lado3 = int(input('Lado3: '))

triangulo = True
lado12 = lado1 + lado2
lado13 = lado1 + lado3
lado23 = lado2 + lado3

if lado12 <= lado3:
    triangulo = False
elif lado13 <= lado2:
    triangulo = False
elif lado23 <= lado1:
    triangulo = False
if(triangulo):
    if (lado1 == lado2 and lado2 == lado3):
        print('Triângulo Equilátero')
    elif (((lado1 == lado2) and (lado2 != lado3))):
        print ('Triângulo Isósceles')
    elif (((lado1 == lado3) and (lado3 != lado2))):
        print ('Triângulo Isósceles')
    elif (((lado2 == lado3) and (lado3 != lado1))):
        print ('Triângulo Isósceles')
    else:
        print ('Triângulo Escaleno')
else:
    print('Essas medidas não podem ser de um triângulo.')
```

    Lado1: 3
    Lado2: 4
    Lado3: 5
    Triângulo Escaleno


4. Escreva um programa que aceita um número como entrada e insere hífens (-) entre dois números pares. Por exemplo, se receber o número 02368859 como entrada, a saída do programa deverá ser: 0-236-8-859.


```python
numero = input('Numero: ')
lista_numero = list(numero)
quant_num = len(lista_numero)
temp = ''

for i in range(quant_num):
    if(int(lista_numero[i]) % 2 == 0 and int(lista_numero[i+1]) % 2 == 0):
        temp += str(lista_numero[i]) + '-'
    else:
        temp += str(lista_numero[i])

print(temp)
```

    Numero: 02368859
    0-236-8-859


5. Escreva um programa que encontre o item mais frequente de um vetor. Exemplo: [2, 7, 7, 7, ‘#’, ‘#’, ‘#’, ‘@’, 3, ‘#’, 6]  // Saída: # aparece 4 vezes


```python
itens = input('Itens: ')
lista_itens = list(itens)
pos_maior = int(0)
quant_maior = int(0)

for i in range(len(lista_itens)):
    if lista_itens.count(lista_itens[i]) > quant_maior:
        quant_maior = lista_itens.count(lista_itens[i])
        pos_maior = i

print(lista_itens[pos_maior] + ' aparece ' + str(quant_maior) + ' vezes.')
```

    Itens: 2777###@3#6
    # aparece 4 vezes.


6. Um número de Armstrong de 3 dígitos é um inteiro pelo qual a soma dos cubos dos seus dígitos é igual ao seu número. Por exemplo: o número inteiro 371 é um número de Armstrong, porque 3³ + 7³ + 1³ = 371. Escreva um programa que verifique se um número de 3 dígitos fornecido como entrada é um número de Armstrong.


```python
numero = input('Numero: ')
lista_numero = list(numero)
quant_num = len(lista_numero)
multiplica = int(lista_numero[0])**3 + int(lista_numero[1])**3 + int(lista_numero[2])**3

if int(multiplica) == int(numero):
    print(numero + ' é um número de Armstrong')
else:
    print(numero + ' não é um número de Armstrong')

```

    Numero: 371
    371 é um número de Armstrong


7. Escreva uma função ue receba uma string e conte o número de vogais dentro dela, por exemplo: entrada: ‘Ciência de Dados’, saída: 7 vogais


```python
def contar(nome):
    conta_a = nome.count('a') + nome.count('á') + nome.count('à') + nome.count('ã') + nome.count('â')
    conta_e = nome.count('e') + nome.count('é') + nome.count('è') + nome.count('ê')
    conta_i = nome.count('i') + nome.count('ì') + nome.count('í') + nome.count('î')
    conta_o = nome.count('o') + nome.count('ó') + nome.count('ò') + nome.count('õ') + nome.count('ô')
    conta_u = nome.count('u') + nome.count('ú') + nome.count('ù') + nome.count('û')
    return(str(conta_a + conta_e + conta_i + conta_o + conta_u) + ' vogais')

nome = input('Nome: ')
print(contar(nome))
```

    Nome: Ciência de Dados
    7 vogais


8. Implemente em Python o algoritmo de Busca Binária


```python
numeros = [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25]

def busca(vetor, numero):
    achou = 'false'
    esquerda = 0
    meio = 0
    direita = len(vetor)
    while(achou != 'true'):
        meio = (direita + esquerda) // 2
        if numero == vetor[meio]:
            buscar = meio
            achou = 'true'
        elif numero > vetor[meio]:
            esquerda = meio
            buscar = meio
        else:
            direita = meio
            buscar = meio
    return meio

numero = int(input('Numero: '))
buscar = busca(numeros, numero)
print('O número ' + str(numero) + ' está na posição ' + str(buscar) + ' do vetor')
```

    Numero: 13
    O número 13 está na posição 13 do vetor


9. Escreva uma função que receba algum valor como parâmetro e retorne seu tipo


```python
def tipo(valor):
    return(type(valor))

inteiro = 1
texto = 'teste'
decimal = 3.14
logico = True
lista = [1,2,3,4]
tupla = (1,2,3,4)
set = {1,2,3,4}

print(str(inteiro) + ' é um ' + str(tipo(inteiro)))
print(str(texto) + ' é um ' + str(tipo(texto)))
print(str(decimal) + ' é um ' + str(tipo(decimal)))
print(str(logico) + ' é um ' + str(tipo(logico)))
print(str(lista) + ' é um ' + str(tipo(lista)))
print(str(tupla) + ' é um ' + str(tipo(tupla)))
print(str(set) + ' é um ' + str(tipo(set)))
```

    1 é um <class 'int'>
    teste é um <class 'str'>
    3.14 é um <class 'float'>
    True é um <class 'bool'>
    [1, 2, 3, 4] é um <class 'list'>
    (1, 2, 3, 4) é um <class 'tuple'>
    {1, 2, 3, 4} é um <class 'set'>


10. Escreva uma função que receba um lista numérica como parâmetro e retorne os segundos maiores e menores números da sequência, por exemplo: entrada [1, 2, 3, 4, 5, 6, 7, 8, 9], saída [2, 8].


```python
def contar (lista):
    sorted(lista)
    lista.remove(max(int(numero) for numero in lista))
    lista.remove(min(int(numero) for numero in lista))
        
    
    return [lista[0], lista[len(lista)-1]]

lista = [1, 2, 3, 4, 5, 6, 7, 8, 9]
conta = contar(lista)
print(conta)
```

    [2, 8]


11.  Escreva uma função que receba um número inteiro como entrada (px.: 32243) e retorne o número invertido (px.: 34223).


```python
numero = input('Numero: ')
lista_numero = list(numero)
inverso = ''

for i in range((len(lista_numero) - 1), -1, -1):
    inverso += lista_numero[i]
    
print(inverso)
```

    Numero: 12345
    54321
