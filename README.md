# Relatório do Desafio de Engenharia de Dados
## Introdução
Este documento detalha a execução e implementação da solução para o Indicium Tech Code Challenge.

- Scheduler: **Airflow**

- Data Loader: **Meltano (Baseado em Python)**

- Database: **PostgreSQL**

## Configuração do Ambiente

Instalação do Meltano: Ferramenta que facilita o gerenciamento de pipelines de dados.
```
pip install meltano
```

Construção do Projeto: Executado para configurar o ambiente e instalar dependências adicionais necessárias para o projeto.
```
bash ./build.sh
```

Inicialização da Aplicação: Utilizado para inicializar o projeto, configurando os plugins e verificando as dependências.
```
bash ./init.sh
```

Pipeline executa qualquer dia anterior. Modifique a data para escolher qualquer dia de interesse.
```
bash ./init.sh 2024-10-06
```

# Verifique onde o pipeline falhou
Navegue até o diretório queries/arquivos para analisar onde erros podem ocorre na conversão dos arquivos.
![image](https://github.com/poxaIan/Desafio_Engenharia_Dados/blob/main/Docs/queries.png)
## Resultado da Consulta

Verifique o resultado salvo localmen
## Estrutura do Projeto

Pasta data/postgres: Local onde os arquivos CSV são salvos após a extração.

Banco de Dados challenge_db2_1: Banco de dados PostgreSQL onde os dados transformados são carregados.

## Configuração do Docker
Foram configurados dois serviços de banco de dados PostgreSQL usando Docker:

db: Banco de dados de origem contendo os dados brutos.

db2: Banco de dados de destino onde os dados transformados são carregados.

Os dados foram inicializados a partir de arquivos SQL fornecidos, e volumes Docker foram usados para persistir os dados entre reinicializações.

## Pipeline ETL
O pipeline ETL foi configurado usando o Meltano:

Extractors: Utilizados para extrair dados dos arquivos CSV.

Loaders: Utilizados para carregar os dados transformados no banco de dados PostgreSQL.

Mappers: Utilizados para transformar os dados conforme necessário.

## Resultados
Extração e Transformação
Os dados foram extraídos com sucesso dos arquivos CSV e transformados conforme necessário. As transformações incluíram ajustes de tipos de dados e a configuração de chaves primárias compostas para garantir a integridade dos dados.

Carregamento
Os dados transformados foram carregados com sucesso no banco de dados PostgreSQL challenge_db2_1. A estrutura final do banco de dados atendeu aos requisitos do desafio, permitindo a execução de consultas SQL para verificar a integridade e precisão dos dados carregados.

## Desafios Enfrentados
Configuração Inicial: A configuração inicial do ambiente, incluindo a instalação do Meltano e a configuração do Docker, apresentou alguns desafios, especialmente em relação à compatibilidade de versões.
Compatibilidade do Docker Compose: Foi necessário ajustar os arquivos de script para garantir a compatibilidade com a versão do Docker Compose utilizada.
Conflitos de Porta: Houve a necessidade de gerenciar conflitos de porta com outros serviços em execução no sistema.
Padrões de Nome de Arquivo: O script organiza_details.py apresentou dificuldades ao lidar com padrões de nome de arquivo, exigindo ajustes para garantir que os arquivos fossem processados corretamente.

## Conclusão
Apesar dos desafios enfrentados, a solução foi implementada com sucesso. Os dados foram extraídos de arquivos locais, transformados conforme necessário e carregados no banco de dados PostgreSQL conforme os requisitos do desafio. Este projeto proporcionou uma experiência valiosa no uso de ferramentas de ETL e orquestração de dados, como Meltano e Docker, e demonstrou a eficácia dessas ferramentas na automação de processos de engenharia de dados.