# Perguntas de negócios I 

- 1. Qual o número de clientes únicos do estado de Minas Gerais?
    
    ```sql
    SELECT
    	COUNT(c.customer_state)
    FROM 
    	customer c
    
    Resultado: 11635
    ```
    
- Qual a quantidade de cidades únicas dos vendedores do
estado de Santa Catarina?
    
    ```sql
    SELECT 
    	COUNT(DISTINCT g.geolocation_city)
    FROM 
    	geolocation g
    WHERE 
    	geolocation_state = 'SC'
    Resultado: 420 cidades
    ```
    
- Qual a quantidade de cidades únicas de todos os vendedores
da base?
    
    ```sql
    SELECT 
    	COUNT(DISTINCT g.geolocation_city)
    FROM 
    	geolocation g
    Resultado: 8011 cidades
    ```
    
- Qual o número total de pedidos únicos acima de R$ 3.500
    
    ```sql
    SELECT 
    	COUNT(DISTINCT oi.order_id)
    FROM 
    	order_items oi
    WHERE 
    	oi.price > 3500
    Resultado = 18 pedidos
    ```
    
- Qual o valor médio do preço de todos os pedidos?
    
    ```sql
    SELECT 
    	AVG(oi.price)
    FROM 
    	order_items oi
    Resposta: R$ 120,65
    ```
    
- Qual o maior valor de preço entre todos os pedidos?
    
    ```sql
    SELECT 
    	MAX(oi.price)
    FROM 
    	order_items oi
    Resposta: R$ 6.735
    ```
    
- Qual o menor valor de preço entre todos os pedidos?
    
    ```sql
    SELECT 
    	MIN(oi.price)
    FROM 
    	order_items oi
    Resposta: R$ 0,85.
    ```
    
- Qual a quantidade de produtos distintos vendidos abaixo do
preço de R$ 100.00?
    
    ```sql
    SELECT 
    	COUNT(DISTINCT oi.product_id)
    FROM 
    	order_items oi
    WHERE 
    	oi.price < 100
    
    Reposta: 20,112
    ```
    
- Qual a quantidade de vendedores distintos que receberam
algum pedido antes do dia 23 de setembro de 2016?
    
    ```sql
    SELECT
    	COUNT( oi.seller_id)
    FROM 
    	order_items oi
    WHERE 
    	oi.shipping_limit_date < '2016-09-23 00:00:00'
    
    Resposta: 4 vendedores
    ```
    
- Quais os tipos de pagamentos existentes?
    
    ```sql
    SELECT
    	DISTINCT op.payment_type 
    FROM 
    	order_payments op
    
    Resposta: credit_card, boleto, voucher, debit_card e not_defined.
    ```
    
- Qual o maior número de parcelas realizado?
    
    ```sql
    SELECT
    	MAX(op.payment_installments)
    FROM 
    	order_payments op
    Resposta: 24 parcelas
    ```
    
- Qual o menor número de parcelas realizado?
    
    ```sql
    SELECT
    	MIN(op.payment_installments)
    FROM 
    	order_payments op
    Resposta: 0 parcelas
    ```
    
- Qual a média do valor pago no cartão de crédito?
    
    ```sql
    SELECT
    	AVG(op.payment_value)
    FROM 
    	order_payments op 
    WHERE
    	op.payment_type = 'credit_card'
    Resposta: R$ 163,32
    ```
    
- Quantos tipos de status para um pedido existem?
    
    ```sql
    SELECT
    	COUNT(DISTINCT o.order_status)
    FROM 
    	orders o
    Resposta: 8 status
    ```
    
- Quais os tipos de status para um pedido?
    
    ```sql
    SELECT
    	DISTINCT o.order_status
    FROM 
    	orders o
    Resposta: 
    delivered
    invoiced
    shipped
    processing
    unavailable
    canceled
    created
    approved
    ```
    
- Quantos clientes distintos fizeram um pedido?
    
    ```sql
    SELECT
    	COUNT(DISTINCT o.customer_id)
    FROM 
    	orders o
    Resposta: 99,441 
    ```
    
- Quantos produtos estão cadastrados na empresa?
    
    ```sql
    SELECT
    	COUNT(DISTINCT p.product_id)
    FROM 
    	products p
    Resultado: 32951
    ```
    
- Qual a quantidade máxima de fotos de um produto?
    
    ```sql
    SELECT
    	MAX(p.product_photos_qty)
    FROM 
    	products p
    Resposta: 20 fotos
    ```
    
- Qual o maior valor do peso entre todos os produtos?
    
    ```sql
    SELECT
    	MAX(DISTINCT p.product_weight_g)
    FROM 
    	products p
    Resposta: 40,425 g
    ```
    
- Qual a altura média dos produtos?
    
    ```sql
    SELECT
    	AVG(DISTINCT p.product_height_cm)
    FROM 
    	products p
    Resposta: 52,67 cm
    ```