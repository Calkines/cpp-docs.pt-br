---
title: Erros de compilador C2800 a C2899
ms.date: 11/17/2017
f1_keywords:
- C2816
- C2820
- C2822
- C2826
- C2832
- C2836
- C2837
- C2840
- C2841
- C2848
- C2851
- C2852
- C2853
- C2866
- C2880
- C2887
- C2889
- C2895
- C2899
helpviewer_keywords:
- C2816
- C2820
- C2822
- C2826
- C2832
- C2836
- C2837
- C2840
- C2841
- C2848
- C2851
- C2852
- C2853
- C2866
- C2880
- C2887
- C2889
- C2895
- C2899
ms.assetid: e5de1e92-746a-4315-a331-c5d9efb76dbb
ms.openlocfilehash: 1c1b001e4d55c913cd2b9a50ee2e4bb4d2915523
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601097"
---
# <a name="compiler-errors-c2800-through-c2899"></a>Erros de compilador C2800 a C2899

Os artigos nesta seção da documentação explicam um subconjunto das mensagens de erro que são gerados pelo compilador.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="error-messages"></a>Mensagens de erro

|Erro|Mensagem|
|-----------|-------------|
|[Erro do compilador C2800](compiler-error-c2800.md)|' operador *operador*' não pode ser sobrecarregado|
|[Erro do compilador C2801](compiler-error-c2801.md)|'*membro*' deve ser um membro não estático|
|[Erro do compilador C2802](compiler-error-c2802.md)|membro estático ' operador *operador*' não possui parâmetros formais|
|[Erro do compilador C2803](compiler-error-c2803.md)|' operador *operador*' deve ter pelo menos um parâmetro formal do tipo de classe|
|[Erro do compilador C2804](compiler-error-c2804.md)|binário ' operador *operador*' possui muitos parâmetros|
|[Erro do compilador C2805](compiler-error-c2805.md)|binário ' operador *operador*' possui poucos parâmetros|
|[Erro do compilador C2806](compiler-error-c2806.md)|' operador *operador*' possui muitos parâmetros formais|
|[Erro do compilador C2807](compiler-error-c2807.md)|o segundo parâmetro formal de sufixo ' operador *operador*' deve ser 'int'|
|[Erro do compilador C2808](compiler-error-c2808.md)|unário ' operador *operador*' possui muitos parâmetros formais|
|[Erro do compilador C2809](compiler-error-c2809.md)|' operador *operador*' não possui parâmetros formais|
|[Erro do compilador C2810](compiler-error-c2810.md)|'*interface*': uma interface só pode herdar de outra interface|
|[Erro do compilador C2811](compiler-error-c2811.md)|'*type1*': não pode herdar de '*type2*', uma classe ref só pode herdar de uma classe ref ou classe de interface|
|[Erro do compilador C2812](compiler-error-c2812.md)|#import não é suportado com /clr: pure e /CLR: safe|
|[Erro do compilador C2813](compiler-error-c2813.md)|#import não é suportado com /MP|
|[Erro do compilador C2814](compiler-error-c2814.md)|'*membro*': um tipo nativo não pode ser aninhado dentro de um tipo gerenciado/WinRT '*classe*'|
|[Erro do compilador C2815](compiler-error-c2815.md)|'operator delete': primeiro parâmetro formal deve ser ' void *', mas '* tipo *' foi usado|
|C2816 de erro do compilador|Obsoleto.|
|[Erro do compilador C2817](compiler-error-c2817.md)|tipo de retorno para 'operator delete' deve ser 'void'|
|[Erro do compilador C2818](compiler-error-c2818.md)|'aplicativo de operador ->' sobrecarregado é recursiva através do tipo '*classe*'|
|[Erro do compilador C2819](compiler-error-c2819.md)|tipo '*classe*' não tem um membro sobrecarregado 'operator' ->|
|C2820 de erro do compilador|Obsoleto.|
|[Erro do compilador C2821](compiler-error-c2821.md)|o primeiro parâmetro formal para 'operator new' deve ser 'size_t'|
|C2822 de erro do compilador|desenrolamento local não tem suporte nesta plataforma|
|[Erro do compilador C2823](compiler-error-c2823.md)|um typedef modelo/genérico é ilegal|
|[Erro do compilador C2824](compiler-error-c2824.md)|tipo de retorno para 'operator new' deve ser ' void *'|
|[Erro do compilador C2825](compiler-error-c2825.md)|'*identificador*': deve ser uma classe ou namespace quando seguido por ':: '|
|C2826 de erro do compilador|Obsoleto.|
|[Erro do compilador C2827](compiler-error-c2827.md)|' operador *operador*' não pode ser substituído globalmente com forma unária|
|[Erro do compilador C2828](compiler-error-c2828.md)|' operador *operador*' não pode ser substituído globalmente com forma binária|
|[Erro do compilador C2829](compiler-error-c2829.md)|' operador *operador*' não pode ter uma lista de parâmetros variáveis|
|[Erro do compilador C2830](compiler-error-c2830.md)|somente os parâmetros de posicionamento para 'operator new' podem ter valores padrão|
|[Erro do compilador C2831](compiler-error-c2831.md)|' operador *operador*' não pode ter parâmetros padrão|
|C2832 de erro do compilador|'*identificador*': um tipo de referência não pode ser inicializado por valor|
|[Erro do compilador C2833](compiler-error-c2833.md)|' operador *token*' não é um operador ou tipo reconhecido|
|[Erro do compilador C2834](compiler-error-c2834.md)|' operador *operador*' deve ser qualificado globalmente|
|[Erro do compilador C2835](compiler-error-c2835.md)|conversão definida pelo usuário '*tipo*' não recebe parâmetros formais|
|C2836 de erro do compilador|'*identificador*': membro de dados de apenas um não-estático de uma união pode ter um inicializador de membro padrão|
|C2837 de erro do compilador|'*função*': não é possível usar diretivas OpenMP e loop (hint_parallel) #pragma na mesma função|
|[Erro do compilador C2838](compiler-error-c2838.md)|'*identificador*': nome qualificado inválido na declaração de membro|
|[Erro do compilador C2839](compiler-error-c2839.md)|tipo de retorno inválido '*tipo*' para sobrecarregado 'operator ->'|
|C2840 de erro do compilador|argumento de palavra de instrução não constante|
|C2841 de erro do compilador|Registre-se o argumento não constante|
|[Erro do compilador C2842](compiler-error-c2842.md)|'*classe*': um tipo gerenciado/WinRT não pode definir seu próprio 'operator new' ou 'operator delete'|
|[Erro do compilador C2843](compiler-error-c2843.md)|'*membro*': não é possível obter o endereço de um membro de dados não estáticos ou método de um tipo gerenciado/WinRT|
|[Erro do compilador C2844](compiler-error-c2844.md)|'*identificador*': não pode ser um membro de interface '*interface*'|
|[Erro do compilador C2845](compiler-error-c2845.md)|'*tipo*': não é permitida neste tipo de aritmética de ponteiro|
|[Erro do compilador C2846](compiler-error-c2846.md)|'*interface*': uma interface não pode ter um construtor|
|[Erro do compilador C2847](compiler-error-c2847.md)|não é possível aplicar sizeof a tipo de WinRT gerenciados / '*classe*'|
|C2848 de erro do compilador|'*classe*': um tipo gerenciado/WinRT não pode ser um membro de uma união|
|[Erro do compilador C2849](compiler-error-c2849.md)|'*interface*': uma interface não pode ter um destruidor|
|[Erro do compilador C2850](compiler-error-c2850.md)|'*construir*': permitido apenas em escopo de arquivo; não pode estar em uma construção aninhada|
|C2851 de erro do compilador|'*enum*': uma enumeração WinRT pública somente pode usar 'int' ou 'unsigned int' como um tipo base|
|C2852 de erro do compilador|'*identificador*': somente os membros de dados podem ser inicializados dentro de uma classe|
|C2853 de erro do compilador|'*identificador*': um membro de dados não estático não pode ter um tipo que contenha 'auto'|
|[Erro do compilador C2854](compiler-error-c2854.md)|Erro de sintaxe em #pragma hdrstop|
|[Erro do compilador C2855](compiler-error-c2855.md)|opção de linha de comando '*opção*' inconsistente com cabeçalho pré-compilado|
|[Erro do compilador C2856](compiler-error-c2856.md)|#pragma hdrstop não pode ser dentro de um bloco #if|
|[Erro do compilador C2857](compiler-error-c2857.md)|' #include ' instrução especificada com o /Yc*filename* opção de linha de comando não foi encontrada no arquivo de origem|
|[Erro do compilador C2858](compiler-error-c2858.md)|opção de linha de comando ' /Yc (/Fd*filename*)' inconsistente com cabeçalho pré-compilado, que é usado ' /Fd*filename*'|
|[Erro do compilador C2859](compiler-error-c2859.md)|*nome do arquivo* não é o *filetype* arquivo que foi usado quando esse cabeçalho pré-compilado foi criado, recrie o cabeçalho pré-compilado.|
|[Erro do compilador C2860](compiler-error-c2860.md)|'void' não pode ser um tipo de argumento, exceto para '(void)'|
|[Erro do compilador C2861](compiler-error-c2861.md)|'*declaração*': uma função de membro de interface não pode ser definida.|
|[Erro do compilador C2862](compiler-error-c2862.md)|'*interface*': uma interface só pode possuir membros públicos|
|[Erro do compilador C2863](compiler-error-c2863.md)|'*interface*': uma interface não pode possuir friends|
|[Erro do compilador C2864](compiler-error-c2864.md)|'*identificador*': uma variável de membro/modelo de dados estático com um inicializador em classe deve ter tipo integral const não volátil|
|[Erro do compilador C2865](compiler-error-c2865.md)|'*operador*': comparação inválida para o identificador/ponteiro de objeto|
|C2866 de erro do compilador|Obsoleto.|
|[Erro do compilador C2867](compiler-error-c2867.md)|'*identificador*': não é um namespace|
|[Erro do compilador C2868](compiler-error-c2868.md)|'*identificador*': sintaxe inválida para declaração de using; esperado nome qualificado|
|[Erro do compilador C2869](compiler-error-c2869.md)|'*identificador*': já foi definido para ser um namespace|
|[Erro do compilador C2870](compiler-error-c2870.md)|'*identificador*': uma definição de namespace deve aparecer no escopo do arquivo ou imediatamente dentro de outra definição de namespace|
|[Erro do compilador C2871](compiler-error-c2871.md)|'*identificador*': um namespace com esse nome não existe|
|[Erro do compilador C2872](compiler-error-c2872.md)|'*identificador*': símbolo ambíguo|
|[Erro do compilador C2873](compiler-error-c2873.md)|'*símbolo*': símbolo não pode ser usado em uma declaração using|
|[Erro do compilador C2874](compiler-error-c2874.md)|declaração de Using causa uma declaração múltipla de '*identificador*'|
|[Erro do compilador C2875](compiler-error-c2875.md)|declaração de Using causa uma declaração múltipla de '*classe*::*identificador*'|
|[Erro do compilador C2876](compiler-error-c2876.md)|'*classe*::*membro*': nem todas as sobrecargas são acessíveis|
|[Erro do compilador C2877](compiler-error-c2877.md)|'*membro*'não é acessível de'*classe*'|
|[Erro do compilador C2878](compiler-error-c2878.md)|'*identificador*': um namespace ou classe este nome não existe|
|[Erro do compilador C2879](compiler-error-c2879.md)|'*identificador*': apenas um namespace existente pode ser dado um nome alternativo por uma definição de alias de namespace|
|C2880 de erro do compilador|SWI ou HVC requer uma constante válida como primeiro argumento (SWI number)|
|[Erro do compilador C2881](compiler-error-c2881.md)|'*identificador*': já é usado como um alias para '*classe*'|
|[Erro do compilador C2882](compiler-error-c2882.md)|'*identificador*': uso inválido de identificador de namespace na expressão|
|[Erro do compilador C2883](compiler-error-c2883.md)|'*função*': declaração de função está em conflito com '*identificador*' introduzido por declaração using|
|[Erro do compilador C2884](compiler-error-c2884.md)|'*identificador*': introduzido por declaração using está em conflito com função local '*função*'|
|[Erro do compilador C2885](compiler-error-c2885.md)|'*classe*::*identificador*': não uma declaração de using válida em escopo diferente de classe|
|[Erro do compilador C2886](compiler-error-c2886.md)|'*classe*::*identificador*': símbolo não pode ser usado em uma declaração de using membro|
|C2887 de erro do compilador|SWI ou HVC não pode ter mais de cinco argumentos (SWI number, r0 - r3)|
|[Erro do compilador C2888](compiler-error-c2888.md)|'*identificador*': símbolo não pode ser definido dentro do namespace '*namespace*'|
|C2889 de erro do compilador|'*classe*': um tipo de classe WinRT gerenciados/não pode ser uma classe base virtual|
|[Erro do compilador C2890](compiler-error-c2890.md)|'*classe*': uma classe ref só pode ter uma classe de base não interface|
|[Erro do compilador C2891](compiler-error-c2891.md)|'*parâmetro*': não é possível obter o endereço de um parâmetro de modelo|
|[Erro do compilador C2892](compiler-error-c2892.md)|classe local não deve ter modelos de membro|
|[Erro do compilador C2893](compiler-error-c2893.md)|Falha ao especializar template de função '*modelo*'|
|[Erro do compilador C2894](compiler-error-c2894.md)|modelos não podem ser declarados para ter ' c'|
|C2895 de erro do compilador|'*declaração*': não é possível instanciar explicitamente um modelo de função que foi declarado com dllimport|
|[Erro do compilador C2896](compiler-error-c2896.md)|'*função1*': não é possível usar o modelo de função/genérico '*função2*' como um argumento de função|
|[Erro do compilador C2897](compiler-error-c2897.md)|um destruidor/finalizador não pode ser um modelo de função|
|[Erro do compilador C2898](compiler-error-c2898.md)|'*declaração*': modelos de função de membro não podem ser virtuais|
|C2899 de erro do compilador|Obsoleto.|
