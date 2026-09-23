# Decisoes da pratica A

1. Falta de calibracao: quem lanca, propaga e recupera?
C++

Na falta de calibracao, a funcao adquirir e responsavel por lancar a excecao FalhaCalibracao.

A funcao lerServico apenas chama adquirir, portanto nao trata a excecao e apenas a propaga para quem a chamou.

A funcao executarCiclo e responsavel por recuperar a falha. Ela captura primeiro FalhaCalibracao e retorna false, valor 0 e o motivo "calibracao".

O caminho da chamada e:

executarCiclo -> lerServico -> adquirir

Portanto, adquirir lanca a excecao, lerServico propaga e executarCiclo recupera a falha.

Python

No Python, acontece a mesma coisa. A funcao adquirir lanca FalhaCalibracao quando a fonte esta disponivel, mas nao esta calibrada.

A funcao ler_servico apenas chama adquirir, portanto a excecao e propagada ate executar_ciclo.

A funcao executar_ciclo captura FalhaCalibracao e retorna False, 0, "calibracao".

O caminho da chamada e:

executar_ciclo -> ler_servico -> adquirir

Assim, o comportamento e equivalente ao C++.

2. Ordem das capturas e liberacao da sessao

A captura de FalhaCalibracao vem antes da captura de FalhaLeitura porque FalhaCalibracao e uma classe derivada de FalhaLeitura.

Se FalhaLeitura fosse capturada primeiro, ela tambem capturaria uma FalhaCalibracao. Dessa forma, o programa nao conseguiria identificar especificamente que o problema foi a falta de calibracao.

No C++, a sessao e liberada automaticamente pelo destrutor de Sessao. Quando adquirir lanca a excecao, a funcao e encerrada e o destrutor de Sessao e executado antes que a excecao chegue ao catch de executarCiclo.

No Python, a sessao e liberada pelo bloco finally dentro de adquirir. O comando sessao.fechar() e executado mesmo quando ocorre uma excecao, antes de ela chegar ao except de executar_ciclo.

Assim, nas duas linguagens, o recurso e liberado antes da captura da excecao.

3. Contrato comum para as duas fontes

FonteNivel e FonteConstante podem ser consultadas pelo mesmo contrato porque ambas implementam IFonteLeitura.

Esse contrato define que uma fonte deve fornecer os metodos valor() e unidade(). Dessa forma, as funcoes de aquisicao nao precisam conhecer os detalhes de cada fonte.

No make run, podemos observar:

Painel: 20

e

Fonte simulada: 42.5 %

O valor 20 esta relacionado a FonteNivel, que utiliza o valor do SensorNivel.

Ja o valor 42.5 % e fornecido pela FonteConstante.

Mesmo sendo fontes diferentes, ambas podem ser utilizadas pelo mesmo fluxo de leitura porque seguem o contrato IFonteLeitura
