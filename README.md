# VerificaMalha

Aplicação local (HTML/JS/CSS) para:
1. carregar um DayRep em HTML,
2. organizar os segmentos por matrícula em linha do tempo,
3. cadastrar restrições de malha,
4. analisar impactos e gerar eventos.

## Arquivos principais

- `index.html`: upload do DayRep, parsing e timeline por matrícula.
- `restricoes.html`: cadastro/edição/exclusão de restrições.
- `analise.html`: cruzamento DayRep x restrições e lista de eventos.

## Como usar

1. Abra `index.html` no navegador e carregue o DayRep (`DayRep.html` ou equivalente).
2. Verifique a timeline (ordem cronológica por matrícula), incluindo voo anterior e sucessor por etapa.
3. Abra `restricoes.html` e cadastre as regras desejadas.
4. Abra `analise.html` para visualizar os eventos detectados.

## Persistência local

A aplicação usa `localStorage`:

- `currentDayRepSegments`: segmentos enriquecidos do DayRep.
- `currentDayRepMeta`: metadados do último DayRep carregado.
- `restrictionsV2`: restrições cadastradas.
- `lastAnalysis`: última análise gerada.

Ao carregar um novo DayRep em `index.html`, a chave `lastAnalysis` é removida para forçar nova análise.

## Campos de restrição implementados

- Restriction Type
- ARPT_IATA_Arr
- ARPT_IATA_Orig
- Weekday
- Day
- Month
- Year
- Init_Hour1 / End_Hour1
- Init_Hour2 / End_Hour2
- Init_Hour3 / End_Hour3
- Fleet_Type
- Max Delay Time
- Max Ground Time
- Min Crew Composition
- Expiration Date / validade
- Description / remarks

Campos vazios funcionam como wildcard (não restritivo).

## Lógica de análise

- Critérios gerais em **AND**.
- Blocos de hora em **OR** entre as 3 janelas.
- `Max Delay Time`: compara duração do segmento com limite, usando `ETA-ETD` e fallback `STA-STD`.
- `Max Ground Time`: compara tempo de solo estimado entre chegada atual e partida da próxima etapa da mesma matrícula.
- `Min Crew Composition`: compara com `Crew #` do DayRep (evento quando crew real fica abaixo do mínimo exigido).

## Suposições de parsing do DayRep

Parser implementado com heurística resiliente para DayRep HTML:

1. Procura linha de cabeçalho com `DATE`, `REG`, `DEP`, `ARR`, `STD`, `STA`.
2. Usa primeira ocorrência de cada coluna principal (evita colunas repetidas do relatório).
3. Aceita datas `dd/mm/yy` ou `dd/mm/yyyy` e horários `HH:MM`.
4. Ajusta cruzamento de meia-noite quando horário de chegada é menor que partida.
5. Ignora linhas sem dados mínimos de voo.

Essas heurísticas foram validadas com o `DayRep.html` presente no repositório.
