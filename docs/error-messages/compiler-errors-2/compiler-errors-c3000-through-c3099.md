---
title: Erros do compilador C3000 a C3099
ms.date: 04/21/2019
f1_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
helpviewer_keywords:
- C3051
- C3061
- C3064
- C3067
- C3074
- C3078
- C3079
- C3081
- C3082
- C3086
- C3088
- C3089
- C3090
- C3091
- C3092
- C3093
- C3098
ms.assetid: 01b7b9cb-b351-4b5a-8cb0-1fcddb08d2ab
ms.openlocfilehash: 08c7b691d6390e6c1070fc71dff116604731ebab
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856920"
---
# <a name="compiler-errors-c3000-through-c3099"></a>Erros do compilador C3000 a C3099

Os artigos nesta seção da documentação explicam um subconjunto das mensagens de erro que são gerados pelo compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensagens de erro

|Erro|Mensagem|
|-----------|-------------|
|Erro do compilador C3000|Obsoleto.|
|[Erro do compilador C3001](compiler-error-c3001.md)|'*mensagem*': esperado um nome de diretiva de OpenMP|
|[Erro do compilador C3002](compiler-error-c3002.md)|'*name1* *nome2*': vários nomes de diretiva de OpenMP|
|[Erro do compilador C3003](compiler-error-c3003.md)|'*directive*': Nome de diretiva de OpenMP não permitido após cláusulas de diretiva|
|[Erro do compilador C3004](compiler-error-c3004.md)|'*cláusula*': cláusula inválida na OpenMP '*diretiva*' diretiva|
|[Erro do compilador C3005](compiler-error-c3005.md)|'*mensagem*': token inesperado encontrado na OpenMP '*diretiva*' diretiva|
|[Erro do compilador C3006](compiler-error-c3006.md)|'*cláusula*': cláusula de OpenMP '*diretiva*' diretiva não tem um argumento esperado|
|[Erro do compilador C3007](compiler-error-c3007.md)|'*cláusula*': cláusula de OpenMP '*diretiva*' diretiva não aceita um argumento|
|[Erro do compilador C3008](compiler-error-c3008.md)|*argumento*': argumento não possui o fechamento ')' em OpenMP '*diretiva*' diretiva|
|[Erro do compilador C3009](compiler-error-c3009.md)|'*rótulo*': ir diretamente para o bloco estruturado de OpenMP não permitido|
|[Erro do compilador C3010](compiler-error-c3010.md)|'*rótulo*': salto para fora do bloco estruturado de OpenMP não permitido|
|[Erro do compilador C3011](compiler-error-c3011.md)|assembly embutido não permitido diretamente dentro de uma região parallel|
|[Erro do compilador C3012](compiler-error-c3012.md)|'*função*': função intrínseca não permitida diretamente dentro de uma região parallel|
|[Erro do compilador C3013](compiler-error-c3013.md)|'*cláusula*': cláusula deve aparecer apenas uma vez no OpenMP '*diretiva*' diretiva|
|[Erro do compilador C3014](compiler-error-c3014.md)|esperado um loop OpenMP a seguir for '*diretiva*' diretiva|
|[Erro do compilador C3015](compiler-error-c3015.md)|inicialização em OpenMP 'instrução for' possui forma inadequada|
|[Erro do compilador C3016](compiler-error-c3016.md)|'*identificador*': variável de índice em OpenMP 'instrução for' deve possuir tipo signed integral|
|[Erro do compilador C3017](compiler-error-c3017.md)|teste de encerramento em OpenMP 'instrução for' possui forma inadequada|
|[Erro do compilador C3018](compiler-error-c3018.md)|'*identifier*': OpenMP 'for' teste ou incremento deve usar a variável de índice '*variável*'|
|[Erro do compilador C3019](compiler-error-c3019.md)|incremento de OpenMP 'instrução for' possui forma inadequada|
|[Erro do compilador C3020](compiler-error-c3020.md)|'*variável*': variável de índice do OpenMP 'loop for' não pode ser modificado no corpo do loop|
|[Erro do compilador C3021](compiler-error-c3021.md)|'*argumento*': argumento está vazio no OpenMP '*diretiva*' diretiva|
|[Erro do compilador C3022](compiler-error-c3022.md)|'*diretiva*': tipo de agenda inválida de '*diretiva*'on OpenMP'*diretiva*' diretiva|
|[Erro do compilador C3023](compiler-error-c3023.md)|'*argumento*': token inesperado encontrado no argumento de OpenMP '*diretiva*' cláusula|
|[Erro do compilador C3024](compiler-error-c3024.md)|'Schedule (Runtime)': expressão de chunk_size não é permitido|
|[Erro do compilador C3025](compiler-error-c3025.md)|'*cláusula*': expressão integral esperada|
|[Erro do compilador C3026](compiler-error-c3026.md)|'*cláusula*': expressão constante deve ser positiva|
|[Erro do compilador C3027](compiler-error-c3027.md)|'*cláusula*': expressão aritmética ou de ponteiro esperada|
|[Erro do compilador C3028](compiler-error-c3028.md)|'*membro*': somente um membro de dados estáticos ou variável pode ser usado em uma cláusula de compartilhamento de dados|
|[Erro do compilador C3029](compiler-error-c3029.md)|'*símbolo*': só pode aparecer uma vez no compartilhamento de dados cláusulas em uma diretiva de OpenMP|
|[Erro do compilador C3030](compiler-error-c3030.md)|'*identificador*': variável em '*diretiva*' cláusula/diretiva não pode ter o tipo de referência|
|[Erro do compilador C3031](compiler-error-c3031.md)|'*identificador*': variável em cláusula 'reduction' deve ter tipo aritmético escalar|
|[Erro do compilador C3032](compiler-error-c3032.md)|'*identificador*': variável em '*cláusula*'cláusula não pode ter tipo incompleto'*tipo*'|
|[Erro do compilador C3033](compiler-error-c3033.md)|'*identificador*': variável em '*cláusula*' cláusula não pode ter tipo qualificado como const|
|[Erro do compilador C3034](compiler-error-c3034.md)|OpenMP '*diretiva*' diretiva não pode ser diretamente aninhada dentro de'*diretiva*' diretiva|
|[Erro do compilador C3035](compiler-error-c3035.md)|OpenMP 'ordered' diretiva deve ligar diretamente para um 'for' ou 'parallel for' diretiva com a cláusula 'ordered'|
|[Erro do compilador C3036](compiler-error-c3036.md)|'*cláusula*': token de operador inválido em cláusula de OpenMP 'reduction'|
|[Erro do compilador C3037](compiler-error-c3037.md)|'*identificador*': variável em '*cláusula*' cláusula deve ser shared em contexto delimitador|
|[Erro do compilador C3038](compiler-error-c3038.md)|'*identificador*': variável em cláusula 'private' não pode ser uma variável de reduction em contexto delimitador|
|[Erro do compilador C3039](compiler-error-c3039.md)|'*identificador*': variável de índice em OpenMP 'instrução for' não pode ser uma variável de reduction|
|[Erro do compilador C3040](compiler-error-c3040.md)|'*identificador*': tipo de variável em cláusula 'reduction' é incompatível com o operador de reduction '*operador*'|
|[Erro do compilador C3041](compiler-error-c3041.md)|'*identificador*': variável em cláusula 'copyprivate' deve ser private em contexto delimitador|
|[Erro do compilador C3042](compiler-error-c3042.md)|cláusulas 'copyprivate' e 'nowait' não podem aparecer juntos em OpenMP '*diretiva*' diretiva|
|[Erro do compilador C3043](compiler-error-c3043.md)|Diretiva de OpenMP 'critical' não pode ser aninhada em diretiva 'critical' com o mesmo nome|
|[Erro do compilador C3044](compiler-error-c3044.md)|'section': permitida apenas aninhada diretamente sob uma diretiva de OpenMP 'sections'|
|[Erro do compilador C3045](compiler-error-c3045.md)|Esperada uma instrução composta após diretiva de OpenMP 'sections'. Faltando ' {'|
|[Erro do compilador C3046](compiler-error-c3046.md)|Faltando bloco estruturado em uma região de OpenMP '#pragma omp sections'|
|[Erro do compilador C3047](compiler-error-c3047.md)|Bloco estruturado em um região de 'sections' deve ser precedido por '#pragma omp section' de OpenMP|
|[Erro do compilador C3048](compiler-error-c3048.md)|Expressão após '#pragma omp atomic' possui forma inadequada|
|[Erro do compilador C3049](compiler-error-c3049.md)|'*argumento*': argumento inválido em cláusula 'default' de OpenMP|
|[Erro do compilador C3050](compiler-error-c3050.md)|'*classe*': uma classe ref não pode herdar de '*identificador*'|
|Erro do compilador C3051|Obsoleto.|
|[Erro do compilador C3052](compiler-error-c3052.md)|'*identificador*': variável não aparece em uma cláusula de compartilhamento de dados em uma cláusula default (none)|
|[Erro do compilador C3053](compiler-error-c3053.md)|'*identificador*': 'threadprivate' só é válido para itens de dados global ou estática|
|[Erro do compilador C3054](compiler-error-c3054.md)|'#pragma omp parallel' não é suportado atualmente em uma classe genérica ou uma função|
|[Erro do compilador C3055](compiler-error-c3055.md)|'*identificador*': símbolo não pode ser referenciado antes de ser usada na diretiva 'threadprivate'|
|[Erro do compilador C3056](compiler-error-c3056.md)|'*identificador*': símbolo não está no mesmo escopo com a diretiva 'threadprivate'|
|[Erro do compilador C3057](compiler-error-c3057.md)|'*identificador*': inicialização dinâmica de símbolos de 'threadprivate' não é suportada atualmente|
|[Erro do compilador C3058](compiler-error-c3058.md)|'*identificador*': símbolo não declarado como 'threadprivate' antes de ser usada na cláusula 'copyin'|
|[Erro do compilador C3059](compiler-error-c3059.md)|'*identificador*': símbolo 'threadprivate' não pode ser usado a '*cláusula*' cláusula|
|[Erro do compilador C3060](compiler-error-c3060.md)|'*identificador*': uma função friend não pode ser definida dentro de uma classe usando um nome qualificado (ela só deve ser declarada)|
|Erro do compilador C3061|operador '*operador*': não permitido em enumeração '*tipo*'com tipo subjacente'*tipo*'|
|[Erro do compilador C3062](compiler-error-c3062.md)|'*identificador*': enumerador requer valor porque o tipo subjacente é '*tipo*'|
|[Erro do compilador C3063](compiler-error-c3063.md)|operador '*operador*': todos os operandos devem ter o mesmo tipo de enumeração|
|Erro do compilador C3064|'*identificador*': deve ser um tipo simples ou resolver para um|
|[Erro do compilador C3065](compiler-error-c3065.md)|declaração de propriedade em escopo diferente de classe não é permitida|
|[Erro do compilador C3066](compiler-error-c3066.md)|Há várias maneiras que um objeto desse tipo pode ser chamado com estes argumentos|
|Erro do compilador C3067|uma lista de inicializadores não pode ser usada com o operador interno]|
|[Erro do compilador C3068](compiler-error-c3068.md)|'*identificador*': uma função 'naked' não pode conter objetos que possam requerer liberação caso uma exceção de C++|
|[Erro do compilador C3069](compiler-error-c3069.md)|operador '*operador*': não é permitido para tipo de enumeração|
|[Erro do compilador C3070](compiler-error-c3070.md)|'*identificador*': a propriedade não tem um método 'set'|
|[Erro do compilador C3071](compiler-error-c3071.md)|operador '*operador*' só pode ser aplicado a uma instância de uma classe ref ou um tipo de valor|
|[Erro do compilador C3072](compiler-error-c3072.md)|operador '*operador*' não pode ser aplicado a uma instância de um uso de classe ref o operador unário '% s' para converter uma instância de uma referência de classe para um tipo de identificador|
|[Erro do compilador C3073](compiler-error-c3073.md)|'*identificador*': classe ref não tem um construtor de cópia definido pelo usuário|
|Erro do compilador C3074|uma matriz não pode ser inicializada com um inicializador entre parênteses|
|[Erro do compilador C3075](compiler-error-c3075.md)|'*identificador*': não é possível inserir uma instância de um tipo de referência, '*tipo*', em um tipo de valor|
|[Erro do compilador C3076](compiler-error-c3076.md)|'*identificador*': não é possível inserir uma instância de um tipo de referência, '*tipo*', em um tipo nativo|
|[Erro do compilador C3077](compiler-error-c3077.md)|'*identificador*': um finalizador só pode ser um membro de um tipo de referência|
|Erro do compilador C3078|tamanho da matriz deve ser especificado em novas expressões|
|Erro do compilador C3079|uma lista de inicializadores não pode ser usada como o operando direito deste operador de atribuição|
|[Erro do compilador C3080](compiler-error-c3080.md)|'*finalizador*': um finalizador não pode ter um especificador de classe de armazenamento|
|Erro do compilador C3081|Obsoleto.|
|Erro do compilador C3082|Obsoleto.|
|[Erro do compilador C3083](compiler-error-c3083.md)|'*identificador*': o símbolo à esquerda de um ':: ' deve ser um tipo|
|[Erro do compilador C3084](compiler-error-c3084.md)|'*identificador*': um destruidor/finalizador não pode ser '*palavra-chave*'|
|[Erro do compilador C3085](compiler-error-c3085.md)|'*identificador*': um construtor não pode ser '*palavra-chave*'|
|Erro do compilador C3086|não é possível localizar 'std:: initializer_list': você precisa #include \<initializer_list >|
|[Erro do compilador C3087](compiler-error-c3087.md)|'*identificador*': chamada '*declaração*' já inicializa este membro|
|Erro do compilador C3088|'*classe*': construtor de atributo deve possuir argumentos formais nomeados|
|Erro do compilador C3089|'*identificador*': nome de parâmetro não corresponder ao nome do qualquer membro de dados|
|Erro do compilador C3090|'*classe*': classe de atributo não pode ser um modelo|
|Erro do compilador C3091|'*classe*': classe de atributo não pode ter classes base|
|Erro do compilador C3092|'*classe*': membro de classe de atributo não pode ser um pouco campo, 'static' ou 'const'|
|Erro do compilador C3093|'*tipo*': tipo não permitido para o membro de classe de atributo '*membro*'|
|[Erro do compilador C3094](compiler-error-c3094.md)|'*atributo*': uso anônimo não permitido|
|[Erro do compilador C3095](compiler-error-c3095.md)|'*atributo*': atributo não pode ser repetido|
|[Erro do compilador C3096](compiler-error-c3096.md)|'*atributo*': atributo é permitido em membros de classes de atributo apenas dados|
|[Erro do compilador C3097](compiler-error-c3097.md)|'*atributo*': atributo deve ser estendido com ' assembly:' ou ' módulo:'|
|Erro do compilador C3098|'*identificador*': atributo não tem nenhum construtor definido pelo usuário|
|[Erro do compilador C3099](compiler-error-c3099.md)|'*palavra-chave*': use [System::AttributeUsageAttribute] / [Windows::Foundation::Metadata::AttributeUsageAttribute] para atributos WinRT/gerenciado|

## <a name="see-also"></a>Consulte também

[C /C++ ferramentas de compilador e build erros e avisos](../compiler-errors-1/c-cpp-build-errors.md) \
[Erros do compilador C2000 - C3999](../compiler-errors-1/compiler-errors-c2000-c3999.md)
