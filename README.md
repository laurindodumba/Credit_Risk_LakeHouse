# Credit Risk Lakehouse — Microsoft Fabric

## Notebooks
1. `01_bronze_credit_risk_ingestion.ipynb` — carrega o CSV para Bronze.
2. `02_silver_credit_risk_quality.ipynb` — tipagem, deduplicação, regras de qualidade e rejeitados.
3. `03_gold_credit_risk_analytics.ipynb` — KPIs e tabelas analíticas para Power BI.

## Preparação no Microsoft Fabric
1. Crie um workspace e um Lakehouse chamado `lh_credit_risk`.
2. Anexe o Lakehouse como padrão a cada notebook.
3. Faça upload do Kaggle CSV para `Files/landing/credit_risk_dataset.csv`.
4. Importe os três ficheiros `.ipynb` como notebooks Fabric.
5. Execute na ordem 01 → 02 → 03.

## Fonte de dados
https://www.kaggle.com/datasets/laotse/credit-risk-dataset

Esperado: `credit_risk_dataset.csv`, com colunas como `person_age`, `person_income`, `loan_amnt`, `loan_status`, etc.

## Observações
- Os notebooks usam tabelas Delta geridas pelo Lakehouse padrão.
- A primeira execução usa overwrite para facilitar reprodução. Para produção, definir ingestão incremental, chaves, tratamento de schema drift e estratégia de upsert.
- A camada Gold é analítica/descritiva; não é um modelo de decisão ou previsão de crédito.
- Rever resultados da tabela `silver_credit_risk_rejects` antes de considerar a qualidade final aprovada.
