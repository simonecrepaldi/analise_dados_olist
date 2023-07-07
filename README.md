# Análise - Olist
A [Olist](https://olist.com/pt-br/) conecta pequenos negócios de todo o Brasil, que vendem os seus produtos através da Olist Store e enviam os pedidos diretamente os clientes.

Depois que um consumidor realiza uma compra, a Olist notifica um vendedor para atender esse pedido. Após receber o produto, ou na data prevista de entrega, o cliente recebe por email uma pesquisa de satisfação para avaliar a experiência através de uma nota de 1 a 5, onde pode também deixar algum comentário sobre a sua compra/experiência.

## Dados
Os dados foram disponibilizados pela Olist no [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) e possuem informações de mais de 100 mil pedidos realizadtos entre 2016 e 2018, distribuídos em 8 datasets.

![image](https://github.com/simonecrepaldi/analise_dados_olist/assets/77973522/dfc869b9-2e9f-4a64-82ad-2fe7da6b9888)


### customers
*Possui informações sobre os clientes e a sua localização, como CEP, cidadade e estado. Para identificar a quantidade de clientes únicos devemos usar a "customer_unique_id", portando um mesmo cliente pode ter mais de uma "customer_id".*
*	customer_id: id do cliente (chave para o orders_dataset.xlsx)
*	customer_unique_id: id única do cliente
*	customer_zip_code_prefix: 5 primeiros dígitos do código de endereçamento postal do cliente (CEP)
*	customer_city: cidade do cliente
*	customer_state: estado do cliente


### geolocation
*Aqui podemos obter a longitude e latitude de cada CEP e, com isso, determinar as distâncias entre vendedores e clientes.*
*	geolocation_zip_code_prefix: 5 primeiros dígitos do código de endereçamento (CEP)*
*	geolocation_lat: latitude
*	geolocation_lng: longitude
*	geolocation_city: cidade
*	geolocation_state: estado


### order_items
*Contém as informações sobre os itens de cada pedido. Caso um pedido tenha mais de um item, eles irão aparecer cada um em uma linha diferente. Podemos identificar a quantidade de itens do pedido através do "order_item_id".*
*	order_id: id única do pedido
*	order_item_id: número sequencial que identifica o número de itens em um mesmo pedido
*	product_id: id única do produto
*	seller_id: id única do vendedor
*	shipping_limit_date: data limite para envio do pedido a empresa de entrega
*	price: preço do item
*	freight_value: preço do frete do item (se um pedido tiver mais de um item, o valor do frete é dividido entre os itens)


### order_payments
*Mostra as informações sobre o pagamento do pedido.*
*	order_id: id única do pedido
*	payment_sequential: o pagamento pode ser feito com mais de um método de pagamento. Nesse caso, será gerada uma sequência numérica dos métodos escolhidos.
*	payment_type: método de pagamento escolhido pelo cliente (credit_card, boleto, voucher, not_defined)
*	payment_installments: número de parcelas
*	payment_value: valor total do pagamento


### order_reviews
*As avaliações feitas pelos clientes são apresentadas nesse dataset. Quando o pedido é entregue, o cliente recebe um email com uma pesquisa de satisfação para avaliar a experiência com uma nota de 1 a 5 e, caso queira, pode também deixar um comentário. O email também é enviado se acabar o prazo de entrega previsto no momento da compra, mesmo se ela não tiver sido entregue.*
*	review_id: id única da avaliação
*	order_id: id única do pedido
*	review_score: pontuação da avaliação (1 a 5) data pelo cliente na pesquisa de satisfação
*	review_comment_title: título da avaliação deixada pelo cliente
*	review_comment_message: mensagem da avaliação deixada pelo cliente
*	review_creation_date: data de envio da pesquisa de satisfação ao cliente
*	review_answer_timestamp: data/hora da resposta da pesquisa de satisfação feita pelo cliente


### orders
*É o dataset principal que contém as informações sobre o pedido como o status, data da compra, id do cliente, datas de entrega ao cliente, data de aprovação do pagamento, entre outras. Através dele conseguimos relacionar os demais datasets utilizando a "order_id" e "customer_id".*
*	order_id: id única do pedido
*	customer_id: id do cliente (chave para o customer_dataset.xlsx)
*	order_status: status do pedido (delivered, shipped, canceled, approved, created, invoiced, processing, unavailable)
*	order_purchase_timestamp: data/hora da compra
*	order_approved_at: data/hora da aprovação do pagamento
*	order_delivered_carrier_date: data/hora da entrega do pedido à transportadora
*	order_delivered_customer_date: data/hora da entrega do pedido ao cliente
*	order_estimated_delivery_date: data estimada de entrega informada ao cliente no momento da compra


### products
*Possui informações sobre os produtos a venda, como categoria e atributos (peso e dimensões).*
*	product_id: id única do produto
*	product_category: categoria do produto
*	product_name_lenght: comprimento (número de caracteres) do nome do produto
*	product_description_lenght: comprimento (número de caracteres) da descrição do produto
*	product_photos_qty: quantidade de fotos publicadas do produto
*	product_weight_g: peso do produto (em gramas)
*	product_lenght_cm: comprimento do produto (em centímetros)
*	product_height_cm: altura do produto (em centímetros)
*	product_width_cm: largura do produto (em centímetros)


### sellers
*Mostra as informações sobre os vendedores como a id e a localização (CEP, cidade e estado).*
*	seller_id: id única do vendedor
*	seller_zip_code_prefix: 5 primeiros dígitos do código de endereçamento postal do vendedor (CEP)
*	seller_city: cidade do vendedor
*	seller_state: estado do vendedor


## Mapeamento do Processo de Compra
![image](https://github.com/simonecrepaldi/analise_dados_olist/assets/77973522/381d0577-9667-4033-bd90-148677cab373)
