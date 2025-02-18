Azure Machine Learning - Bike Rental Prediction

Este repositório fornece instruções para configurar um ambiente no Azure Machine Learning e treinar um modelo de previsão de aluguel de bicicletas usando aprendizado de máquina automatizado (AutoML).

Configuraço do Ambiente no Azure

1. Acessar o Portal do Azure

Acesse Azure Portal e faça login com suas credenciais da Microsoft.

Selecione + Criar um recurso e pesquise por Machine Learning.

Crie um novo recurso de Azure Machine Learning com as seguintes configurações:

Assinatura: Sua assinatura do Azure.

Grupo de recursos: Crie ou selecione um grupo de recursos.

Nome: Escolha um nome único para seu workspace.

Região: Leste dos EUA (East US).

Conta de armazenamento: Aceite a conta padrão que será criada automaticamente.

Key Vault: Aceite o cofre de chaves padrão.

Application Insights: Aceite a configuração padrão.

Registro de contêiner: Nenhum (um será criado automaticamente ao implantar um modelo).

Clique em Revisar + Criar e depois em Criar. Aguarde a criação do workspace.

Acesse o recurso criado e clique em Launch Studio ou abra Azure Machine Learning Studio e faça login.

Criando e Executando um Job de AutoML

2. Criar um Job de Machine Learning Automatizado

No Azure Machine Learning Studio, acesse Automated ML na guia Authoring.

Crie um novo trabalho (job) com as seguintes configurações:

Configurações Básicas:

Nome do Job: Nome gerado automaticamente (mantenha-o).

Nome do Experimento: mslearn-bike-rental

Descrição: Automated machine learning for bike rental prediction

Tags: Nenhuma

Tipo de Tarefa e Dados:

Tipo de Tarefa: Regressão

Dataset: Criar um novo dataset com:

Nome: bike-rentals

Descrição: Historic bike rental data

Tipo: Table (mltable)

Fonte de Dados: From local files

Destino de Armazenamento: Azure Blob Storage

Nome do Datastore: workspaceblobstore

Upload: Baixe e extraia os arquivos de bike-rentals dataset e envie-os.

Configurações da Tarefa:

Coluna Alvo: rentals

Métrica Primária: NormalizedRootMeanSquaredError

Modelos Permitidos: RandomForest, LightGBM

Limites:

Máximo de Testes: 3

Testes Concorrentes: 3

Nós Máximos: 3

Threshold de Métrica: 0.085

Timeout do Experimento: 15 minutos

Timeout de Iteração: 15 minutos

Early Termination: Ativado

Validação e Teste:

Tipo de Validação: Train-validation split

Percentual de Validação: 10%

Dataset de Teste: Nenhum

Computação:

Tipo de Computação: Serverless

Tipo de VM: CPU

Tier da VM: Dedicated

Tamanho da VM: Standard_DS3_V2*

Número de Instâncias: 1

Se a assinatura não permitir esse tamanho de VM, escolha outro disponível.

3. Submeter o Job e Aguardar a Execução

Envie o trabalho de treinamento. Ele iniciará automaticamente.

Aguarde a conclusão do processo (pode levar alguns minutos).

Agora você está pronto para analisar os resultados e usar o modelo treinado! 🚀
