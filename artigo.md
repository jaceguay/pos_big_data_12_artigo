Resumo - O presente artigo detalha os testes utilizando o SUMO, um simulador microscópico de trânsito, para obter características do fluxo de veículos a partir de informações dispobinibilizadas abertamente em serviços de navegação veícular, específicamente o Google Maps traffic. Para as simulações foi selecionado uma inteseção viária complexa, compreendendo uma rótula entre vias de várias classes. Pela natureza das informações disponibilizadas pelo Google Traffic, o nível de detalhe apresentado é maior quanto o número de conflitos ou congestionamentos, desta maneira o horário selecionado foi o pico da tarde, das 18:00 horas até as 19:00 horas. O objetivo é que se tenha uma estimativa do número de veículos, para que se possa utilizar como variáveis de entrada em outros cenários de simulação no próprio SUMO.

Palavras chave - Mapa de tráfego, Simulador SUMO, Google Traffic, contagem de tráfego.

## 1. Introdução

O crescimento acelerado das cidades, principalmente a partir da década de 1970, resultou no aumento da frota de veículos, principalmente dos individuais motorizados.

Evolução na Frota de Veículos dos municípios do entorno da BR 101/SC - 2010 e 2019

Variável          | 2010       | 2019        | % de Crescimento | Estimativa para 2029
------------------|------------|-------------|------------------|---------------------
Frota de veículos | 1.7 milhão | 2.6 milhões | 52,9%            | 4.5 milhões
Fonte: Denatran - Elaboração e compilação FIESC/GETMS

A demanda acelerada por mobilidade e subsequentemente pressão na infra estrutura viária, se manifesta com congestionamentos e decaimento no nível de serviços de vias. Ao mesmo tempo eleva o consumo de combustíveis e níveis de poluição. Enquanto se por um lado setor público tem investido na análise das redes viárias, a fim de predizer e tratar os fatores determinantes geradores de conflitos, várias iniciativas privadas buscam desenvolver serviços, com a intenção de auxiliar o grande número de pessoas atingidas. O modelo adotado é o colaborativo, onde cada usuário reporta em tempo real sua situação para a rede. Outra característica, a fim de garantir a adequação as leis de proteção de dados e o anonimato de seus usuários, é a de que os dados são em grande parte qualitativos, limitando-se a exibir apenas as condições de tráfego, sem detalhes sobre as quantidades, por tipos de veículos ou condutores.

Apesar de apresentar apenas uma fração, no que diz respeito as informações necessárias para o planejamento pelo poder público, onde a contagem do fluxo de veículos é um dos insumos primários de qualquer análise do sistema viário, os aplicativos compensam oferecendo dispobinilidade e abrangência tanto temporal quanto espacial.

As provas realizadas buscam reunir as características do tráfego, reportadas pelos aplicativos, as características físicas da malha viária e regulamentação de tránsito, para preencher parâmetros desconhecidos, neste caso o número de veículos, através da simulação utilizando-se do SUMO.

## 2. Conceitos básicos

### "Simulation of Urban MObility" (SUMO)
A simulação de sistema de transporte como ferramenta de análise, tem a habilidade de emular a variação do tempo sobre a enorme quantidade de variáveis que sugem ao redor do trânsito, é utilizada para predizer o resultado de um sistema real. Dentre os modelos destacam-se:

- Macroscópico, onde o fluxo macroscópico (densidade, volume e velocidade) são caracterizados e utilizam-se cálculos como na dinâmica computacional de fluídos. Este modelo aborda o problema de fluxo de tráfego em um nível baixo de detalhes, não existindo interesse por cada unidade individual, e sim no processo como um todo.

- Micoscópico, é apropriado para estudos com elevado nível de detalhamento, baseado na descrição do movimento de cada veículo individualmente, cada um com propriedades como troca de faixa, aceleração entro outras. A abordagem mais evidente é a car-following, em que o veículo reage ao veículo imediatamente anterior a ele no fluxo de tráfego.

O SUMO é um simulador Microscópico, o que significa que sua implementação é síncrona, a cada passo da simulação (por padrão um segundo) o estado de todas as entidades do modelo são atualizadas, a rotina pode ser descrita da seguinte maneira:

a. Inicialização: Calcula o menor caminho, a partir da origem para o destino pré definidos.

b. Inserção de veículos: Repete até que sejja inserida toda a demanda de tráfego:

    1. Determina o próximo movimento de cada entidade.

    2. Aplica os modelos de troca de faixa, car-following, etc.

    3. Aplica a posição final resultante.

c. Resultado: Coleta e apresenta o conjunto de informações a respeito da simulação.

Os arquivos de entrada mínimos necessários, todos XML, são os seguintes:

- simulacao.sumocfg: Responsável por indicar o nome dos outros arquivos de entrada e saída da simulação.

- malha.net.xml: Linhas (edges) e vértices (nodes), na forma de um grafo que representa o desenho da malha viária. Também armazena as regras de conversões em cruzamentos e velocidades máximas de cada via e faixas. O módulo Netedit (interface gráfica para desenho da malha) e NetConvert podem ser utilizados.

- demanda.rou.xml: Em resumo contêm a maneira, momento, e quantidade de elementos que irão entrar na malha viária, pode conter uma rota pré definida ou apenas um ponto de origem e destinho.

Outros arquivos como um adicional também podem ser incluídos, definindo elementos como sensores e câmeras para contagem em pontos específicos por exemplo.

Os arquivos de saída com os resultados da simulação podem ser solicitados em vários níveis de detalhe, a partir da linha de comando ao se chamar a simulação, como arqumento ou dentro do arquivo sumocfg. Os valores podem ser dentre vários disponíveis, os dados completos (--full-output) com a posição e estado dos veículos a cada passo da simulação por trecho do sistema viário, as medições agregadas pela velocidade em cada trecho, tempos de espera, atrasos, consumo de combustível, etc.

### Google Maps Traffic

O a difusão do uso de aplicativos de mapeamento e acesso a celulares com GPS, apresentou uma oportunidade inédita ao que antes tratava apenas de orientação e roteamento. Apple Maps, Waze, Nokia, HERE maps e Mapquest, contam com informações complementares sobre o tráfego, utilizando como fontes a própria contribuição anônima dos usuários do sistema. Dentre estes o google se destaca desde a compra do Waze em 2013, pelo grande número de usuários e por consequência contribuições para seu serviço.

O acesso ao serviço se dá através de dispositivos móveis ou pelo endereço http://maps.google.com, em sua interface o usuário pode navegar até a área de interesse e alternar entre a visulização de temas como satélite, transporte público e por fim o trânsito. Neste existem duas leituras, a padrão é a "Trânsito em tempo real" que pode ser alterada para ˜Trânsito típico", baseado no histórico da área.

Os trechos com irregularidades possuem duas propriedades, o comprimento e cor atribuída ao nível de atraso. O atraso é relativo a velocidade da via.

- verde: 70% a 100%
- laranja: 55% a 70%
- vermelho: 30% a 55%
- vermelho escuro: 0% a 30%

## 3. Metodologia

### Captura de dados

### Configuração do SUMO

## 4. Experimento

## 5. Resultados

### Comparação com contagem

## 6. Conclusão

## 7. Próximos passos

## Referências