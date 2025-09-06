# desafio_instancia_ec2_dio
Desafio Code Girl EC2

O diagrama representa uma arquitetura simples do processamento e armazenamento de imagens na AWS, envolvendo os seguintes serviços e etapas:

1. Ator (Usuário Final)
  O ator inicia uma interação, presumivelmente pelo envio de uma imagem para o sistema.
2. Internet
  O pedido do usuário é enviado pela Internet até os serviços hospedados na AWS.
3. AWS EC2
  Uma instância EC2 (servidor virtual na AWS) recebe o pedido inicial do usuário.
  A EC2 pode executar uma aplicação web responsável por receber o upload da imagem.
4. EBS
  O EC2 está conectado a um volume EBS, utilizado para armazenamento de dados persistentes da aplicação.
5. S3 (Upload de Imagem)
  Após o upload ser processado pelo EC2, uma imagem é enviada para um bucket S3, que serve para armazenar arquivos, neste caso, imagens.
  O S3 aparece com a indicação “Upload Image”.
6. AWS Lambda (Processamento de Imagem)
  Quando uma imagem é enviada ao S3, uma função Lambda é disparada para processá-la.
  Lambda executa código sem necessidade de servidor dedicado, ideal para tarefas pontuais como redimensionamento, conversão ou análise de imagem.
7. S3 (Galeria de Imagem)
  Depois do processamento, a imagem pode ser armazenada em outro bucket S3, identificado como “Galeria de Imagem”, onde ficam   as imagens prontas para consulta/exibição.

Resumo do Fluxo
  O usuário faz upload de uma imagem via internet para o EC2 .
  EC2 salva dados no EBS e envia a imagem para o S3 (Upload Image) .
  O upload dispara um evento que aciona o Lambda (Função de Processamento de Imagem) .
  A função Lambda processa a imagem e salva o resultado em outro S3 (Galeria de Imagem) .
  Componentes Visuais no Diagrama
  Ator : Representa o usuário.
  Internet : Conexão do usuário com a AWS.
  AWS EC2 : Instância que recebe upload e orquestra o fluxo.
  EBS : Armazenamento associado ao EC2.
  S3 (Upload Image) : Balde inicial de armazenamento.
  Lambda : Função de processamento desencadeada por eventos no S3.
  S3 (Galeria de Imagem) : Balde final para consulta.
  Setas : Indicam o fluxo de dados e chamadas de serviços.
