# Briefing — Blendêê Burger

**Cliente:** Igor Aguiar, dono da Blendêê Burger (hamburgueria artesanal, abre sexta, sábado e domingo à noite)

**Tipo:** Cliente novo

**Objetivo principal:** Fechar esse primeiro cliente e usar de case/portfólio.

**Entrega inicial:** Sistema de gestão de estoque.

## Contexto

Dor original identificada (call de prospecção): dificuldade em atrair mais clientes, alcançar mais pessoas e ter um posicionamento digital mais profissional e completo — o que apontava pra site + automação de atendimento.

Na entrevista de abertura do projeto, a prioridade declarada mudou: o Igor está precisando, inicialmente, de um sistema de gestão de estoque. Site e automação de atendimento seguem como possíveis próximas entregas, mas a entrada é pelo estoque.

## Fatos confirmados

- Loja única (não múltiplas unidades)
- Hamburgueria nova — 8 meses de funcionamento (não 5, corrigido na call de 05/10/2026), crescendo rápido
- Controle de estoque hoje é de cabeça ou no papel — não aguenta mais o volume atual
- Igor usa sozinho, sem ajuda — cadastro de fornecedor e multiusuário não são relevantes pra ele agora (confirma que o PWA local no aparelho é suficiente, sem necessidade de dado compartilhado entre dispositivos)
- Rotina semanal: opera quinta a domingo. Segunda/terça ele levanta o que falta e faz os pedidos, que chegam até quinta. ~20-30 insumos no total
- Frequência de compra: pão e batata quase toda semana; carne e bebida de 15 em 15 dias
- Prefere mexer no celular, não em planilha — já tentou controlar estoque pelo ChatGPT (foto de nota fiscal) e não funcionou, a memória do chat "esquecia"
- Avaliou o "Chefia" (controle de estoque via WhatsApp, IA lê foto de nota fiscal) — achou completo mas caro pro nível de controle que precisa agora (R$150/mês por 500 mensagens)
- Quer rastrear custo dos insumos, não só ter/não ter — preços variam (ex: tomate R$7 a R$15 dependendo da semana) e ele quer isso pra acompanhar CMV
- **Fluxo ideal pra baixa de estoque** (o requisito mais importante da call): cada produto do cardápio tem uma "ficha técnica" (ex: Chicken Bacon = 1 pão + 30g maionese + 30g catupiry + 1 fatia muçarela + 1 hambúrguer de frango + 10g alface + 2 rodelas de tomate). Ele lança quanto vendeu de cada produto no dia (digitando, ou colando o relatório de vendas que já tira do sistema de pedidos dele) e o sistema desconta os insumos automaticamente pela ficha técnica. Confirmou que digitar manualmente também resolve, não precisa ser importação de relatório.
- Itens medidos por peso mas vendidos em porção (ex: batata) — ele já pensa em termos de "porção grande" / "porção pequena" como unidade de estoque (ex: 1 pacote de 2,5kg = 10 porções grandes + 15 porções pequenas), não em kg direto. Confirmar esse cadastro por porção ao montar os insumos.
- Já usa um sistema de gestão de pedidos separado (integra iFood + WhatsApp via chatbot, gera relatório de vendas por categoria/produto exportável) — esse sistema continua sendo a fonte dos dados de venda, não faz parte do escopo substituir ele

## Decisões de arquitetura

- PWA (app instalável direto do celular, sem loja de aplicativo) — funciona com ou sem wifi/internet, dados salvos no próprio aparelho. Hospedado em serviço gratuito, sem domínio nem mensalidade. Entrega mediante pagamento, como produto fechado: depois de entregue, o Igor usa por conta própria e a Blendêê não depende do Gabriel pra continuar no ar. Ajustes e atualizações são publicados por Gabriel e chegam automaticamente no app do Igor — não exige reinstalação nem visita presencial pra manutenção simples.
- Cadastro inicial dos insumos via importação de planilha, em vez de formulário item por item.

## Próximos passos

- ~~Levantar com o Igor os requisitos do sistema de estoque~~ — feito na call de 05/10/2026 (ver Fatos confirmados)
- Apresentar a proposta de escopo + demo funcional na call de 12/10/2026 (segunda-feira, ~20h) — objetivo é mostrar que o fluxo de ficha técnica + baixa automática por venda é viável, mesmo incompleto
- Fechar lista final dos ~20-30 insumos e fichas técnicas de cada item do cardápio
- Fechar escopo e comercial
- Depois de validado, retomar as demais frentes (site, automação de atendimento)
