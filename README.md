# Projeto Criptografia de Mensagem

## Descrição:

Código usado para uma atividade avaliativa da disciplina "Matemática para Computação", onde podemos fazer a conversão de uma frase(inicialmente pré-definida) usando multiplicação de matrizes

## Código:

### Criando Dicionário para fazer as conversões:

```py
tabela_alfanumérica = {
    "A":1,"B":2,"C":3,"D":4,"E":5,"F":6,"G":7,"H":8,"I":9,"J":10,"K":11,"L":12,"M":13,"N":14,"O":15,"P":"16","Q":17,"R":18,"S":19,"T":20,"U":21,"V":22,"W":23,"X":24,"Y":25
    ,"Z":26,".":27,"!":28,"#":29," ":30
}

tabela_inversa = {
    1: 'A', 2: 'B', 3: 'C', 4: 'D', 5: 'E', 6: 'F', 7: 'G',8: 'H', 9: 'I', 10: 'J', 11: 'K', 12: 'L', 13: 'M', 14: 'N', 15: 'O', 
    16: 'P', 17: 'Q', 18: 'R', 19: 'S', 20: 'T', 21: 'U', 22: 'V', 
    23: 'W', 24: 'X', 25: 'Y', 26: 'Z', 27: '.', 28: '!', 29: '#', 
    30: ' '
}
```

### Criando Matriz com a chave e a mensagem a ser codificada:

``` py
chave = [["A","Z"],["U","L"]]
chave_convertida = []

mensagem = [["Q","U","E","M","#","E","X","E","R","C","I"],
            
            ["T","A","#","A","P","R","E","N","D","E","!"]]

mensagem_criptografada = []

matrizC = []

```

### Convertendo e Mostrando Matriz Chave:

``` py
for i in range(len(chave)):
    chave_convertida.append([])
    for j in range(len(chave)):

        letra_convertida = tabela_alfanumérica[chave[i][j]]
        chave_convertida[i].append(letra_convertida)

print("Matriz Chave Convertida: ")
print()
for i in range(len(chave_convertida)):
    for j in range(len(chave_convertida)):
        print(f"[{chave_convertida[i][j]:^5}]", end = '')
    print()
print()

```
### Convertendo e mostrando matriz da mensagem
``` py
for i in range(len(mensagem)):
    mensagem_criptografada.append([])
    for j in range(len(mensagem[0])):

        letra_convertida = tabela_alfanumérica[mensagem[i][j]]
        mensagem_criptografada[i].append(letra_convertida)

for i in range(len(mensagem_criptografada)):
    for j in range(len(mensagem_criptografada[i])):
        print(f"[{mensagem_criptografada[i][j]:^5}]", end = '')
    print()
print()
```

### Multiplicação de Matrizes:

``` py
linhas_matrizC = len(chave)
colunas_matrizC = len(mensagem[0])

dimensão_comum = len(mensagem)

for i in range(linhas_matrizC):
    matrizC.append([])
    for j in range(colunas_matrizC):
        soma = 0
        for k in range(dimensão_comum):
            soma += int(chave_convertida[i][k]) * int(mensagem_criptografada[k][j])
        matrizC[i].append(soma)
    
for i in range(linhas_matrizC):
    for j in range(colunas_matrizC):
        print(f"[{matrizC[i][j]:^5}]",end ='')
    print()
print()
```

### Mostra a nova matriz converttida, ou seja, a frase codificada:

``` py
frase_descriptografada = []

for i in range(len(matrizC)):
    frase_descriptografada.append([])
    for j in range(len(matrizC[0])):
        if matrizC[i][j] > 30:
            letra_convertida = tabela_inversa[matrizC[i][j]%30]
            frase_descriptografada[i].append([letra_convertida])
        else:
            letra_convertida = tabela_inversa[matrizC[i][j]]
            frase_descriptografada[i].append(letra_convertida)
        
for i in range(len(frase_descriptografada)):
    for j in range(len(frase_descriptografada[0])):
        print(f"{frase_descriptografada[i][j]}",end = '')
    print()

``` 

## Considerações Finais: 
Aindad ficou faltando a parte de descriptgrafar para a mensagem original, mas no geral foi um exercício um pouco desafiador mas ao mesmo tempo interessante, principalmente pois temos que aplicar a lógica matemática para o código.
