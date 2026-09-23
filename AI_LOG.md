# Uso de IA

Pedido realizado

Utilizei uma ferramenta de IA para auxiliar na compreensão da atividade e na implementação das alterações solicitadas nos arquivos C++ e Python.

Os principais pedidos feitos foram:

Identificar onde deveria ser lançada a exceção FalhaCalibracao.
Explicar a ordem correta das capturas de FalhaCalibracao e FalhaLeitura.
Auxiliar na implementação do tratamento da exceção em C++ e Python.
Auxiliar na elaboração da documentação das decisões da prática.
Orientações aceitas

Foi aceita a orientação de lançar FalhaCalibracao na função adquirir quando a fonte estivesse disponível, mas não estivesse calibrada.

Também foi aceita a orientação de capturar FalhaCalibracao antes de FalhaLeitura, pois FalhaCalibracao deriva de FalhaLeitura.

A orientação de manter a liberação da sessão por meio do RAII no C++ e do finally no Python também foi aceita.

Orientações rejeitadas

Não foram realizadas alterações em partes que o enunciado determinava que deveriam ser preservadas, como Sessao, lerServico, ler_servico e os testes.

Justificativa

As orientações aceitas foram verificadas de acordo com o enunciado e com o funcionamento esperado do programa.

Após as alterações, foi executado o comando:

make test ETAPA=A

O resultado foi:

OK pratica integrada A (C++)

OK pratica integrada A (Python)