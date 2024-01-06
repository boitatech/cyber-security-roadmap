# Introdução

Uma rede de computadores é um conjunto de dispositivos interconectados que se comunicam entre si para compartilhar recursos, dados e informações. Essas redes podem ser pequenas, como uma rede doméstica com alguns dispositivos conectados, ou grandes, como a internet, que conecta bilhões de dispositivos em todo o mundo. Elas usam protocolos e tecnologias específicas para permitir a troca de dados.

Nesse artigo vamos falar da camada física de transmissão até como ocorre a lógica de comunicação dentro dessas redes.

# Comunicação humana e seu paralelo com a comunicação de redes
A espécie humana é inerentemente social, buscando constantemente a troca de informações com seus semelhantes. E para que essa comunicação ocorra de maneira eficaz, é necessário seguir algumas diretrizes.

Tomemos como exemplo uma conversa entre duas pessoas: a comunicação entre elas requer que compartilhem o mesmo idioma, possuam habilidades de fala e audição (ou visão para aqueles com deficiência auditiva), e que o ambiente esteja propício, livre de interferências externas que possam interromper a comunicação.

Neste exemplo, alguns conceitos essenciais se destacam:

- Na comunicação vocal, o ar atua como meio de transmissão para propagar informações.
- O compartilhamento do mesmo idioma entre as pessoas implica em regras comuns, incluindo significados das palavras e normas gramaticais. Estes elementos possibilitam a codificação, transmissão, recepção e compreensão das informações trocadas.
- Um ambiente livre de interferências externas é fundamental para uma comunicação sem ruídos, preservando a integridade das informações durante a transmissão.

Esses conceitos fundamentais são extrapolados para a comunicação entre dispositivos, onde se manifestam como meios de propagação de dados, protocolos e interferências.

# Modelo OSI

Há várias maneiras de abordar a compreensão do funcionamento de uma rede de computadores. Para este propósito, usaremos o modelo OSI (Open System Interconnection), embora existam outros como o TCP/IP.

O modelo OSI segmenta a rede em sete camadas distintas, que vão desde a camada física até as abstrações das aplicações.

Na tabela abaixo mostra cada uma das camadas do modelo.

| Camada | Nome |
|:---:|:---:|
| 1 | Física |
| 2 | Enlace |
| 3 | Redes |
| 4 | Transporte |
| 5 | Sessão |
| 6 | Apresentação |
| 7 | Aplicação |

> Vamos dar uma olhada mais detalhada em algumas dessas camadas a seguir.

## Camada Física

A camada física refere-se ao meio físico usado para transmitir informações, classificado em duas categorias principais, cada uma com seus subgrupos:

1.  Transmissão Guiada
    -   Elétricos
        -   [Coaxial](https://pt.wikipedia.org/wiki/Cabo_coaxial#:~:text=O%20cabo%20coaxial%20%C3%A9%20um,e%20rodeado%20de%20uma%20blindagem)
        -   [Par t0rançado](https://pt.wikipedia.org/wiki/Cabo_de_par_tran%C3%A7ado)
    -   Óticos
        -   [Fibra óptica](https://pt.wikipedia.org/wiki/Fibra_%C3%B3ptica)
2.  Transmissão Sem Fio
    -   [Ondas eletromagnéticas](https://pt.wikipedia.org/wiki/Espectro_eletromagn%C3%A9tico)

> Para maiores detalhes sobre o funcionamento de redes sem fio recomendo a leitura dos artigos:
> - [Wireless (EN)](https://en.wikipedia.org/wiki/Wireless)
> - [Radio (EN)](https://en.wikipedia.org/wiki/Radio)

### Comunicação de dados

A comunicação ocorre basicamente pela manipulação de duas variáveis, a corrente elétrica (I) e a tensão (V).

> Esses sinais podem ser analisados matematicamente através de uma função de $$ f(t) $$ que representa o comportamento do sinal.
> A análise desses sinais se da utilizando Fourier e caso deseje se aprofundar melhor nesse assunto recomendo dar uma olhada em [séries](https://www.feis.unesp.br/Home/departamentos/engenhariaeletrica/mcap03.pdf) e [transformada](https://www.feis.unesp.br/Home/departamentos/engenhariaeletrica/mcap05.pdf) de Fourier.

### Largura de banda e taxa de transmissão

A largura de banda pode ser fisicamente compreendida como o intervalo de frequência no qual um sinal é transmitido, representado pela diferença entre a maior e a menor frequência ocupada pelo sinal, expressa pela equação $ BW = f_{max} - f_{min} $.

> Em transmissões de sinal, o corte preciso na frequência nem sempre é alcançado, resultando em um vazamento de sinal com atenuação significativa. Geralmente, esses vazamentos não são considerados na transmissão, a menos que estejamos lidando com interferências.

A largura de banda tem uma influência direta na capacidade de transmissão de bits por um canal. Em muitos casos, é possível calcular a largura de banda utilizando a Equação de Nyquist quando necessário.

$$ T_{bit/s} = 2 \times BW log_2 V $$

Onde:
- $ T_{bit/s} $ é taxa de transmissão em bits por segundo;
- $ BW $ é a largura de banda;
- $ V $ é a quantidade de níveis discretos.

Caso o canal possua interferência é necessário contabilizar a relação de sinal e ruído $ S/N $ que resulta na seguinte equação modificada.

$$ T_{bit/s} = 2 \times BW log_2 \left ( 1+\frac{S}{N} \right ) $$

> Para mais informações consulte o artigo sobre o [teorema de amostragem de Nyquist-Shannon](https://pt.wikipedia.org/wiki/Teorema_de_Nyquist-Shannon).

### Modulação e multiplexação

#### Modulação

Processo de alterar propriedades físicas do sinal para permitir a transmissão de dados é conhecido como modulação. Alguns exemplos comuns de técnicas de modulação incluem:

- **[Modulação de Amplitude (AM):](https://en.wikipedia.org/wiki/Amplitude_modulation)** Variação da amplitude do sinal portador de acordo com a amplitude do sinal modulante.
- **[Modulação de Frequência (FM):](https://en.wikipedia.org/wiki/Frequency_modulation)** Variação da frequência do sinal portador em relação ao sinal modulante.
- **[Modulação de Fase (PM ou PSK):](https://en.wikipedia.org/wiki/Phase_modulation)** Variação da fase do sinal portador de acordo com o sinal modulante.
- **[Modulação de Quadratura (QAM):](https://en.wikipedia.org/wiki/Quadrature_amplitude_modulation)** Combinação de modulação em amplitude e fase para permitir uma transmissão de dados mais eficiente.

### Multiplexação

Multiplexação é a operação de combinação de sinais em um canal de transmissão. Criando formas mais complexas de transmissão e permitindo que mais informação seja transmitida no canal.

Existem diferentes técnicas de multiplexação:

- **[Multiplexação por Divisão de Tempo (TDM - Time Division Multiplexing)](https://en.wikipedia.org/wiki/Time-division_multiplexing):** Nesse método, o tempo de transmissão é dividido em intervalos fixos e cada fonte de dados transmite durante um intervalo específico. Por exemplo, se há quatro fontes de dados, o canal é dividido em quatro intervalos de tempo e cada fonte transmite em seu intervalo designado.
- **[Multiplexação por Divisão de Frequência (FDM - Frequency Division Multiplexing)](https://en.wikipedia.org/wiki/Frequency-division_multiplexing):** Aqui, diferentes sinais são combinados para ocupar diferentes faixas de frequência dentro do espectro disponível. Cada fonte de dados é associada a uma faixa de frequência distinta, evitando interferências entre elas.
- **[Multiplexação por Divisão de Comprimento de Onda (WDM - Wavelength Division Multiplexing)](https://en.wikipedia.org/wiki/Wavelength-division_multiplexing):** Usado em sistemas ópticos, o WDM permite que múltiplos sinais ópticos sejam transmitidos simultaneamente em uma única fibra óptica, cada um usando um comprimento de onda de luz diferente.
- **[Multiplexação por Divisão de Código (CDM - Code Division Multiplexing)](https://en.wikipedia.org/wiki/Code-division_multiple_access):** Nesse método, os dados são combinados utilizando diferentes códigos de sequência, permitindo que múltiplos sinais ocupem o mesmo intervalo de tempo e frequência, mas sejam separados com base nos códigos exclusivos atribuídos a cada fonte.

## Camada Enlace

Essa camada é também conhecida como camada de acesso ao meio sendo responsável por gerenciar a comunicação confiável e eficiente entre dispositivos na mesma rede local.

Podemos dividir o enlace em duas categorias: as que utilizam conexões ponto a ponto e as que utilizam broadcast.

### Problema da comunicação simultânea

Visualize uma sala de reuniões movimentada, com várias pessoas engajadas em diálogo. Todos têm a oportunidade de expressar seus pensamentos e ouvir uns aos outros. No entanto, quando alguém conclui sua fala, muitos tentam se manifestar ao mesmo tempo.

Como podemos estabelecer um método para permitir ou restringir a fala? No cenário físico, uma solução simples é que aqueles que desejam falar levantem a mão, facilitando a organização e dando voz a um de cada vez.

No entanto, como podemos resolver essa questão em um ambiente virtual ou em rede, onde não é possível usar gestos físicos como levantar a mão?

### Canais e alocação

Quando nos deparamos com uma rede broadcast, onde vários elementos podem transmitir sinais simultaneamente, é comum ocorrer congestão na rede e perda de sinais devido à interferência mútua entre várias fontes.

Para enfrentar esse problema, optamos pela criação de canais de comunicação. Uma abordagem inicial é a distribuição equitativa da largura de banda total disponível na rede entre todos os usuários. Isso é exemplificado nas redes de telefonia E1, onde uma ligação é subdividida em 32 canais, permitindo chamadas simultâneas.

No entanto, esse método de divisão mostra-se ineficiente em situações em que há um número limitado de usuários em comparação com a quantidade de canais disponíveis. Por exemplo, ao ter 32 canais disponíveis, mas apenas dois usuários ativos, os outros 30 canais permanecerão inutilizados, resultando em uma utilização extremamente ineficiente da largura de banda.

A solução para isso é adotar a alocação dinâmica de canais. No entanto, para que isso funcione adequadamente, algumas premissas devem ser atendidas:

- **Trafego independente:** Este modelo consiste em N estações independentes, como computadores ou telefones, cada uma operada por um programa ou usuário que gera quadros para transmissão. A quantidade esperada de quadros gerados em um intervalo de duração $ \Delta t $ é $ \lambda \Delta t $, onde $ \lambda $ é uma constante representando a taxa de chegada de novos quadros. Após a geração de um quadro, a estação entra em um estado bloqueado, aguardando até que o quadro seja transmitido com sucesso.
- **Canal único:** Há um único canal disponível para todas as comunicações, permitindo que todas as estações transmitam e recebam por ele. Embora todas as estações sejam consideradas igualmente capazes, os protocolos podem atribuir diferentes papéis (como prioridades) a elas.
- **Colisões observáveis:** Se dois quadros forem transmitidos simultaneamente, eles se sobreporão no tempo, resultando em uma colisão que adultera o sinal. Todas as estações são capazes de detectar colisões. Um quadro que tenha sofrido colisão precisará ser retransmitido posteriormente. Não existem outros erros além daqueles gerados por colisões.
- **Tempo contínuo ou segmentado:** O tempo pode ser considerado contínuo, permitindo que a transmissão do quadro comece a qualquer momento. Alternativamente, o tempo pode ser dividido em intervalos discretos (slots). As transmissões de quadros sempre iniciam no início de um slot. Um slot pode conter 0, 1 ou mais quadros, indicando um slot ocioso, uma transmissão bem-sucedida ou uma colisão, respectivamente.
- **Detecção de portadora ou sem detecção de portadora:** Com a premissa de detecção de portadora, as estações podem detectar se o canal está em uso antes de tentar transmitir. Se o canal estiver ocupado, nenhuma estação tentará utilizá-lo até que ele fique livre. Sem a detecção de portadora, as estações não conseguem detectar a ocupação do canal antes da tentativa de transmissão. Elas simplesmente prosseguem com a transmissão e só posteriormente determinam se foi bem-sucedida ou não.

> Caso esteja interessado em saber mais sobre as diferentes formas de resolver esses problemas sugiro dar uma pesquisada sobre os protocolos e conceitos [ALOHA](https://pt.wikipedia.org/wiki/ALOHAnet), [CSMA](https://www.geeksforgeeks.org/carrier-sense-multiple-access-csma/), [BIT-MAP](https://www.geeksforgeeks.org/collision-free-protocols-in-computer-network/) e [TREE WALK](https://copyprogramming.com/howto/the-adaptive-tree-walk-protocol).

### Ethernet

Basicamente a forma de comunicação mais comum utilizada, mas ela pode ser dividida de duas formas:
- **Clássica:** que resolve o problema de acessos múltiplos utilizando as diferentes técnicas de alocação de canais apresentadas ou referenciadas anteriormente (Descontinuada).
- **Comutada:** utilizando um dispositivo de comutação (switch) que cria canais de comunicação ponto a ponto (modelo atual).

### MAC Ethernet

O endereço MAC (Media Access Control) é um identificador exclusivo atribuído a cada dispositivo de comunicação em uma rede. Ele é essencial para o encaminhamento de pacotes entre dispositivos dentro dessa rede. Esse endereço é pré-definido pelos fabricantes nas placas de rede (Network Interface Card), porém, pode ser alterado de forma lógica, o que abre brechas para técnicas como o MAC Spoofing.

O endereço MAC é constituído por 12 caracteres alfanuméricos, que podem ser representados como "00:00:00:00:00:00", incluindo caracteres de 0 a 9 e letras de A a F, representando valores hexadecimais.

> As atribuições de endereços MAC válidos são regidos pela [Registration Authority](https://standards.ieee.org/products-programs/regauth/) do [IEEE](https://www.ieee.org/).

#### Estrutura de um endereço MAC

| Bytes | 8 | 6 | 6 | 2 | 0-1500 | 0-46 | 4 |
|---|---|---|---|---|---|---|---|
| Componente | Preâmbulo | Endereço de destino | Endereço de origem | Tipo | Dados | Preenchimento | Check-sum |

> Os padrões de comunicação em redes locais e metropolitanas são estabelecidas pelas normas da série IEEE 802.x.

> Os protocolos de redes sem fio adicionam diversas complexidades e são definidos pelo normativo IEEE 802.11 e IEEE 802.1x.

> É possível o controle do tamanho do pacote através da alteração do [MTU](https://pt.wikipedia.org/wiki/Unidade_m%C3%A1xima_de_transmiss%C3%A3o).

## Camada de Redes

## Camada de Transporte

## Aplicação

