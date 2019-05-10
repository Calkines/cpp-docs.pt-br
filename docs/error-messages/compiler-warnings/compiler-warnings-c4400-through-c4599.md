---
title: Avisos do compilador C4400 a C4599
ms.date: 04/21/2019
f1_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4452
- C4453
- C4454
- C4455
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
helpviewer_keywords:
- C4413
- C4415
- C4416
- C4417
- C4418
- C4419
- C4421
- C4423
- C4424
- C4425
- C4426
- C4427
- C4438
- C4442
- C4443
- C4444
- C4446
- C4447
- C4448
- C4449
- C4450
- C4451
- C4452
- C4453
- C4454
- C4455
- C4456
- C4457
- C4459
- C4472
- C4474
- C4475
- C4476
- C4478
- C4480
- C4482
- C4483
- C4491
- C4492
- C4493
- C4494
- C4495
- C4496
- C4497
- C4498
- C4499
- C4509
- C4519
- C4531
- C4542
- C4562
- C4568
- C4569
- C4573
- C4574
- C4575
- C4582
- C4583
- C4585
- C4586
- C4587
- C4588
- C4591
- C4592
- C4593
- C4594
- C4595
ms.assetid: b07850a5-ae89-48ea-bf9a-f0e30939f9b9
ms.openlocfilehash: 7dd09e6f31592f6d4b62b94d8d3256fe1a432010
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857413"
---
# <a name="compiler-warnings-c4400-through-c4599"></a>Avisos do compilador C4400 a C4599

Os artigos nesta seção da documentação explicam um subconjunto das mensagens de aviso são geradas pelo compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Mensagens de aviso

|Aviso|Mensagem|
|-------------|-------------|
|[Aviso do compilador (nível 1) C4600](compiler-warning-level-1-c4600.md)|#pragma '*nome da macro*': espera-se uma cadeia de caracteres não vazia válida|
|[Aviso do compilador (nível 4) C4400](../../error-messages/compiler-warnings/compiler-warning-level-4-c4400.md)|'*tipo*': não há suporte para qualificadores const/volatile neste tipo|
|[Aviso do compilador (nível 1) C4401](../../error-messages/compiler-warnings/compiler-warning-level-1-c4401.md)|'*campo de bits*': membro é campo de bits|
|[Aviso do compilador (nível 1) C4402](../../error-messages/compiler-warnings/compiler-warning-level-1-c4402.md)|deve usar operador PTR|
|[Aviso do compilador (nível 1) C4403](../../error-messages/compiler-warnings/compiler-warning-level-1-c4403.md)|operador PTR inválido|
|[Aviso do compilador (nível 3) C4404](../../error-messages/compiler-warnings/compiler-warning-level-3-c4404.md)|ponto em diretiva ignorado|
|[Aviso do compilador (nível 1) C4405](../../error-messages/compiler-warnings/compiler-warning-level-1-c4405.md)|'*identificador*': identificador é palavra reservada|
|[Aviso do compilador (nível 1) C4406](../../error-messages/compiler-warnings/compiler-warning-level-1-c4406.md)|operando em diretiva ignorado|
|[Aviso do compilador (nível 1) C4407](../../error-messages/compiler-warnings/compiler-warning-level-1-c4407.md)|conversão entre diferente ponteiro para representações de membro, compilador pode gerar código incorreto|
|[Aviso do compilador (nível 4) C4408](../../error-messages/compiler-warnings/compiler-warning-level-4-c4408.md)|anônimo ' struct&#124;union' não declarou nenhum membro de dados|
|[Aviso do compilador (nível 1) C4409](../../error-messages/compiler-warnings/compiler-warning-level-1-c4409.md)|tamanho de instrução inválido|
|[Aviso do compilador (nível 1) C4410](../../error-messages/compiler-warnings/compiler-warning-level-1-c4410.md)|tamanho inválido para operando|
|[Aviso do compilador (nível 1) C4411](../../error-messages/compiler-warnings/compiler-warning-level-1-c4411.md)|'*identificador*': símbolo resolve para registro de deslocamento|
|[Aviso do compilador (nível 2) C4412](../../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)|'*função*': assinatura de função contém o tipo '*tipo*'; Objetos de C++ são seguros para passar entre código puro e combinado ou nativo.|
|C4413 de aviso do compilador|'classname::member': membro de referência é inicializado para um temporário que não persiste após o construtor encerrar|
|[Aviso do compilador (nível 3) C4414](../../error-messages/compiler-warnings/compiler-warning-level-3-c4414.md)|'*função*': salto short para função convertido para near|
|Aviso do compilador (nível 1) C4415|duplicate __declspec(code_seg('*name*'))|
|Aviso do compilador (nível 1) C4416|__declspec(code_seg(...)) contém a cadeia de caracteres vazia: ignorado|
|Aviso do compilador (nível 1) C4417|uma instanciação de modelo explícitos não pode ter __declspec(code_seg(...)): ignorado|
|Aviso do compilador (nível 1) C4418|__declspec(code_seg(...)) ignorada na enumeração|
|Aviso do compilador (nível 3) C4419|'*símbolo*'não tem nenhum efeito quando aplicado à ref class privada'*classe*'.|
|[Aviso do compilador (nível 1) C4420](../../error-messages/compiler-warnings/compiler-warning-level-1-c4420.md)|'*checked_operator*': operador não está disponível, usando '*operador*'; verificação de tempo de execução pode ser comprometida|
|Aviso do compilador (nível 3) C4421|'*parâmetro*': um parâmetro de referência em uma função retomável é potencialmente não seguro|
|Aviso do compilador (nível 3) C4423|'std:: bad_alloc': será capturado por classe ('*tipo*') na linha *número*|
|Aviso do compilador (nível 3) C4424|Catch para '*type1*'precedido por'*type2*' na linha *número*; imprevisível poderá ocorrer um comportamento se 'std:: bad_alloc' for lançada|
|Aviso do compilador (nível 1) C4425|Uma anotação SAL não pode ser aplicada a '...'|
|Aviso do compilador (nível 1) C4426|os sinalizadores de otimização foram alterados após incluir o cabeçalho, pode ser devido a #pragma optimize)|
|Aviso do compilador (nível 1) C4427|'*operador*': estouro na divisão constante, comportamento indefinido|
|[Aviso do compilador (nível 4) C4429](../../error-messages/compiler-warnings/compiler-warning-level-4-c4429.md)|possíveis incompleto ou formado incorretamente-nome de caractere universal|
|[Aviso (erro) C4430 do compilador](../../error-messages/compiler-warnings/compiler-warning-c4430.md)|faltando especificador de tipo - int assumido. Observação: C++ não suporta default-int|
|[Aviso do compilador (nível 4) C4431](../../error-messages/compiler-warnings/compiler-warning-level-4-c4431.md)|faltando especificador de tipo - int assumido. Observação: C não suporta default-int|
|[Aviso do compilador (nível 4) C4434](../../error-messages/compiler-warnings/compiler-warning-level-4-c4434.md)|um construtor static deve possuir acessibilidade private; alterando para acesso privado|
|[Aviso do compilador (nível 4) C4435](../../error-messages/compiler-warnings/compiler-warning-level-4-c4435.md)|'*derived_class*': Layout do objeto em/vd2 será alterado devido à base virtual '*base_class*'|
|[Aviso do compilador (nível 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)|dinâmico\_conversão de base virtual '*base_class*'para'*derived_class*' no construtor ou destruidor poderia falhar com o objeto parcialmente construído|
|[Aviso do compilador (nível 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)|dinâmico\_conversão de base virtual '*base_class*'para'*derived_class*' poderia falhar em alguns contextos|
|C4438 de aviso do compilador|'*função*': não pode ser chamado com segurança /await: clrcompat modo. Se '*função*' chamadas para o CLR-lo pode resultar em corrupção de cabeçalhos CLR|
|[Aviso (erro) C4439 do compilador](../../error-messages/compiler-warnings/compiler-warning-c4439.md)|'*função*': definição de função com um tipo gerenciado na assinatura deve ter um clrcall convenção de chamada|
|[Aviso do compilador (nível 1) C4440](../../error-messages/compiler-warnings/compiler-warning-level-1-c4440.md)|redefinição de convenção de chamada de '*calling_convention1*'para'*calling_convenction2*' ignorado|
|[Aviso do compilador (nível 1) C4441](../../error-messages/compiler-warnings/compiler-warning-level-1-c4441.md)|convenção de chamada de '*calling_convention1*' ignorado; '*calling_convention2*' usado em vez disso|
|Aviso do compilador (nível 1) C4442|terminador nulo inserido no argumento de Annotation.  Valor será truncado.|
|Aviso do compilador (nível 1) C4443|parâmetro pragma esperado como ser '0', '1' ou '2'|
|Aviso do compilador (nível 3) C4444|'*identificador*': unaligned' de nível superior não está implementado neste contexto|
|[Aviso do compilador (nível 1) C4445](../../error-messages/compiler-warnings/compiler-warning-level-1-c4445.md)|'*função*': em um ' WinRT&#124;gerenciado ' tipo de um método virtual não pode ser privado|
|Aviso do compilador (nível 1) C4446|'*tipo*': não é possível mapear o membro '*Nome1*' para este tipo devido a conflito com o nome do tipo. O método foi renomeado para '*nome2*'|
|Aviso do compilador (nível 1) C4447|assinatura 'main' encontrada sem modelo de threading. Considere o uso de ' int principal (Platform:: array\<Platform:: String ^ > ^ args)'.|
|C4448 de aviso do compilador|'*tipo*1' não tem uma interface padrão especificada nos metadados. Separação: '*type2*', que pode falhar em tempo de execução.|
|C4449 de aviso do compilador|'*tipo*' um tipo não selado deve ser marcado como '[WebHostHidden]'|
|C4450 de aviso do compilador|'*type1*'deve ser marcado como '[WebHostHidden]' porque deriva de'*type2*'|
|Aviso do compilador (nível 4) C4451|'classname1::member': O uso de classe ref classname2::member dentro deste contexto pode levar a empacotamento inválido do objeto entre contextos|
|Aviso do compilador (nível 1) C4452|'*identificador*': tipo público não pode estar em escopo global. Ele deve ser em um namespace que é um filho do nome do arquivo de saída. winmd.|
|Aviso do compilador (nível 1) C4453|'*type*': Um tipo de '[WebHostHidden]' não deve ser usado na superfície publicada de um tipo público que não seja '[WebHostHidden]'|
|Aviso do compilador (nível 1) C4454|'*função*' está sobrecarregado por mais do que o número de parâmetros de entrada sem ter [DefaultOverload] especificado. Separação '*declaração*' como a sobrecarga padrão|
|Aviso do compilador (nível 1) C4455|' operador *operador*': identificadores de sufixos literais que não começam com um sublinhado são reservados|
|[Aviso do compilador (nível 4) C4456](compiler-warning-level-4-c4456.md)|declaração de '*identificador*' oculta uma declaração local anterior|
|[Aviso do compilador (nível 4) C4457](compiler-warning-level-4-c4457.md)|declaração de '*identificador*' oculta o parâmetro de função|
|[Aviso do compilador (nível 4) C4458](compiler-warning-level-4-c4458.md)|declaração de '*identificador*' oculta o membro da classe|
|[Aviso do compilador (nível 4) C4459](compiler-warning-level-4-c4459.md)|declaração de '*identificador*' oculta uma declaração global|
|[Aviso do compilador (nível 4) C4460](../../error-messages/compiler-warnings/compiler-warning-level-4-c4460.md)|' WinRT&#124;gerenciado ' operador '*operador*', tem o parâmetro passado por referência. ' WinRT&#124;gerenciado ' operador '*operador*' tem semânticas diferentes do C++ operador '*cpp_operator*', você pretendia passar por valor?|
|[Aviso do compilador (nível 1) C4461](../../error-messages/compiler-warnings/compiler-warning-level-1-c4461.md)|'*classname*': essa classe tem um finalizador '! *finalizador*', mas nenhum destruidor ' ~*dtor*'|
|[Aviso do compilador (nível 1, erro) C4462](../../error-messages/compiler-warnings/compiler-warning-level-1-c4462.md)|'*tipo*': não é possível determinar o GUID do tipo. O programa poderá falhar no tempo de execução.|
|[Aviso do compilador (nível 4) C4463](compiler-warning-level-4-c4463.md)|estouro; atribuição de '*valor*'para o campo de bits que pode conter apenas valores de'*min_value*'para'*max_value*'|
|[Aviso do compilador (nível 4) C4464](../../error-messages/compiler-warnings/c4464.md)|caminho de inclusão relativo contém '.. '|
|[Aviso do compilador (nível 1) C4470](../../error-messages/compiler-warnings/compiler-warning-level-1-c4470.md)|pragmas de controle de ponto flutuante ignorados sob /clr|
|[Aviso do compilador (nível 4) C4471](compiler-warning-level-4-c4471.md)|'*enumeração*': declaração de encaminhamento de uma enumeração sem escopo deve ter um tipo subjacente (int assumido)|
|Aviso do compilador (nível 1) C4472|'*identificador*' é uma enumeração nativa: adicionar um especificador de acesso (pública/privada) para declarar um ' WinRT&#124;gerenciado ' enum|
|[Aviso do compilador (nível 1) C4473](c4473.md)|'*função*': não há argumentos suficientes passado para a cadeia de caracteres de formato|
|Aviso do compilador (nível 3) C4474|'*função*': muitos argumentos passados para a cadeia de caracteres de formato|
|Aviso do compilador (nível 3) C4475|'*função*': modificador de comprimento '*modificador*'não pode ser usado com o caractere de campo do tipo'*caractere*' no especificador de formato|
|Aviso do compilador (nível 3) C4476|'*função*': caractere de campo de tipo desconhecido '*caractere*' no especificador de formato|
|[Aviso do compilador (nível 1) C4477](c4477.md)|'*função*': cadeia de caracteres de formato '*cadeia de caracteres*'requer um argumento do tipo'*tipo*', mas o argumento variadic *número* tem o tipo '*tipo*'|
|Aviso do compilador (nível 1) C4478|'*função*': os espaços reservados posicionais e não posicionais não podem ser misturados na mesma cadeia de caracteres de formato|
|Aviso (erro) C4480 do compilador|extensão não padrão usada: especificação de tipo subjacente para enumeração '*enumeração*'|
|[Aviso do compilador (nível 4) C4481](../../error-messages/compiler-warnings/compiler-warning-level-4-c4481.md)|extensão não padrão usada: especificador de substituição '*palavra-chave*'|
|C4482 de aviso do compilador|extensão não padrão usada: enum '*enumeração*' usado no nome qualificado|
|Aviso do compilador (nível 1, erro) C4483|Erro de sintaxe: esperada palavra-chave C++|
|[Aviso (erro) C4484 do compilador](../../error-messages/compiler-warnings/compiler-warning-c4484.md)|'*override_function*': correspondências de método ref class base '*base_class_function*', mas não está marcado como 'virtual', 'new' ou 'override'; 'new' (e não 'virtual') é assumido|
|[Aviso (erro) C4485 do compilador](../../error-messages/compiler-warnings/compiler-warning-c4485.md)|'*override_function*': correspondências de método ref class base '*base_class_function*', mas não está marcado como 'new' ou 'override'; 'new' (e 'virtual') são assumidos|
|[Aviso do compilador (nível 1) C4486](../../error-messages/compiler-warnings/compiler-warning-level-1-c4486.md)|'*função*': um método private virtual de uma classe ref ou classe de valor deve ser marcado como 'sealed'|
|[Aviso do compilador (nível 4) C4487](../../error-messages/compiler-warnings/compiler-warning-level-4-c4487.md)|'*derived_class_function*': correspondências herdadas de método não virtual '*base_class_function*', mas não está explicitamente marcado como 'new'|
|[Aviso do compilador (nível 1) C4488](../../error-messages/compiler-warnings/compiler-warning-level-1-c4488.md)|'*função*': requer '*palavra-chave*'palavra-chave para implementar o método de interface'*interface_method*'|
|[Aviso do compilador (nível 1) C4489](../../error-messages/compiler-warnings/compiler-warning-level-1-c4489.md)|'*especificador*': não é permitido em método de interface '*método*'; especificadores são permitidos apenas em métodos da classe ref classe e o valor de substituição|
|[Aviso do compilador (nível 1) C4490](../../error-messages/compiler-warnings/compiler-warning-level-1-c4490.md)|'override': uso incorreto de especificador de substituição; '*função*' não coincide com um método de classe ref base|
|Aviso do compilador (nível 1) C4491|'*nome*': tem um formato de versão IDL inválido|
|Aviso do compilador (nível 1, erro) C4492|'*função1*': correspondências de método ref class base '*função2*', mas não está marcado como 'override'|
|Aviso do compilador (nível 3, erro) c4493 informando|expressão de exclusão não surte efeito porque o destruidor de '*tipo*' não tem acessibilidade 'pública'|
|Aviso do compilador (nível 1) C4494|'*função*': Ignorando __declspec(allocator) porque o tipo de retorno de função não é um ponteiro ou referência|
|C4495 de aviso do compilador|extensão não padrão super' utilizada: substitua pelo nome de classe base explícito|
|C4496 de aviso do compilador|extensão não padrão 'for each' usada: Substituir por instrução intervalo-para|
|C4497 de aviso do compilador|extensão não padrão 'selada' usada: Substituir por 'final'|
|C4498 de aviso do compilador|extensão não padrão usada: '*extensão*'|
|Aviso do compilador (nível 4) C4499|"*função*': uma especialização explícita não pode ter uma classe de armazenamento (ignorada)"|
|[Aviso do compilador (nível 1) C4502](../../error-messages/compiler-warnings/compiler-warning-level-1-c4502.md)|'*especificação de vinculação*' requer o uso da palavra-chave 'extern' e deve preceder todos os outros especificadores|
|[Aviso do compilador (nível 1) C4503](../../error-messages/compiler-warnings/compiler-warning-level-1-c4503.md)|'*identificador*': decorado excedido, comprimento do nome nome foi truncado|
|[Aviso do compilador (nível 4) C4505](../../error-messages/compiler-warnings/compiler-warning-level-4-c4505.md)|'*função*': função local não referenciada foi removida|
|[Aviso do compilador (nível 1) C4506](../../error-messages/compiler-warnings/compiler-warning-level-1-c4506.md)|Nenhuma definição de função embutida '*função*'|
|[Aviso do compilador (nível 1) C4508](../../error-messages/compiler-warnings/compiler-warning-level-1-c4508.md)|'*função*': função deve retornar um valor; supõe-se de tipo de retorno 'void'|
|C4509 de aviso do compilador|extensão não padrão usada: '*função*' usa SEH e '*objeto*' possui destruidor|
|[Aviso do compilador (nível 4) C4510](../../error-messages/compiler-warnings/compiler-warning-level-4-c4510.md)|'*classe*': construtor padrão foi implicitamente definido como excluído|
|[Aviso do compilador (nível 3) C4511](../../error-messages/compiler-warnings/compiler-warning-level-3-c4511.md)|'*classe*': construtor de cópia foi implicitamente definido como excluído|
|[Aviso do compilador (nível 4) C4512](../../error-messages/compiler-warnings/compiler-warning-level-4-c4512.md)|'*classe*': operador de atribuição foi implicitamente definido como excluído|
|[Aviso do compilador (nível 4) C4513](../../error-messages/compiler-warnings/compiler-warning-level-4-c4513.md)|'*classe*': destrutor foi implicitamente definido como excluído|
|[Aviso do compilador (nível 4) C4514](../../error-messages/compiler-warnings/compiler-warning-level-4-c4514.md)|'*função*': função inline não referenciada foi removida|
|[Aviso do compilador (nível 4) C4515](../../error-messages/compiler-warnings/compiler-warning-level-4-c4515.md)|'*namespace*': namespace usa a mesmo|
|[Aviso do compilador (nível 4) C4516](../../error-messages/compiler-warnings/compiler-warning-level-4-c4516.md)|'class::symbol': declarações de acesso são preteridas; declarações de using membro fornecem uma alternativa melhor|
|[Aviso do compilador (nível 4) C4517](../../error-messages/compiler-warnings/compiler-warning-level-4-c4517.md)|declarações de acesso são preteridas; declarações de using membro fornecem uma alternativa melhor|
|[Aviso do compilador (nível 1) C4518](../../error-messages/compiler-warnings/compiler-warning-level-1-c4518.md)|'*especificador*': classe de armazenamento ou um tipo specifier(s) inesperado aqui; ignorado|
|Aviso (erro) C4519 do compilador|argumentos de modelo padrão são permitidos apenas em um modelo de classe|
|[Aviso do compilador (nível 3) C4521](../../error-messages/compiler-warnings/compiler-warning-level-3-c4521.md)|'*classe*': vários construtores de cópia especificados|
|[Aviso do compilador (nível 3) C4522](../../error-messages/compiler-warnings/compiler-warning-level-3-c4522.md)|'*classe*': vários operadores de atribuição especificadas|
|[Aviso do compilador (nível 3) C4523](../../error-messages/compiler-warnings/compiler-warning-level-3-c4523.md)|'*classe*': vários destruidores especificados|
|[Aviso do compilador (nível 1) C4526](../../error-messages/compiler-warnings/compiler-warning-level-1-c4526.md)|'*função*': função de membro estático não pode substituir função virtual '*função virtual*' substituição ignorada, função virtual será ocultada|
|[Aviso do compilador (nível 1) C4530](../../error-messages/compiler-warnings/compiler-warning-level-1-c4530.md)|Manipulador de exceção de C++ usado, mas semântica de liberação não estão habilitados. Especifique /EHsc|
|Aviso do compilador (nível 1) C4531|Tratamento de exceções de C++ não disponível no Windows CE. Use o tratamento de exceções estruturado|
|[Aviso do compilador (nível 1) C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|'continue': salto para fora do bloco Finally/finally' possui comportamento indefinido durante manipulação de encerramento|
|[Aviso do compilador (nível 1) C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|inicialização de '*variável*'é ignorada por'*goto rótulo*'|
|[Aviso do compilador (nível 3) C4534](../../error-messages/compiler-warnings/compiler-warning-level-3-c4534.md)|'*construtor*'não será um construtor padrão para 'classe/struct' '*identificador*' devido ao argumento padrão|
|[Aviso do compilador (nível 3) C4535](../../error-messages/compiler-warnings/compiler-warning-level-3-c4535.md)|chamada set_se_translator () requer /EHa|
|[Aviso do compilador (nível 4) C4536](../../error-messages/compiler-warnings/compiler-warning-level-4-c4536.md)|'*typename*': nome do tipo excede o limite de metadados de '*character_limit*' caracteres|
|[Aviso do compilador (nível 1) C4537](../../error-messages/compiler-warnings/compiler-warning-level-1-c4537.md)|'*objeto*': '.' aplicado a tipo não UDT|
|[Aviso do compilador (nível 3) C4538](../../error-messages/compiler-warnings/compiler-warning-level-3-c4538.md)|'*tipo*': não há suporte para qualificadores const/volatile neste tipo|
|[Aviso do compilador (nível 1) C4540](../../error-messages/compiler-warnings/compiler-warning-level-1-c4540.md)|dynamic_cast usado para converter para base inacessível ou ambígua; teste de tempo de execução falhará ('*type1*'para'*type2*')|
|[Aviso do compilador (nível 1) C4541](../../error-messages/compiler-warnings/compiler-warning-level-1-c4541.md)|'*identificador*'usado em tipo polimórfico'*tipo*' com /GR-; poderá ocorrer comportamento imprevisível|
|Aviso do compilador (nível 1) C4542|Ignorando a geração do arquivo de texto injetado mesclado, não é possível gravar *filetype* arquivo: '*problema*': *mensagem*|
|[Aviso do compilador (nível 3) C4543](../../error-messages/compiler-warnings/compiler-warning-level-3-c4543.md)|Injetado suprimido por atributo de texto ' sem\_injected_text'|
|[Aviso do compilador (nível 1) C4544](../../error-messages/compiler-warnings/compiler-warning-level-1-c4544.md)|'*declaração*': argumento de modelo ignorado nessa declaração de template padrão|
|[Aviso do compilador (nível 1) C4545](../../error-messages/compiler-warnings/compiler-warning-level-1-c4545.md)|expressão antes da vírgula é avaliada para uma função que está ausente em uma lista de argumentos|
|[Aviso do compilador (nível 1) C4546](../../error-messages/compiler-warnings/compiler-warning-level-1-c4546.md)|faltando lista de argumentos na chamada de função antes da vírgula|
|[Aviso do compilador (nível 1) C4547](../../error-messages/compiler-warnings/compiler-warning-level-1-c4547.md)|'*operador*': operador antes da vírgula não tem nenhum efeito; esperado operador com efeito colateral|
|[Aviso do compilador (nível 1) C4548](../../error-messages/compiler-warnings/compiler-warning-level-1-c4548.md)|expressão antes da vírgula não tem efeito; expressão esperada com efeito colateral|
|[Aviso do compilador (nível 1) C4549](../../error-messages/compiler-warnings/compiler-warning-level-1-c4549.md)|'*operador*': operador antes da vírgula não tem nenhum efeito; você pretendia '*operador*'?|
|[Aviso do compilador (nível 1) C4550](../../error-messages/compiler-warnings/compiler-warning-level-1-c4550.md)|expressão é avaliada como uma função que está faltando uma lista de argumentos|
|[Aviso do compilador (nível 1) C4551](../../error-messages/compiler-warnings/compiler-warning-level-1-c4551.md)|lista de argumentos ausente de chamada de função|
|[Aviso do compilador (nível 1) C4552](../../error-messages/compiler-warnings/compiler-warning-level-1-c4552.md)|'*operador*': operador não tem nenhum efeito; esperado operador com efeito colateral|
|[Aviso do compilador (nível 1) C4553](../../error-messages/compiler-warnings/compiler-warning-level-1-c4553.md)|'*operador*': operador não tem nenhum efeito; você pretendia ' operador?|
|[Aviso do compilador (nível 3) C4554](../../error-messages/compiler-warnings/compiler-warning-level-3-c4554.md) C4554|'*operador*': Verifique a precedência do operador para possível erro; use parênteses para esclarecer a precedência|
|[Aviso do compilador (nível 1) C4555](../../error-messages/compiler-warnings/compiler-warning-level-1-c4555.md)|expressão não tem efeito; expressão esperada com efeito colateral|
|[Aviso do compilador (nível 1) C4556](../../error-messages/compiler-warnings/compiler-warning-level-1-c4556.md)|valor do argumento imediato intrínseco '*valor*'está fora do intervalo'*lower_bound* - *upper_bound*'|
|[Aviso do compilador (nível 3) C4557](../../error-messages/compiler-warnings/compiler-warning-level-3-c4557.md)|assume' contém efeito '*efeito*'|
|[Aviso do compilador (nível 1) C4558](../../error-messages/compiler-warnings/compiler-warning-level-1-c4558.md)|valor do operando '*valor*'está fora do intervalo'*lower_bound* - *upper_bound*'|
|[Aviso do compilador (nível 4) C4559](../../error-messages/compiler-warnings/compiler-warning-level-4-c4559.md)|'*função*': redefinição; a função ganhos __declspec(modifier)|
|[Aviso do compilador (nível 1) C4561](../../error-messages/compiler-warnings/compiler-warning-level-1-c4561.md)|fastcall' incompatível com o ' / clr' opção: convertendo para stdcall'|
|Aviso do compilador (nível 4) C4562|funções totalmente prototipadas são necessárias com o ' / clr' opção: convertendo '()' para '(void)'|
|[Aviso do compilador (nível 4) C4564](../../error-messages/compiler-warnings/compiler-warning-level-4-c4564.md)|método '*método*'de 'class' '*classname*'define parâmetro padrão sem suporte'*parâmetro*'|
|[Aviso do compilador (nível 4) C4565](../../error-messages/compiler-warnings/compiler-warning-level-4-c4565.md)|'*função*': redefinição; símbolo foi declarado anteriormente com __declspec(modifier)|
|[Aviso do compilador (nível 1) C4566](../../error-messages/compiler-warnings/compiler-warning-level-1-c4566.md)|caractere representado por nome de caractere universal '*char*' não pode ser representado na página de código atual (*número*)|
|Aviso do compilador (nível 1) C4568|'*função*': nenhum membro corresponde à assinatura da substituição explícita|
|Aviso do compilador (nível 3) C4569|'*função*': nenhum membro corresponde à assinatura da substituição explícita|
|[Aviso do compilador (nível 3) C4570](../../error-messages/compiler-warnings/compiler-warning-level-3-c4570.md)|'*tipo*': não é declarado explicitamente como abstract, mas possui funções abstract|
|[Aviso do compilador (nível 4) C4571](../../error-messages/compiler-warnings/compiler-warning-level-4-c4571.md)|Informativo: semântica catch alterada desde o Visual C++ 7.1; exceções estruturadas (SEH) não são mais capturadas|
|[Aviso do compilador (nível 1) C4572](../../error-messages/compiler-warnings/compiler-warning-level-1-c4572.md)|Atributo [ParamArray] é preterido sob /clr, use '...' em vez disso|
|Aviso do compilador (nível 1) C4573|o uso de '*função lambda*' requer que o compilador capture 'this' mas o modo de captura padrão atual não permite|
|Aviso do compilador (nível 4) C4574|'*Identificador*'é definido como ' 0': você pretendia usar '#if identifier'?|
|Aviso do compilador (nível 1) C4575|vectorcall' incompatível com o ' / clr' opção: convertendo para stdcall'|
|Aviso do compilador (nível 1, erro) C4576|um tipo de entre parênteses seguido por uma lista de inicializadores é uma sintaxe de conversão de tipo explícito não padrão|
|Aviso do compilador (nível 1, Off) C4577|'noexcept' usado com nenhum modo especificado; de manipulação de exceção Não há garantia a terminação na exceção. Especifique /EHsc|
|Aviso do compilador (nível 1, erro) C4578|'abs': conversão de '*type1*'para'*type2*', possível perda de dados (você pretendia chamar '*função*' ou #include \<cmath >?)|
|[Aviso do compilador (nível 3) C4580](../../error-messages/compiler-warnings/compiler-warning-level-3-c4580.md)|[attribute] é preterido; em vez disso, especifique System::Attribute ou Platform:: Metadata como uma classe base|
|[Aviso do compilador (nível 1) C4581](../../error-messages/compiler-warnings/compiler-warning-level-1-c4581.md)|comportamento preterido: ' "*cadeia de caracteres*"' substituído por '*cadeia de caracteres*' para processar atributo|
|Aviso do compilador (nível 4) C4582|'*tipo*': construtor não está chamado implicitamente|
|Aviso do compilador (nível 4) C4583|'*tipo*': destruidor não é chamado implicitamente|
|[Aviso do compilador (nível 1) C4584](../../error-messages/compiler-warnings/compiler-warning-level-1-c4584.md)|'*class1*': classe base*class2*'já é uma classe base de'*class3*'|
|Aviso do compilador (nível 1, erro) C4585|'*classe*': Uma WinRT '' classe ref pública deve ser selada ou deriva de uma classe não lacrada existente|
|Aviso do compilador (nível 1, erro) C4586|'*type*': Um tipo público não pode ser declarado em um namespace de nível superior chamado 'Windows'|
|Aviso do compilador (nível 1) C4587|'*anonymous_structure*': alteração de comportamento: construtor é não é mais implicitamente chamado|
|Aviso do compilador (nível 1) C4588|'*anonymous_structure*': alteração de comportamento: destruidor é não é mais implicitamente chamado|
|Aviso do compilador (nível 1) C4591|limite de profundidade da chamada de 'constexpr' *número* excedido (/ /constexpr: Depth\<número >)|
|Aviso do compilador (nível 3) C4592|'*função*': Falha na avaliação da chamada 'constexpr'; função será chamada em tempo de execução|
|Aviso do compilador (nível 1) C4593|'*função*': limite de etapa de avaliação de chamadas de 'constexpr' de '*limite*' excedido; use /constexpr: Steps\<número > para aumentar o limite|
|Aviso do compilador (nível 3) C4594|'*tipo*': destruidor não será implicitamente chamado se uma exceção é lançada|
|Aviso do compilador (nível 1) C4595|'*tipo*': alteração de comportamento: destruidor será não é mais implicitamente chamado se uma exceção é lançada|
|Aviso do compilador (nível 4) C4596|'*identificador*': nome qualificado inválido na declaração de membro|
|Aviso do compilador (erro) C4597|um comportamento indefinido: offsetof aplicado a um membro de uma base virtual|
|Aviso do compilador (nível 1 e nível 3) C4598|' #include "*cabeçalho*"': o número de cabeçalho *número* no cabeçalho pré-compilado não coincide com a compilação atual naquela posição|
|Aviso do compilador (nível 3) C4599|'*sinalizador* *caminho*': número de argumento de linha de comando *número* não corresponde ao cabeçalho pré-compilado|

## <a name="see-also"></a>Consulte também

[C /C++ ferramentas de compilador e build erros e avisos](../compiler-errors-1/c-cpp-build-errors.md) \
[Avisos do compilador C4000 - C5999](compiler-warnings-c4000-c5999.md)
