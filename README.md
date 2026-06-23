# Relatório Diário — Greidistas (PWA)

App instalável no Android e iOS para o relatório diário de atividades dos greidistas: marcação topográfica, mestras, inconsistências de projeto, condições e registro fotográfico com carimbo de data/hora/localização.

## O que este app faz

Cada relatório registra:
- Data, hora, nome do greidista e turno
- Mina, Frente e Planta (com possibilidade de digitar uma frente que não esteja na lista)
- Equipamento em operação
- Se havia marcação topográfica (e motivo, se não havia)
- Se as mestras foram marcadas (e motivo, se não foram)
- Inconsistências no projeto (e descrição, se houver)
- Condição climática
- Paralisação da atividade (e motivo, se houve)
- Volume/metragem executada (estimativa)
- Nível de risco observado
- Comentários livres
- Fotos tiradas pela própria câmera do celular, com carimbo de data/hora/localização desenhado na imagem

## Hospedagem — mesmo processo do app de Ronda de Mina

Este é um PWA (Progressive Web App): precisa estar publicado numa URL `https://...` para instalar de verdade no celular (não funciona abrindo o arquivo localmente — é regra do próprio Android/iOS).

Suba a pasta inteira (`index.html`, `manifest.json`, `service-worker.js`, `icons/`) em um destes serviços gratuitos:
- **GitHub Pages** (recomendado — testado e mais previsível para esse tipo de site estático)
- **Netlify Drop** (rápido, mas tem limite de banda no plano gratuito)
- **Vercel** (cuidado: configure como projeto estático/"Other", não deixe detectar framework automaticamente)
- Servidor interno da empresa, se disponível

Depois de publicado, no Android o navegador oferece "Instalar" automaticamente; no iPhone, abra no Safari e use Compartilhar → "Adicionar à Tela de Início".

## Atualizando a lista de Mina/Frente

O app já vem com uma lista inicial de minas e frentes. Para atualizar:
1. Toque em "⚙ Mina/Frente" no topo do app
2. Exporte a lista atual em CSV (opcional, para usar como base)
3. Prepare um CSV com as colunas: `mina;frente`
4. Importe esse CSV no mesmo menu — a lista é salva no próprio dispositivo

## Exportação

No botão "⬇ Exportar relatórios" há três opções:
- **CSV** — para análise no Power BI
- **Fotos (.zip)** — todas as fotos carimbadas, nomeadas por registro
- **Relatório PDF** — documento único com todos os campos e fotos, pronto para enviar por e-mail

## Atualizando o app no futuro

Substitua os arquivos no mesmo local de hospedagem. A tela principal sempre busca a versão mais recente do servidor; quando há atualização do modo offline, aparece um aviso na tela com botão "Atualizar".
