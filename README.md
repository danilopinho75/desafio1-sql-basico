# Desafio de SQL Básico
Este repositório contém um conjunto de consultas SQL desenvolvidas como parte de um desafio para a área de telemarketing. O objetivo é extrair e analisar informações dos clientes armazenados na tabela `cadastro`. Abaixo estão as perguntas e as respectivas consultas realizadas:

## Desafios

### Desafio 1
A área de telemarketing está organizando uma campanha e precisa que você levante alguns dados para que eles consigam entrar em contato com os clientes da empresa. À partir de uma tabela chamada 'cadastro' selecione todos os clientes que estão localizados nela e as informações das colunas 'Id', 'CPF', 'Primeiro_Nome', 'Idade'.
```
SELECT
  Id,
  CPF,
  Primeiro_Nome,
  Idade
FROM cadastro;
```

### Desafio 2
A área de telemarketing quer que o arquivo esteja ordenado de forma ascendente pela idade, i.e., contendo os mais novos nas primeiras linhas e os mais velhos nas últimas. Realize este ajuste na consulta feita no desafio 1.
```
SELECT
  Id,
  CPF,
  Primeiro_Nome,
  Idade
FROM cadastro
ORDER BY Idade ASC;
```

### Desafio 3
Parece haver um problema na tabela 'cadastro' do desafio 1. Como uma forma de estudar uma amostra dela, você decide pegar somente as primeiras 20 linhas. Escreva uma consulta semelhante ao que foi feito no desafio 1, mas contendo apenas as 20 primeiras linhas.
```
SELECT
  Id,
  CPF,
  Primeiro_Nome,
  Idade
FROM cadastro
LIMIT 20;
```

### Desafio 4
Depois de muito investigar, você viu que não há nenhum problema na tabela, somente um cadastro mal feito, algo bem pontual. Delete o cadastro de Id número 100.
```
DELETE FROM cadastro
WHERE Id = 100;
```

### Desafio 5
Após eliminar o cadastro incorreto do Id de número 100 e reescrever a consulta do desafio 1, você agora precisa passar para seu chefe qual a idade média dos clientes da empresa. Escreva a query que realiza essa consulta.
```
SELECT
  AVG(Idade) AS 'Idade Média'
FROM cadastro;
```
ou
```
SELECT
  ROUND(AVG(Idade)) AS 'Idade Média'
FROM cadastro;
```

### Desafio 6
A empresa deseja saber quantos clientes são maiores de idade. Conte o número de clientes na tabela 'cadastro' que têm 18 anos ou mais.​ Retorne a coluna com a contagem com o nome 'Maior_de_Idade​'.
```
SELECT
  COUNT(*) AS 'Maior_de_Idade'
FROM cadastro
WHERE Idade >= 18;
```

### Desafio 7
A área financeira precisa que você identifique na tabela 'cadastro' quantos clientes têm entre 30 e 40 anos. Escreva uma query para contar esses clientes.​ A coluna de contagem deve ter o nome "Qtd_Clientes_30_e_40".
```
SELECT
  COUNT(*) AS "Qtd_Clientes_30_e_40"
FROM cadastro
WHERE Idade BETWEEN 30 AND 40;
```

### Desafio 8
Verifique a distribuição de clientes por faixa etária agrupando-os em 'menores de 18', '18 a 65' e 'maiores de 65'.​ Em outras palavras, conte quantos clientes temos nessas faixas, retornando essas faixas em uma coluna chamada Faixa_Etaria e a quantidade de clientes na coluna Qtd_Clientes.
```
SELECT
  CASE
    WHEN Idade < 18 THEN "Menores de 18"
    WHEN Idade BETWEEN 18 AND 65 THEN "18 a 65"
    ELSE "Maiores de 65"
  END Faixa_Etaria,
  COUNT(*) AS Qtd_Clientes
FROM cadastro
GROUP BY Faixa_Etaria;
```

### Desafio 9
A área de marketing quer enviar promoções apenas para os 10 clientes mais jovens. Selecione os Ids e Primeiros Nomes dos 10 clientes mais jovens.
```
SELECT
  Id,
  Primeiro_Nome
FROM cadastro
ORDER BY Idade ASC
LIMIT 10;
```

### Desafio 10
Alguns clientes foram cadastrados erroneamente com 'Idade' igual a zero. Encontre esses clientes e exiba seus Ids e Primeiros Nomes.
```
SELECT
  Id,
  Primeiro_Nome
FROM cadastro
WHERE Idade = 0;
```
