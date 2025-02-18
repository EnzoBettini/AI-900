<h1>DIO AI-900</h1>
<h6> este repositório conta com as intruções e os outputs em json do curso AI-900 da DIO </h6>

<h2>Configuração do Ambiente no Azure</h2>
<h3>1. Acessar o Portal do Azure</h3>
<ol>
    <li>Acesse <a href="https://portal.azure.com">Azure Portal</a> e faça login com suas credenciais da Microsoft.</li>
    <li>Selecione <code>+ Criar um recurso</code> e pesquise por <code>Machine Learning</code>.</li>
    <li>Crie um novo recurso de <code>Azure Machine Learning</code> com as seguintes configurações:</li>
    <ul>
        <li><strong>Assinatura</strong>: Sua assinatura do Azure.</li>
        <li><strong>Grupo de recursos</strong>: Crie ou selecione um grupo de recursos.</li>
        <li><strong>Nome</strong>: Escolha um nome único para seu workspace.</li>
        <li><strong>Região</strong>: Leste dos EUA (East US).</li>
        <li><strong>Conta de armazenamento</strong>: Aceite a conta padrão que será criada automaticamente.</li>
        <li><strong>Key Vault</strong>: Aceite o cofre de chaves padrão.</li>
        <li><strong>Application Insights</strong>: Aceite a configuração padrão.</li>
        <li><strong>Registro de contêiner</strong>: Nenhum (um será criado automaticamente ao implantar um modelo).</li>
    </ul>
    <li>Clique em <code>Revisar + Criar</code> e depois em <code>Criar</code>. Aguarde a criação do workspace.</li>
    <li>Acesse o recurso criado e clique em <code>Launch Studio</code> ou abra <a href="https://ml.azure.com">Azure Machine Learning Studio</a> e faça login.</li>
</ol>

<h2>Criando e Executando um Job de AutoML</h2>
<h3>2. Criar um Job de Machine Learning Automatizado</h3>
<p>No Azure Machine Learning Studio, acesse <code>Automated ML</code> na guia <code>Authoring</code>.</p>
<p>Crie um novo trabalho (job) com as seguintes configurações:</p>

<h4>Configurações Básicas:</h4>
<ul>
    <li><strong>Nome do Job</strong>: Nome gerado automaticamente (mantenha-o).</li>
    <li><strong>Nome do Experimento</strong>: <code>mslearn-bike-rental</code></li>
    <li><strong>Descrição</strong>: Automated machine learning for bike rental prediction.</li>
</ul>

<h4>Tipo de Tarefa e Dados:</h4>
<ul>
    <li><strong>Tipo de Tarefa</strong>: Regressão</li>
    <li><strong>Dataset</strong>: Criar um novo dataset com:</li>
    <ul>
        <li><strong>Nome</strong>: bike-rentals</li>
        <li><strong>Descrição</strong>: Historic bike rental data</li>
        <li><strong>Fonte de Dados</strong>: From local files</li>
        <li><strong>Destino de Armazenamento</strong>: Azure Blob Storage</li>
    </ul>
</ul>

<h4>Configurações da Tarefa:</h4>
<ul>
    <li><strong>Coluna Alvo</strong>: rentals</li>
    <li><strong>Métrica Primária</strong>: NormalizedRootMeanSquaredError</li>
    <li><strong>Modelos Permitidos</strong>: RandomForest, LightGBM</li>
    <li><strong>Timeout do Experimento</strong>: 15 minutos</li>
</ul>

<h3>3. Submeter o Job e Aguardar a Execução</h3>
<ol>
    <li>Envie o trabalho de treinamento. Ele iniciará automaticamente.</li>
    <li>Aguarde a conclusão do processo (pode levar alguns minutos).</li>
</ol>
<p>Agora você está pronto para analisar os resultados e usar o modelo treinado! 🚀</p>
