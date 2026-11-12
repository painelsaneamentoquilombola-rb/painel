# Painel de Saneamento Quilombola – Barra do Turvo (SP)

Painel de dados sobre água, esgoto, resíduos sólidos e drenagem nas comunidades quilombolas de Barra do Turvo (Cedro, Reginaldo, Pedra Preta/Paraíso, Ribeirão Grande/Terra Seca e Ilhas), com classificação do atendimento segundo o Programa Nacional de Saneamento Rural (PNSR).

Produto técnico-tecnológico da dissertação de mestrado de Luiz Henrique Dias Roman no Mestrado Profissional em Gestão e Regulação de Recursos Hídricos (ProfÁgua), UNESP/FEIS, sob orientação do Prof. Dr. Jefferson Nascimento de Oliveira.

## Como o painel funciona

- `index.html` é a página do painel. Ela não guarda os números: lê os arquivos da pasta `dados/` toda vez que é aberta.
- `dados/` contém três planilhas em formato CSV (texto separado por ponto e vírgula, que o Excel abre normalmente).

## Como atualizar os dados

1. Abra a pasta `dados/` aqui no GitHub e clique no arquivo que quer mudar.
2. Clique no ícone de download (seta para baixo) para baixar o arquivo.
3. Abra no Excel, altere os valores e salve como **CSV UTF-8 (delimitado por vírgulas)**. O Excel em português usa ponto e vírgula como separador, que é o que o painel espera.
4. Volte à pasta `dados/` no GitHub, clique em **Add file → Upload files**, arraste o arquivo salvo (com o mesmo nome) e clique em **Commit changes**.
5. Em um ou dois minutos o painel publicado mostra os dados novos. Cada alteração fica registrada no histórico do repositório, com data.

Regras para não quebrar o painel:
- Não mude o nome dos arquivos nem a primeira linha (os nomes das colunas).
- Use vírgula como separador decimal (ex.: `39,36`).
- Uma linha por item; linhas em branco são ignoradas.

## Dicionário de dados

### `comunidades.csv` – uma linha por comunidade

| Coluna | Conteúdo |
|---|---|
| id | código curto da comunidade, sem espaços (usado para ligar as planilhas) |
| nome | nome da comunidade |
| familias | número de famílias (ITESP) |
| area_ha | área do território, em hectares |
| reconhecimento | data do reconhecimento pelo ITESP, no formato AAAA-MM-DD |
| dentro_rds | `sim` ou `não`: se o território está na RDS Quilombos de Barra do Turvo |
| situacao_ibge | situação fundiária registrada pelo IBGE (vazio se não houver dado) |
| pessoas_quilombolas | pessoas quilombolas recenseadas no território (Censo 2022) |
| domicilios | domicílios com pelo menos um morador quilombola (Censo 2022) |
| fonte | origem principal dos dados da comunidade (`Censo` ou `Vistoria`) |
| observacao | texto curto exibido na ficha da comunidade |

### `atendimento.csv` – uma linha por tipo de solução em cada comunidade

| Coluna | Conteúdo |
|---|---|
| comunidade_id | o mesmo `id` de `comunidades.csv` |
| componente | `agua`, `esgoto`, `lixo`, `drenagem` ou `sabesp` |
| solucao | descrição do tipo de atendimento (ex.: "Fossa rudimentar, vala, rio ou outra forma") |
| domicilios | número de domicílios com essa solução |
| classe_pnsr | `adequado`, `a confirmar`, `precário` ou `sem atendimento` |
| observacao | nota curta exibida no detalhe (opcional) |
| fonte | origem do dado |

Componente sem nenhuma linha aparece no painel como "sem dado". Quando a vistoria de campo for feita, basta substituir as linhas do Censo pelas linhas da vistoria, com a classe PNSR verificada.

### `municipio.csv` – indicadores municipais de contexto

| Coluna | Conteúdo |
|---|---|
| grupo | `agua`, `esgoto` ou `rural` |
| indicador | nome da fonte ou do indicador |
| descricao | o que a fonte conta como atendimento |
| valor_pct | percentual, com vírgula decimal |
| cor | `azul`, `verde` ou `neutro` (cor da barra) |
| fonte | referência |

## Fontes

IBGE, Censo Demográfico 2022: Quilombolas (2024), Tabelas de resultado 12 e 13; ITESP (2026); SINISA 2025, ano de referência 2024; ANA (2025), indicadores ODS 6; Contrato de Concessão nº 01/2024 da URAE-1; Funasa (2019), PNSR, Quadro 4.1; Ministério da Saúde, SISAGUA (2026).

## Licença

Dados e textos sob licença Creative Commons Atribuição 4.0 (CC BY 4.0): podem ser usados e redistribuídos desde que citada a fonte.
