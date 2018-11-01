---
title: Erros do Compilador C2300 a C2399
ms.date: 11/17/2017
f1_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
helpviewer_keywords:
- C2303
- C2304
- C2305
- C2306
- C2314
- C2321
- C2323
- C2328
- C2329
- C2330
- C2331
- C2335
- C2336
- C2339
- C2340
- C2342
- C2343
- C2347
- C2354
- C2358
- C2359
- C2363
- C2366
- C2367
- C2398
- C2399
ms.assetid: 07ca45b5-b2f0-4049-837b-40a7a3caed88
ms.openlocfilehash: 6f95ec90a08b842259a383d7bfc6af2cba119e14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580629"
---
# <a name="compiler-errors-c2300-through-c2399"></a>Erros do Compilador C2300 a C2399

Os artigos nesta seção da documentação explicam um subconjunto das mensagens de erro que são gerados pelo compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensagens de erro

|Erro|Mensagem|
|-----------|-------------|
|[Erro do compilador C2300](compiler-error-c2300.md)|'*classe*': classe não tem um destruidor chamado ' ~*classe*'|
|[Erro do compilador C2301](compiler-error-c2301.md)|esquerda de ' -> ~*identificador*' deve apontar para a classe/struct/union|
|[Erro do compilador C2302](compiler-error-c2302.md)|esquerda de '. ~*identificador*' deve ter o tipo de classe/struct/union|
|C2303 de erro do compilador|Manipulação de exceção estruturada não pode ser usada em uma corrotina|
|C2304 de erro do compilador|'*palavra-chave*' não pode ser usado dentro de um bloco catch|
|C2305 de erro do compilador|'*arquivo*' não contém informações de depuração para este módulo|
|C2306 de erro do compilador|'*arquivo*' não contém as informações de depuração mais recentes para este módulo|
|[Erro do compilador C2307](compiler-error-c2307.md)|pragma *diretiva* devem ser movidos fora da função se compilação incremental estiver habilitada|
|[Erro do compilador C2308](compiler-error-c2308.md)|concatenação de cadeias de caracteres incompatíveis|
|[Erro do compilador C2309](compiler-error-c2309.md)|manipulador catch esperava uma declaração de exceção entre parênteses|
|[Erro do compilador C2310](compiler-error-c2310.md)|manipuladores catch devem especificar um tipo|
|[Erro do compilador C2311](compiler-error-c2311.md)|'*tipo*': é capturado por '...' na linha *número*|
|[Erro do compilador C2312](compiler-error-c2312.md)|'*type1*': é capturado por '*type2*' na linha *número*|
|[Erro do compilador C2313](compiler-error-c2313.md)|'*type1*': é capturado por referência ('*type2*') na linha *número*|
|C2314 de erro do compilador|palavra-chave '*palavrachave1*' é preterida: use '*keyword2*' em vez disso|
|[Erro do compilador C2315](compiler-error-c2315.md)|'*type1*': referência é capturada por '*type2*' na linha *número*|
|[Erro do compilador C2316](compiler-error-c2316.md)|'*tipo*': não pode ser detectado porque o destruidor e/ou o construtor de cópia é inacessíveis ou foram excluídos|
|[Erro do compilador C2317](compiler-error-c2317.md)|'try' começando na linha de bloco '*número*' não possui manipuladores catch|
|[Erro do compilador C2318](compiler-error-c2318.md)|nenhum bloco try associado com este manipulador catch|
|[Erro do compilador C2319](compiler-error-c2319.md)|' try/catch' deve ser seguido por uma instrução composta. Faltando ' {'|
|[Erro do compilador C2320](compiler-error-c2320.md)|esperado ':' a seguir um especificador de acesso '*especificador*'|
|C2321 de erro do compilador|'*identificador*' é uma palavra-chave e não pode ser usado neste contexto|
|[Erro do compilador C2322](compiler-error-c2322.md)|'*identificador*': endereço de dllimport '*identificador*' não é estático|
|C2323 de erro do compilador|'*identificador*': operador não membro novo ou excluir funções não podem ser declaradas estáticos ou em um namespace diferente do namespace global|
|[Erro do compilador C2324](compiler-error-c2324.md)|'*identificador*': inesperado à direita de ':: ~'|
|[Erro do compilador C2325](compiler-error-c2325.md)|'*type1*': tipo inesperado à direita de ' -> ~': esperado '*type2*'|
|[Erro do compilador C2326](compiler-error-c2326.md)|'*declarador*': função não é possível acessar '*identificador*'|
|[Erro do compilador C2327](compiler-error-c2327.md)|'*identificador*': não é um nome de tipo, static ou enumerador|
|C2328 de erro do compilador|'*palavra-chave*': palavra-chave ainda não é suportado|
|C2329 de erro do compilador|'*identificador*': __ptr64 não disponível a ponteiros para funções|
|C2330 de erro do compilador|'implementation_key ()' só é válido em uma região limitada por #pragma start_map_region/stop_map_region|
|C2331 de erro do compilador|acesso a '*identificador*'agora definido como'*accessibility1*', ele foi definido anteriormente para ser'*accessibility2*'|
|[Erro do compilador C2332](compiler-error-c2332.md)|'*typedef*': faltando nome de marca|
|[Erro do compilador C2333](compiler-error-c2333.md)|'*função*': erro na declaração de função; ignorando corpo da função|
|[Erro do compilador C2334](compiler-error-c2334.md)|tokens inesperados anteriores '*token*'; ignorando corpo aparente de função|
|C2335 de erro do compilador|'*identificador*': um tipo não pode ser introduzido em uma lista de parâmetros de função|
|C2336 de erro do compilador|'*tipo*': tipo inválido|
|[Erro do compilador C2337](compiler-error-c2337.md)|'*atributo*': atributo não encontrado|
|[Erro do compilador C2338](compiler-error-c2338.md)|*(mensagem de erro do provedor externo)*|
|C2339 de erro do compilador|'*identificador*': tipo inválido em IDL inserida|
|C2340 de erro do compilador|'*identificador*': 'static' só pode ser usado dentro de uma definição de classe|
|[Erro do compilador C2341](compiler-error-c2341.md)|'*seção*': segmento deve ser definido usando #pragma data_seg, code_seg ou section antes de usar|
|C2342 de erro do compilador|Erro de sintaxe: qualificadores de tipo conflitante|
|C2343 de erro do compilador|'*seção*': atributos de seção conflitantes|
|[Erro do compilador C2344](compiler-error-c2344.md)|align (*número*): alinhamento deve ser uma potência de dois|
|[Erro do compilador C2345](compiler-error-c2345.md)|align (*número*): valor de alinhamento inválido|
|[Erro do compilador C2346](compiler-error-c2346.md)|'*função*' não pode ser compilado como nativo: '*explicação*'|
|C2347 de erro do compilador|Obsoleto.|
|[Erro do compilador C2348](compiler-error-c2348.md)|'*tipo*': não é uma agregação C-style, não pode ser exportada em IDL inserida|
|[Erro do compilador C2349](compiler-error-c2349.md)|'*função*' não pode ser compilado como gerenciado: '*explicação*'; use #pragma não gerenciados|
|[Erro do compilador C2350](compiler-error-c2350.md)|'*identificador*' não é um membro estático|
|[Erro do compilador C2351](compiler-error-c2351.md)|sintaxe de inicialização do construtor de C++ obsoleta|
|[Erro do compilador C2352](compiler-error-c2352.md)|'*identificador*': chamada inválida a função de membro não estático|
|[Erro do compilador C2353](compiler-error-c2353.md)|especificação de exceção não é permitida|
|C2354 de erro do compilador|Obsoleto.|
|[Erro do compilador C2355](compiler-error-c2355.md)|'this': só pode ser referenciada dentro de funções de membro não estático ou inicializadores de membro de dados não estáticos|
|[Erro do compilador C2356](compiler-error-c2356.md)|segmento de inicialização não deve mudar durante unidade de tradução|
|[Erro do compilador C2357](compiler-error-c2357.md)|'*identificador*': deve ser uma função do tipo '*tipo*'|
|C2358 de erro do compilador|'*identificador*': uma propriedade estática não pode ser definida fora de uma definição de classe|
|C2359 de erro do compilador|Obsoleto.|
|[Erro do compilador C2360](compiler-error-c2360.md)|inicialização de '*identificador*' é ignorada por rótulo 'case'|
|[Erro do compilador C2361](compiler-error-c2361.md)|inicialização de '*identificador*' é ignorada por rótulo 'default'|
|[Erro do compilador C2362](compiler-error-c2362.md)|inicialização de '*identificador*' é ignorada por ' goto *rótulo*'|
|C2363 de erro do compilador|função de limite numérico intrínseco do compilador requer um argumento de cadeia de caracteres literal|
|[Erro do compilador C2364](compiler-error-c2364.md)|'*tipo*': tipo inválido para atributo personalizado|
|[Erro do compilador C2365](compiler-error-c2365.md)|'*member1*': redefinição; definição anterior era '*membro2*'|
|C2366 de erro do compilador|'*identificador*': redefinição; especificadores implementation_key diferentes|
|C2367 de erro do compilador|Obsoleto.|
|[Erro do compilador C2368](compiler-error-c2368.md)|'*identificador*': redefinição; especificadores de alocação diferentes|
|[Erro do compilador C2369](compiler-error-c2369.md)|'*identificador*': redefinição; subscritos diferentes|
|[Erro do compilador C2370](compiler-error-c2370.md)|'*identificador*': redefinição; classe de armazenamento diferentes|
|[Erro do compilador C2371](compiler-error-c2371.md)|'*identificador*': redefinição; tipos básicos diferentes|
|[Erro do compilador C2372](compiler-error-c2372.md)|'*identificador*': redefinição; tipos diferentes de indireção|
|[Erro do compilador C2373](compiler-error-c2373.md)|'*identificador*': redefinição; modificadores de tipo diferente|
|[Erro do compilador C2374](compiler-error-c2374.md)|'*identificador*': redefinição; várias inicializações|
|[Erro do compilador C2375](compiler-error-c2375.md)|'*identificador*': redefinição; vínculo diferente|
|[Erro do compilador C2376](compiler-error-c2376.md)|'*identificador*': redefinição; alocação based diferente|
|[Erro do compilador C2377](compiler-error-c2377.md)|'*identificador*': redefinição; typedef não pode ser sobrecarregado com nenhum outro símbolo|
|[Erro do compilador C2378](compiler-error-c2378.md)|'*identificador*': redefinição; símbolo não pode ser sobrecarregado com um typedef|
|[Erro do compilador C2379](compiler-error-c2379.md)|parâmetro formal *número* possui tipo diferente quando promovido|
|[Erro do compilador C2380](compiler-error-c2380.md)|tipo (s) precedendo '*identificador*' (construtor com tipo de retorno, ou redefinição inválida do nome de classe atual?)|
|[Erro do compilador C2381](compiler-error-c2381.md)|'*identificador*': redefinição; '__declspec(noreturn)' ou '[[noreturn]]' difere|
|[Erro do compilador C2382](compiler-error-c2382.md)|'*identificador*': redefinição; especificações de exceção diferentes|
|[Erro do compilador C2383](compiler-error-c2383.md)|'*identificador*': argumentos padrão não são permitidos neste símbolo|
|[Erro do compilador C2384](compiler-error-c2384.md)|'*membro*': não é possível aplicar thread_local ou __declspec(thread) a um membro de uma classe gerenciada/WinRT|
|[Erro do compilador C2385](compiler-error-c2385.md)|acesso ambíguo de '*membro*'|
|[Erro do compilador C2386](compiler-error-c2386.md)|'*identificador*': um símbolo com este nome já existe no escopo atual|
|[Erro do compilador C2387](compiler-error-c2387.md)|'*identificador*': classe base ambígua|
|[Erro do compilador C2388](compiler-error-c2388.md)|'*identificador*': um símbolo não pode ser declarado com __declspec(appdomain) e __declspec(process)|
|[Erro do compilador C2389](compiler-error-c2389.md)|'*operador*': operando inválido 'nullptr'|
|[Erro do compilador C2390](compiler-error-c2390.md)|'*identificador*': classe de armazenamento incorreta*especificador*'|
|[Erro do compilador C2391](compiler-error-c2391.md)|'*identificador*': 'friend' não pode ser usado durante a definição de tipo|
|[Erro do compilador C2392](compiler-error-c2392.md)|'*member1*': covariante retorna tipos não têm suporte em tipos/WinRT gerenciados, caso contrário '*membro2*' poderia ser substituído|
|[Erro do compilador C2393](compiler-error-c2393.md)|'*símbolo*': símbolo per-appdomain não pode ser alocado no segmento '*segmento*'|
|[Erro do compilador C2394](compiler-error-c2394.md)|'*tipo*:: operador *operador*': operador CLR/WinRT não é válido. Pelo menos um parâmetro deve ser um destes tipos: ' t ^', ' t ^ %', ' t ^ &', onde T = '*tipo*'|
|[Erro do compilador C2395](compiler-error-c2395.md)|'*tipo*:: operador *operador*': operador CLR/WinRT não é válido. Pelo menos um parâmetro deve ser um destes tipos: ' t ', ' t %', ' t &', ' t ^', ' t ^ %', ' t ^ &', onde T = '*tipo*'|
|[Erro do compilador C2396](compiler-error-c2396.md)|'*type1*:: operador *type2*': função de conversão definida pelo usuário CLR/WinRT não é válida. Deve converter de ou converter em: ' t ^', ' t ^ %', ' t ^ &', onde T = '*type1*'|
|[Erro do compilador C2397](compiler-error-c2397.md)|conversão de '*type1*'para'*type2*' requer uma conversão redutora|
|C2398 de erro do compilador|Elemento '*número*': conversão de '*type1*'para'*type2*' requer uma conversão redutora|
|C2399 de erro do compilador|Obsoleto.|
