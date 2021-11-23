# Como combinar dados de múltiplas tabelas?

Para este tutorial, usaremos as seguintes tabelas de exemplos:



**Pokemons do tipo Inseto**

```python
bugs = pd.read_csv("data/pkx_bug.csv")

"""
	  Per	Nat  	   Pokemon    HP ... Hoe	Sin		Un		Pokemon.1
0	  10.0	 10.0	  Caterpie  45.0 ... 10.0	10.0	24.0	Caterpie
1	  11.0	 11.0	   Metapod  50.0 ... 11.0	11.0	25.0	Metapod
2	  12.0	 12.0	Butterfree	60.0 ... 12.0	12.0	26.0	Butterfree
3	  13.0	 13.0	    Weedle	40.0 ... 13.0	13.0	27.0	Weedle
4	  14.0	 14.0	    Kakuna	45.0 ... 14.0	14.0	28.0	Kakuna
5	  15.0	 15.0	  Beedrill	65.0 ... 15.0	15.0	29.0	Beedrill
"""
```



**Pokemons do tipo Veneno**

```python
poisons = pd.read_csv("data/pkx_poison.csv")

"""
	Per		Nat		Pokemon		  HP ... Hoe	Sin		Un		Pokemon.1	
0	30.0	29.0	Nidoran ♀	55.0 ... 30.0	29.0	95.0	Nidoran ♀
1	31.0	30.0	Nidorina	70.0 ... 31.0	30.0	96.0	Nidorina
2	32.0	31.0	Nidoqueen	90.0 ... 32.0	31.0	97.0	Nidoqueen
3	33.0	32.0	Nidoran ♂	46.0 ... 33.0	32.0	98.0	Nidoran ♂
4	34.0	33.0	Nidorino	61.0 ... 34.0	33.0	99.0	Nidorino
5	35.0	34.0	Nidoking	81.0 ... 35.0	34.0	100.0	Nidoking
"""
```



## Concatenando objetos

![concatenando objetos](../assets/concat-row.svg)

Note que duas tabelas que possuem uma estrutura similar se tornaram uma única tabela.



```python
print('O formato da tabela Insetos: ', bugs.shape)
# O formato da tabela Insetos: (500, 35)

print('O formato da tabela Venenosos: ', poisons.shape)
# O formato da tabela Venenosos: (487, 35)

poison_bug = pd.concat([poisions, bugs], axis=0)
print('O formato das duas tabelas concatenadas: ', poison_bug.shape)
# O formato das duas tabelas concatenadas: (987, 35)
```

A função `concat()` realiza a concatenação de várias tabelas ao longo de um dos axis (linha ou coluna).

Percebe-se que a tabela resultante possui 987 (500 + 487) linhas.



## Unindo tabelas usando um identificador comum

![unindo tabelas usando um identificador comum](../assets/merge-left.svg)