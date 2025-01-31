# Traffic Sign Recognition
Trabalho Apresentado na Disciplina Cognição Visual 2016/2

Alunos: Ranik Guidolini e Vinicius B. Cardoso

Reconhecimento de Placas de Trânsito

## Requisitos

- Caffe - http://caffe.berkeleyvision.org/

  [Installation instructions](http://caffe.berkeleyvision.org/installation.html)

- Dataset

  [German Traffic Sign Recognition Benchmark (GTSRB)](http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset#Downloads)
  Lembre-se de baixar o arquivo de anotação com o ID da classe [Anotações com ID](http://benchmark.ini.rub.de/Dataset/GTSRB_Final_Test_GT.zip) 

- Caffemodel Rede Pré-treinada

  [NIN-ImageNet](https://gist.github.com/mavenlin/d802a5849de39225bcc6.) 

- Este Repositório

``` bash
git clone https://github.com/vinibc/Trab_Cognicao_RanikVinicius.git
```


## Instruções

Após ter os requisitos verifique o caminho das pastas de treino e teste nos arquivos dataset/train-shuffled.tx e test.txt

Os scripts utilizados para gerar esses arquivos estao na pasta.

Mantendo mesmo nome dos diretorios, nao eh necessario roda-los novamente Se necessário siga as informações no README da pasta dataset

Para rodar os experimentos usando a caffe é necessário o solver, o arquivo de definição da rede e o caffemodel com os pesos da rede neural. 
Os utilizados neste trabalho podem ser encontrados nas pastas Network-Train-1 e Network-Train-2

Para iniciar o treino usando a nin-imagenet
``` bash
caffe train -solver caminho/nome_do_solver -weigth caminho/nin-imagenet.caffemodel
```

Para usar o caffemodel do último treino de reconhecimento de placas


Teste treinando todas as camadas

``` bash
cd Trabalho_Cognicao_RanikVinicius/Network-Train-1
caffe train -solver Signs-all-layers-solver.prototxt -snapshot snapshots/_iter_118120.solverstate
```

Para o teste treinando apenas a última camada

``` bash
cd Trabalho_Cognicao_RanikVinicius/Network-Train-2
caffe train -solver Signs-last-layers-solver.prototxt -snapshot snapshots/_iter_xx.solverstate
```

Os testes foram realizados em GPU, para usar a CPU apenas mude no solver "solver_mode: CPU"

