# Modelagem-de-Banco-de-Dados-com-PostgreSQL---Atividade-Pr-tica-Passo-a-Passo
Atividade de Projetos de Bancos onde foi dado alguns cenários onde temos que desenvolver soluções.

# TEMA: RoupaPermalink
Rede de roupas - Aplicativo para rede social de divulgação, venda e troca de roupas (organização de guarda-roupa, combinação de roupas, registro de reações e negociações).
# codigos mermaide 
---
config:
  layout: elk
  theme: redux-dark-color
title: Sample title
---
erDiagram
	direction TB
	PESSOA {
		int id PK "ID do sistema"  
		int CPF  "CPF pq sim"  
		string name  "Eu tenho nome, e quem não tem?"  
		string email  "Pra enviar spam"  
		int Fucao FK "Pra saber se ele vendo ou compra ou os 2."  
	}

	LOJA {
		string Lid PK "Id da loja"  
		string lname  "Nome da loja"  
		string Pid FK "Produtos da loja"  
	}

	FUNCAO {
		string id FK ""  
		boolean FALSE  "Só compra"  
		boolean TRUE  "Compra e vende"  
		string lid FK "Id da loja"  
	}

	PRODUTOS {
		string Pid PK "Produtos"  
		string name  "Nome do item"  
		float price  "Preço"  
		string lid FK ""  
	}

	carrinho {
		string cid PK ""  
		date orderDate  ""  
		string status  ""  
		string id FK "Pessoa que fez o pedido"  
		string pid FK "Id dos produtos vinculados"  
	}

	NF {
		int NF PK ""  
		string cid FK ""  
	}

	POST {
		string PSid PK ""  
		name nome  ""  
		int id FK ""  
	}

	Feed {
		string Fid PK "feed pessoal"  
		string psid FK "posts"  
		string pid FK "produtos"  
		string lid FK "lojas"  
	}

	PESSOA||--||carrinho:"pessoa/carrinho"
	carrinho||--||NF:"Carrinho/nf"
	FUNCAO||--||PESSOA:"função/pessoa"
	FUNCAO||--||LOJA:"função/loja"
	PRODUTOS}|--|{LOJA:"produtos/loja"
	POST}|--||PESSOA:"post/pessoa"
	PRODUTOS}|--|{carrinho:"produtos/carrinho"
	PRODUTOS}|--|{Feed:"produtos/feed"
	LOJA}|--|{Feed:"lojas/feed"
	POST}|--|{Feed:"posts/feed"
