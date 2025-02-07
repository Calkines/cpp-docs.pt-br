---
title: Expressões regulares (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- regular expressions [C++]
ms.assetid: aafe202a-1d96-4b36-a270-d676dfd3c51c
ms.openlocfilehash: db5a7eacc136b3f30187692c7ea10792b84eb3fc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451383"
---
# <a name="regular-expressions-c"></a>Expressões regulares (C++)

A C++ biblioteca padrão dá suporte a várias gramáticas de expressão regular. Este tópico discute as variações de gramática disponíveis ao usar expressões regulares.

## <a name="regexgrammar"></a> Gramática da expressão regular

A gramática de expressão regular a ser usada é especificada pelo uso de um dos `std::regex_constants::syntax_option_type` valores de enumeração. Essas gramáticas de expressão regular são definidas em std:: regex_constants:

- `ECMAScript`: Isso é mais próximo da gramática usada pelo JavaScript e pelas linguagens .NET.
- `basic`: As expressões regulares básicas do POSIX ou BRE.
- `extended`: As expressões regulares estendidas do POSIX ou pode.
- `awk`: Isso é `extended`, mas tem escapes adicionais para caracteres não imprimíveis.
- `grep`: Isso é `basic`, mas também permite caracteres de nova linha (' \n ') para separar as alternações.
- `egrep`: Isso é `extended`, mas também permite caracteres de nova linha para separar as alternações.

Por padrão, se nenhuma gramática for especificada, `ECMAScript` será assumida. Somente uma gramática pode ser especificada.

Além da gramática, vários sinalizadores podem ser aplicados:
- `icase`: Ignorar maiúsculas e minúsculas ao corresponder.
- `nosubs`: Ignorar correspondências marcadas (ou seja, expressões entre parênteses); nenhuma substituição é armazenada.
- `optimize`: Torne a correspondência mais rápida, às possíveis despesas de tempo de construção maior.
- `collate`: Use sequências de agrupamentos sensíveis à localidade (por exemplo, intervalos do formulário "[a-z]").

Zero ou mais sinalizadores podem ser combinados com a gramática para especificar o comportamento do mecanismo de expressões regulares. Se apenas sinalizadores forem especificados, `ECMAScript` será assumido como a gramática.

### <a name="element"></a>Elemento

Um elemento pode ser um dos seguintes itens:

- Um *caractere comum* que corresponde ao mesmo caractere na sequência de destino.

- Um *caractere curinga* '.' que corresponde a qualquer caractere na sequência de destino, exceto a uma nova linha.

- Uma *expressão entre colchetes* da forma "[`expr`]", que corresponde a um caractere ou a um elemento de ordenação na sequência de destino que também está no conjunto definido pela expressão `expr` ou da forma "[^`expr`]", que corresponde a um caractere ou a um elemento de ordenação na sequência de destino que não está no conjunto definido pela expressão `expr`.

   A expressão `expr` pode conter qualquer combinação dos seguintes itens:

   - Um caractere individual. Adiciona esse caractere ao conjunto definido por `expr`.

   - Um *intervalo de caracteres* no formato "`ch1`-`ch2`". Adiciona os caracteres que são representados pelos valores no intervalo fechado [`ch1`, `ch2`] ao conjunto definido por `expr`.

   - Uma *classe de caracteres* no formato "[:`name`:]". Adiciona os caracteres na classe nomeada ao conjunto definido por `expr`.

   - Uma *classe de equivalência* no formato "[=`elt`=]". Adiciona os elementos de agrupamento que são equivalentes a `elt` ao conjunto definido por `expr`.

   - Um *símbolo de agrupamento* no formato "[.`elt`.]". Adiciona o elemento de ordenação `elt` ao conjunto definido por `expr`.

- Uma *âncora*. A âncora '^' corresponde ao início da sequência de destino; a âncora '$' corresponde ao fim da sequência de destino.

Um *grupo de captura* no formato "( *subexpressão* )" ou "\\( *subexpressão* \\)" em `basic` e `grep`, que corresponde à sequência de caracteres na sequência de destino que é correspondida pelo padrão entre os delimitadores.

- Um *caractere de escape de identidade* no formato "\\`k`", que corresponde ao caractere `k` na sequência de destino.

Exemplos:

- "a" corresponde à sequência de destino "a", mas não corresponde às sequências de destino "B", "b" ou "c".

- "." corresponde a todas as sequências de destino "a", "B", "b" e "c".

- "[b-z]" corresponde às sequências de destino "b" e "c", mas não corresponde às sequências de destino "a" ou "B".

- "[:lower:]" corresponde às sequências de destino "a", "b" e "c", mas não corresponde à sequência de destino "B".

- "(a)" corresponde à sequência de destino "a" e associa o grupo de captura 1 à subsequência "a", mas não corresponde às sequências de destino "B", "b" ou "c".

Em `ECMAScript`, `basic` e `grep`, um elemento também pode ser uma *referência inversa* no formato "\\`dd`", em que `dd` representa um valor decimal N que corresponde a uma sequência de caracteres na sequência de destino que é igual à sequência de caracteres que é correspondida pelo enésimo *grupo de captura*. Por exemplo, "(a)\1" corresponde à sequência de destino "aa" porque o primeiro (e único) grupo de captura corresponde à sequência inicial "a" e \1 corresponde à sequência final "a".

Em `ECMAScript`, um elemento também pode ser um dos seguintes itens:

- Um *grupo de não captura* no formato "(?: subexpressão)". Corresponde à sequência de caracteres na sequência de destino que é correspondida pelo padrão entre os delimitadores.

- Um *escape de formatação de arquivo* no formato "\f", "\n", "\r", "\t" ou "\v". Isso corresponde a um avanço de página, uma nova linha, um retorno de carro, uma guia horizontal e uma guia vertical, respectivamente, na sequência de destino.

- Uma *asserção positiva* no formato "(= *subexpressão* )". Corresponde à sequência de caracteres na sequência de destino que é correspondida pelo padrão entre os delimitadores, mas não altera a posição de correspondência na sequência de destino.

- Uma *asserção negativa* no formato "(! *subexpression* )". Corresponde a qualquer sequência de caracteres na sequência de destino que não corresponde ao padrão entre os delimitadores e não altera a posição de correspondência na sequência de destino.

- Uma *sequência de escape hexadecimal* no formato "\x`hh`". Corresponde a um caractere na sequência de destino que é representado pelos dois dígitos hexadecimais `hh`.

- Uma *sequência de escape unicode* no formato "\u`hhhh`". Corresponde a um caractere na sequência de destino que é representado pelos quatro dígitos hexadecimais `hhhh`.

- Uma *sequência de escape de controle* no formato "\c`k`". Corresponde ao caractere de controle que é nomeado pelo caractere `k`.

- Uma *asserção do limite de palavra* no formato "\b". Corresponde quando a posição atual na sequência de destino está logo após um *limite de palavra*.

- Uma *asserção do limite de palavra negativa* no formato "\B". Corresponde quando a posição atual na sequência de destino não está logo após um *limite de palavra*.

- Um *escape de caractere dsw* no formato "\d", "\D", "\s", "\S", "\w", "\W". Fornece um nome curto para uma classe de caractere.

Exemplos:

- "(?:a)" corresponde à sequência de destino "a", mas "(?:a)\1" é inválido porque não há grupo de captura 1.

- "(=a)a" corresponde à sequência de destino "a". A declaração positiva corresponde à sequência inicial "a" na sequência de destino e "a" final na expressão regular corresponde à sequência inicial "a" na sequência de destino.

- "(!a)a" não corresponde à sequência de destino "a".

- "a\b." corresponde à sequência de destino "a~", mas não corresponde à sequência de destino "ab".

- "a\B." corresponde à sequência de destino "ab", mas não corresponde à sequência de destino "a~".

Em `awk`, um elemento também pode ser um dos seguintes itens:

- Um *escape de formatação de arquivo* no formato "\\\\", "\a", "\b", "\f", "\n", "\r", "\t" ou "\v". Isso corresponde a uma barra invertida, um alerta, um backspace, um avanço de página, uma nova linha, um retorno de carro, uma guia horizontal e uma guia vertical, respectivamente, na sequência de destino.

- Uma *sequência de escape octal* no formato "\\`ooo`". Corresponde a um caractere na sequência de destino cuja representação é o valor representado por um, dois ou três dígitos octais `ooo`.

### <a name="repetition"></a>Repetição

Qualquer elemento diferente de uma *asserção positiva*, uma *asserção negativa* ou uma *âncora* pode ser seguido por uma contagem de repetição. O tipo mais genérico da contagem de repetição usa o formato "{`min`,`max`}" ou "\\{`min`,`max`\\}" em `basic` e `grep`. Um elemento que é seguido por essa forma de contagem de repetição corresponde a pelo menos `min` ocorrências sucessivas e a não mais do que `max` ocorrências sucessivas de uma sequência que corresponde ao elemento. Por exemplo, "a{2,3}" corresponde à sequência de destino "AA" e à sequência de destino "AAA", mas não à sequência de destino "a" ou à sequência de destino "aaaa".

Uma contagem de repetição também pode usar uma das seguintes formas:

- "{`min`}" ou "\\{`min`\\}" em `basic` e `grep`. Equivalente a "{`min`,`min`}".

- "{`min`,}" ou "\\{`min`,\\}" em `basic` e `grep`. Equivalente a "{`min`,unbounded}".

- "\*". Equivalente a "{0,unbounded}".

Exemplos:

- "a{2}" corresponde à sequência de destino "AA", mas não à sequência de destino "a" ou à sequência de destino "AAA".

- "a{2,}" corresponde à sequência de destino "AA", a sequência de destino "AAA" e assim por diante, mas não corresponde à sequência de destino "a".

- "a\*" corresponde à sequência de destino "", a sequência de destino "a", a sequência de destino "AA" e assim por diante.

Para todas as gramáticas, exceto `basic` e `grep`, uma contagem de repetição também pode usar uma das seguintes formas:

- "?". Equivalente a "{0,1}".

- "+". Equivalente a "{1, unbounded}".

Exemplos:

- "a?" corresponde à sequência de destino "" e à sequência de destino "a", mas não à sequência de destino "AA".

- "a+" corresponde à sequência de destino "a", à sequência de destino "aa", e assim por diante, mas não à sequência de destino "".

No `ECMAScript`, todas as formas de contagem de repetição podem ser seguidas pelo caractere '? ', que designa uma *repetição não-ávido*.

### <a name="concatenation"></a>Concatenação

Os elementos de expressão regular, com ou sem *contagens de repetição*, podem ser concatenados para formar expressões regulares mais longas. A expressão resultante corresponde a uma sequência de destino que é uma concatenação das sequências que são correspondidas pelos elementos individuais. Por exemplo, "a{2,3}b" corresponde à sequência de destino "aab" e à sequência de destino "aaab", mas não corresponde à sequência de destino "AB" ou à sequência de destino "aaaab".

### <a name="alternation"></a>Alternação

Em todas as gramáticas de expressão regular, exceto `basic` e `grep`, uma expressão regular concatenada pode ser seguida pelo caractere '&#124;' e outra expressão regular concatenada. Qualquer número de expressões regulares concatenadas pode ser combinado dessa forma. A expressão resultante corresponde a qualquer sequência de destino que corresponda a uma ou mais das expressões regulares concatenadas.

Quando mais de uma expressão regular concatenada corresponde à sequência de destino, `ECMAScript` escolhe a primeira das expressões regulares concatenadas que corresponde à sequência como a correspondência (*primeira correspondência*); as outras gramáticas da expressão regular escolhem aquela que alcança a *correspondência mais longa*. Por exemplo, "ab&#124;cd" corresponde à sequência de destino "ab" e à sequência de destino "cd", mas não à sequência de destino "abd" ou à sequência de destino "acd".

Em `grep` e `egrep`, um caractere de nova linha ('\n') pode ser usado para separar alternações.

### <a name="subexpression"></a>Subexpressão

Em `basic` e `grep`, uma subexpressão é uma concatenação. Em outras gramáticas de expressão regular, uma subexpressão é uma alternância.

## <a name="grammarsummary"></a> Resumo de gramática

A tabela a seguir resume os recursos que estão disponíveis nas várias gramáticas de expressão regular:

|Elemento|Basic|estendido|ECMAScript|grep|egrep|awk|
|-------------|---------|---------|----------|----------|-----------|---------|
|alternância usando '&#124;'||+|+||+|+|
|alternância usando '\n'||||+|+||
|âncora|+|+|+|+|+|+|
|referência inversa|+||+|+|||
|expressão entre colchetes|+|+|+|+|+|+|
|grupo de captura usando "()"||+|+||+|+|
|grupo de captura usando "\\(\\)"|+|||+|||
|sequência de escape de controle|||+||||
|escape de caractere dsw|||+||||
|escape de formato de arquivo|||+|||+|
|sequência de escape hexadecimal|||+||||
|escape de identidade|+|+|+|+|+|+|
|declaração negativa|||+||||
|declaração de limite de palavra negativa|||+||||
|grupo de não captura|||+||||
|repetição não greedy|||+||||
|sequência de escape octal||||||+|
|caractere comum|+|+|+|+|+|+|
|declaração positiva|||+||||
|repetição usando "{}"||+|+||+|+|
|repetição usando "\\{\\}"|+|||+|||
|repetição usando '\*'|+|+|+|+|+|+|
|repetição usando '?' e '+'||+|+||+|+|
|sequência de escape unicode|||+||||
|caractere curinga|+|+|+|+|+|+|
|declaração de limite de palavra|||+||||

## <a name="semanticdetails"></a> Detalhes da semântica

### <a name="anchor"></a>Âncora

Uma âncora corresponde a uma posição na cadeia de caracteres de destino, e não a um caractere. Uma âncora '^' corresponde ao início da cadeia de caracteres de destino e uma âncora '$' corresponde ao fim da cadeia de caracteres de destino.

### <a name="back-reference"></a>Referência inversa

Uma referência inversa é uma barra invertida seguida por um valor N decimal. Ele corresponde ao conteúdo do enésimo *grupo de captura*. O valor de N não deve ser maior que o número de grupos de captura que precede a referência inversa. Em `basic` e `grep`, o valor de N é determinado pelo dígito decimal que segue a barra invertida. Em `ECMAScript`, o valor de N é determinado por todos os dígitos decimais que seguem imediatamente a barra invertida. Portanto, em `basic` e `grep`, o valor de N nunca é superior a 9, mesmo que a expressão regular tenha mais de nove grupos de captura. Em `ECMAScript`, o valor de N é unbounded.

Exemplos:

- "((a+)(b+))(c+)\3" corresponde à sequência de destino "aabbbcbbb". A referência inversa "\3" corresponde ao texto no terceiro grupo de captura, isto é, "(b+)". Ela não corresponde à sequência de destino "aabbbcbb".

- "(a)\2" não é válido.

- "(b(((((((((a))))))))))\10" tem diferentes significados em `basic` e em `ECMAScript`. Em `basic` a referência inversa é "\1". A referência inversa corresponde ao conteúdo do primeiro grupo de captura (isto é, aquele que começa com "(b" e termina com ")" e vem antes da referência inversa), e o final '0' corresponde ao caractere comum '0'. Em `ECMAScript`, a referência inversa é "\10". Corresponde ao décimo grupo de captura, isto é, o mais interno.

### <a name="bracket-expression"></a>Expressão entre colchetes

Uma expressão entre colchetes define um conjunto de caracteres e os *elementos de agrupamento*. Quando a expressão entre colchetes começar com o caractere '^', a correspondência será bem-sucedida se nenhum elemento no conjunto corresponder ao caractere atual na sequência de destino. Caso contrário, a correspondência será bem-sucedida se algum dos elementos no conjunto corresponder ao caractere atual na sequência de destino.

O conjunto de caracteres pode ser definido listando qualquer combinação de *caracteres individuais*, *intervalos de caracteres*, *classes de caracteres*, *classes de equivalência* e *símbolos de agrupamento*.

### <a name="capture-group"></a>Grupo de captura

O grupo de captura marca seu conteúdo como uma unidade única na gramática da expressão regular e rotula o texto de destino que corresponde ao seu conteúdo. O rótulo que é associado a cada grupo de captura é um número, que é determinado pela contagem dos parênteses de abertura que marcam grupos de captura até, e inclusive, os parênteses de abertura que marcam o grupo de captura atual. Nessa implementação, o número máximo de grupos de captura é 31.

Exemplos:

- "ab+" corresponde à sequência de destino "abb", mas não corresponde à sequência de destino "abab".

- "(ab)+" não corresponde à sequência de destino "abb", mas corresponde à sequência de destino "abab".

- "((a+)(b+))(c+)" corresponde à sequência de destino "aabbbc" e associa o grupo de captura 1 à subsequência "aabbb", o grupo de captura 2 à subsequência "aa", o grupo de captura 3 a "bbb" e o grupo de captura 4 à subsequência "c".

### <a name="character-class"></a>Classe de caractere

Uma classe de caractere em uma expressão entre colchetes adiciona todos os caracteres na classe nomeada ao conjunto de caracteres que é definido pela expressão entre colchetes. Para criar uma class de caractere, use "[:" seguido pelo nome da classe seguida por ":]". Internamente, nomes de classes de caractere são reconhecidos chamando `id = traits.lookup_classname`. Um caractere `ch` pertencerá a uma classe dessa se `traits.isctype(ch, id)` retornar true. O modelo `regex_traits` padrão oferece suporte a nomes de classe na tabela a seguir.

|Nome da classe|Descrição|
|----------------|-----------------|
|"alnum"|letras minúsculas, letras maiúsculas e dígitos|
|"alpha"|letras minúsculas e letras maiúsculas|
|"blank"|espaço ou tabulação|
|"cntrl"|os caracteres de *escape de formatação de arquivo*|
|"digit"|dígitos|
|"graph"|letras minúsculas, letras maiúsculas, dígitos e pontuação|
|"lower"|letras minúsculas|
|"print"|letras minúsculas, letras maiúsculas, dígitos, pontuação e espaço|
|"punct"|pontuação|
|"space"|espaço|
|"upper|caracteres maiúsculos|
|"xdigit"|dígitos, 'a', 'b', 'c', 'd', 'e', 'f', 'A', 'B', 'C', 'D', 'E', 'F'|
|"d"|mesmo que digit|
|"s"|mesmo que space|
|"w"|mesmo que alnum|

### <a name="character-range"></a>Intervalo de caracteres

Um intervalo de caracteres em uma expressão entre colchetes adiciona todos os caracteres no intervalo ao conjunto de caracteres que é definido pela expressão entre colchetes. Para criar um intervalo de caracteres, coloque o caractere '-' entre o primeiro e o último caracteres no intervalo. Fazer isso coloca no conjunto todos os caracteres que têm um valor numérico maior ou igual ao valor numérico do primeiro caractere e menor ou igual ao valor numérico do último caractere. Observe que esse conjunto de caracteres adicionados depende da representação de caracteres específica da plataforma. Se o caractere '-' ocorrer no início ou no fim de uma expressão entre colchetes, ou como o primeiro ou o último caractere de um intervalo de caracteres, ele representará a si mesmo.

Exemplos:

- "[0-7]" representa o conjunto de caracteres { '0', '1', '2', '3', '4', '5', '6', '7' }. Ele corresponde às sequências de destino "0", "1", e assim por diante, mas não a "a".

- Em sistemas que usam a codificação de caractere ASCII, "[h-k]" representa o conjunto de caracteres { 'h', 'i', 'j', 'k' }. Ele corresponde às sequências de destino "h", "i", e assim por diante, mas não a "\x8A" ou "0".

- Em sistemas que usam a codificação de caractere EBCDIC, "[h-k]" representa o conjunto de caracteres { 'h', 'i', '\x8A', '\x8B', '\x8C', '\x8D', '\x8E', '\x8F', '\x90', 'j', 'k' } ('h' é codificado como 0x88 e 'k' é codificado como 0x92). Corresponde às sequências de destino "h", "i", "\x8A", e assim por diante, mas não a "0".

- "[-0-24]" representa o conjunto de caracteres { '-', '0', '1', '2', '4' }.

- "[0-2-]" representa o conjunto de caracteres { '0', '1', '2', '-' }.

- Em sistemas que usam a codificação de caractere ASCII, "[+--]" representa o conjunto de caracteres { '+', ',', '-' }.

No entanto, quando os intervalos que diferenciam a localidade são usados, os caracteres em um intervalo são determinados pelas regras de ordenação da localidade. Os caracteres que são agrupados após o primeiro caractere na definição do intervalo e antes do último caractere na definição do intervalo estão no conjunto. Os dois caracteres finais também estão no conjunto.

### <a name="collating-element"></a>Elemento de agrupamento

Um elemento de agrupamento é uma sequência de vários caracteres que é tratada como um único caractere.

### <a name="collating-symbol"></a>Símbolo de agrupamento

Um símbolo de agrupamento em uma expressão entre colchetes adiciona um *elemento de agrupamento* ao conjunto que é definido pela expressão entre colchetes. Para criar um símbolo de agrupamento, use "[." seguido pelo elemento de agrupamento seguido por ".]".

### <a name="control-escape-sequence"></a>Sequência de escape de controle

Uma sequência de escape de controle é uma barra invertida seguida pela letra 'c', seguida por uma das letras de 'a' a 'z' ou 'A' a 'Z'. Ela corresponde ao caractere de controle ASCII que é nomeado por essa letra. Por exemplo, "\ci" corresponde à sequência de destino "\x09", pois \<ctrl-i> tem o valor 0x09.

### <a name="dsw-character-escape"></a>Escape de caractere DSW

Um escape de caractere dsw é um nome curto para uma classe de caractere, conforme mostrado na tabela a seguir.

|Sequência de escape|Classe nomeada equivalente|Classe nomeada padrão|
|---------------------|----------------------------|-------------------------|
|"\d"|"[[:d:]]"|"[[:digit:]]"|
|"\D"|"[^[:d:]]"|"[^[:digit:]]"|
|"\s"|"[[:s:]]"|"[[:space:]]"|
|"\S"|"[^[:s:]]"|"[^[:space:]]"|
|"\w"|"[[:w:]]"|"[a-zA-Z0-9_]"\*|
|"\W"|"[^[:w:]]"|"[^a-zA-Z0-9_]"\*|

\*Conjunto de caracteres ASCII

### <a name="equivalence-class"></a>Classe de equivalência

Uma classe de equivalência em uma expressão entre colchetes adiciona todos os caracteres e *elementos de agrupamento* que são equivalentes ao elemento de agrupamento na definição de classe de equivalência ao conjunto que é definido pela expressão entre colchetes. Para criar uma classe de equivalência, use "[=" seguida por um elemento de agrupamento seguido por "=]". Internamente, dois elementos de agrupamento, `elt1` e `elt2`, serão equivalentes se `traits.transform_primary(elt1.begin(), elt1.end()) == traits.transform_primary(elt2.begin(), elt2.end())`.

### <a name="file-format-escape"></a>Escape de formato de arquivo

Um escape de formatação de arquivo consiste nas sequências de escape de caractere da linguagem C comum, "\\\\", "\a", "\b", "\f", "\n", "\r", "\t", "\v". Elas têm significados comuns, isto é, barra invertida, alerta, backspace, avanço de página, nova linha, retorno de carro, guia horizontal e guia vertical, respectivamente. Em `ECMAScript`, "\a" e "\b" não são permitidos. ("\\\\" é permitido, mas é um caractere de escape de identidade, não um escape de formatação de arquivo).

### <a name="hexadecimal-escape-sequence"></a>Sequência de escape hexadecimal

Uma sequência de escape hexadecimal é uma barra invertida seguida pela letra 'x' seguida por dois dígitos hexadecimais (0-9a-fA-F). Ela corresponde a um caractere na sequência de destino que tem o valor especificado pelos dois dígitos. Por exemplo, "\x41" corresponde à sequência de destino "A" quando a codificação de caractere ASCII é usada.

### <a name="identity-escape"></a>Escape de identidade

Um escape de identidade é uma barra invertida seguida por um único caractere. Ele corresponde a esse caractere. É obrigatório quando o caractere tem um significado especial; ao usar o escape de identidade, o significado especial é removido. Por exemplo:

- "a\*" corresponde à sequência de destino "AAA", mas não corresponde à sequência de destino "\*a".

- "a\\\*" não corresponde à sequência de destino "AAA", mas corresponde à sequência de destino "\*a".

O conjunto de caracteres que são permitidos em um escape de identidade depende da gramática da expressão regular, conforme mostrado na tabela a seguir.

|Gramática|Caracteres de escape de identidade permitidos|
|-------------|----------------------------------------|
|`basic`, `grep`|{ '(', ')', '{', '}', '.', '[', '\\', '\*', '^', '$' }|
|`extended`, `egrep`|{ '(', ')', '{', '.', '[', '\\', '\*', '^', '$', '+', '?', '&#124;' }|
|`awk`|`extended` mais { '"', '/' }|
|`ECMAScript`|Todos os caracteres, exceto aqueles que podem fazer parte de um identificador. Normalmente, isso inclui letras, dígitos, ' $ ', '\_' e sequências de escape Unicode. Para obter mais informações, consulte a especificação de linguagem ECMAScript.|

### <a name="individual-character"></a>Caractere individual

Um caractere individual em uma expressão entre colchetes adiciona esse caractere ao conjunto de caracteres que é definido pela expressão entre colchetes. Em qualquer lugar em uma expressão entre colchetes, exceto no início, um '^' representa a si mesmo.

Exemplos:

- "[abc]" corresponde às sequências de destino "a", "b" e "c", mas não à sequência "d".

- "[^abc]" corresponde à sequência de destino "d", mas não às sequências de destino "a", "b" ou "c".

- "[a^bc]" corresponde às sequências de destino "a", "b", "c" e "^", mas não à sequência de destino "d".

Em todas as gramáticas de expressão regular, exceto `ECMAScript`, se um ']' for o primeiro caractere que segue o '[' de abertura ou for o primeiro caractere que segue um '^' inicial, ele representará a si mesmo.

Exemplos:

- "[]a" é inválido porque não há ']' para finalizar a expressão entre colchetes.

- "[]abc]" corresponde às sequências de destino "a", "b", "c" e "]", mas não à sequência de destino "d".

- "[^]abc]" corresponde à sequência de destino "d", mas não às sequências de destino "a", "b", "c" ou "]".

Em `ECMAScript`, use '\\' para representar o caractere ']' em uma expressão entre colchetes.

Exemplos:

- "[]a" corresponde à sequência de destino "a" porque a expressão entre colchetes está vazia.

- "[\\]abc]" corresponde às sequências de destino "a", "b", "c" e "]", mas não à sequência de destino "d".

### <a name="negative-assert"></a>Declaração negativa

Uma declaração negativa corresponde a qualquer item, menos a seu conteúdo. Ela não consome nenhum caractere na sequência de destino. Por exemplo, "(! AA) (a\*)" corresponde à sequência de destino "a" e associa o grupo 1 de captura com a subsequência "a". Ela não corresponde à sequência de destino "aa" ou à sequência de destino "aaa".

### <a name="negative-word-boundary-assert"></a>Declaração de limite de palavra negativa

Uma asserção do limite de palavra negativa corresponderá se a posição atual na cadeia de caracteres de destino não vier logo após um *limite de palavra*.

### <a name="non-capture-group"></a>Grupo de não captura

Um grupo de não captura marca seu conteúdo como uma unidade única na gramática da expressão regular, mas não rotula o texto de destino. Por exemplo, "(a) (?: b)\*(c)" corresponde ao texto de destino "abbc" e associa o grupo 1 de captura com a subsequência "a" e captura o grupo 2 com a subsequência "c".

### <a name="non-greedy-repetition"></a>Repetição não greedy

Uma repetição não greedy consome a subsequência mais curta da sequência de destino que corresponde ao padrão. Uma repetição greedy consome a mais longa. Por exemplo, "(a +) (a\*b)" corresponde à sequência de destino "aaab". Quando uma repetição não greedy é usada, ela associa o grupo de captura 1 à subsequência "a" no início da sequência de destino e o grupo de captura 2 à subsequência "aab" no fim da sequência de destino. Quando uma correspondência greedy é usada, ela associa o grupo de captura 1 à subsequência "aaa" e o grupo de captura 2 à subsequência "b".

### <a name="octal-escape-sequence"></a>Sequência de escape octal

Uma sequência de escape octal é uma barra invertida seguida por um, dois ou três dígitos octais (0-7). Ela corresponde a um caractere na sequência de destino que tem o valor especificado por esses dígitos. Se todos os dígitos forem '0', a sequência será inválida. Por exemplo, "\101" corresponde à sequência de destino "A" quando a codificação de caractere ASCII é usada.

### <a name="ordinary-character"></a>Caractere comum

Um caractere comum é qualquer caractere válido que não tem um significado especial na gramática atual.

Em `ECMAScript`, os seguintes caracteres têm significados especiais:

- ^  $  \  .  \*  +  ?  (  )  \[  ]  {  }&#124;

Em `basic` e `grep`, os seguintes caracteres têm significados especiais:

- .   \[   \

Além disso, em `basic` e `grep`, os seguintes caracteres têm significados especiais quando são usados em um determinado contexto:

- '\*' tem um significado especial em todos os casos, exceto quando é o primeiro caractere em uma expressão regular ou o primeiro caractere que segue um ' ^ ' inicial em uma expressão regular, ou quando é o primeiro caractere de um grupo de captura ou o primeiro caractere que segue um ' ^ ' inicial em um grupo de captura.

- '^' tem um significado especial quando ele for o primeiro caractere de uma expressão regular.

- '$' tem um significado especial quando ele é o último caractere de uma expressão regular.

Em `extended`, `egrep` e `awk`, os seguintes caracteres têm significados especiais:

- .   \[   \   (   \*   +   ?   {   &#124;

Além disso, em `extended`, `egrep` e `awk`, os seguintes caracteres têm significados especiais quando são usados em um determinado contexto.

- ')' tem um significado especial quando corresponde a um '(' precedente.

- '^' tem um significado especial quando ele for o primeiro caractere de uma expressão regular.

- '$' tem um significado especial quando ele é o último caractere de uma expressão regular.

Um caractere comum que corresponde ao mesmo caractere na sequência de destino. Por padrão, isso significa que a correspondência será bem-sucedida se dois caracteres forem representados pelo mesmo valor. Em uma correspondência que não diferencia letras maiúsculas e minúsculas, dois caracteres `ch0` e `ch1` corresponderão se `traits.translate_nocase(ch0) == traits.translate_nocase(ch1)`. Em uma correspondência que diferencia a localidade, dois caracteres `ch0` e `ch1` corresponderão se `traits.translate(ch0) == traits.translate(ch1)`.

### <a name="positive-assert"></a>Declaração positiva

Uma declaração positiva corresponde a seu conteúdo, mas não consome nenhum caractere na sequência de destino.

Exemplos:

- "(= AA) (a\*)" corresponde à sequência de destino "aaaa" e associa o grupo 1 de captura com a subsequência "aaaa".

- "(AA) (a\*)" corresponde à sequência de destino "aaaa" e associa o grupo 1 de captura com a subsequência "AA" no início da sequência de destino e captura o grupo 2 com a subsequência "AA" no final da sequência de destino.

- "(=aa)(a)&#124;(a)" corresponde à sequência de destino "a" e associa o grupo de captura 1 a uma sequência vazia (pois a asserção positiva falhou) e o grupo de captura 2 ao "a" subsequente. Ele também corresponde à sequência de destino "aa" e associa o grupo de captura 1 à subsequência "aa" e o grupo de captura 2 a uma sequência vazia.

### <a name="unicode-escape-sequence"></a>Sequência de escape Unicode

Uma sequência de escape unicode é uma barra invertida seguida pela letra 'u' seguida por quatro dígitos hexadecimais (0-9a-fA-F). Ela corresponde a um caractere na sequência de destino que tem o valor especificado pelos quatro dígitos. Por exemplo, "\u0041" corresponde à sequência de destino "A" quando a codificação de caractere ASCII é usada.

### <a name="wildcard-character"></a>Caractere curinga

Um caractere curinga que corresponde a qualquer caractere na expressão de destino, exceto a uma nova linha.

### <a name="word-boundary"></a>Limite de palavra

Um limite de palavra ocorre nas seguintes situações:

- O caractere atual está no início da sequência de destino e é um dos caracteres da palavra `A-Za-z0-9_.`

- A posição do caractere atual está após o fim da sequência de destino e o último caractere na sequência de destino é um dos caracteres da palavra.

- O caractere atual é um dos caracteres da palavra e o caractere precedente, não.

- O caractere atual não é um dos caracteres da palavra e o caractere precedente, sim.

### <a name="word-boundary-assert"></a>Declaração de limite de palavra

Uma asserção do limite de palavra corresponderá quando a posição atual na cadeia de caracteres de destino vier logo após um *limite de palavra*.

## <a name="matchingandsearching"></a> Correspondência e pesquisa

Para que uma expressão regular corresponda a uma sequência de destino, a expressão regular inteira deverá corresponder à sequência de destino inteira. Por exemplo, a expressão regular "bcd" corresponde à sequência de destino "bcd", mas não corresponde à sequência de destino "abcd", nem à sequência de destino "bcde".

Para que uma pesquisa de expressão regular seja bem-sucedida, deve haver uma subsequência em algum lugar na sequência de destino que corresponda à expressão regular. Geralmente, a pesquisa encontra a subsequência correspondente à extrema esquerda.

Exemplos:

- Uma pesquisa pela expressão regular "bcd" na sequência de destino "bcd" é bem-sucedida e corresponde à sequência inteira. A mesma pesquisa na sequência de destino "abcd" também é bem-sucedida e corresponde aos três últimos caracteres. A mesma pesquisa na sequência de destino "bcde" também é bem-sucedida e corresponde aos três primeiros caracteres.

- Uma pesquisa pela expressão regular "bcd" na sequência de destino "bcdbcd" é bem-sucedida e corresponde aos três primeiros caracteres.

Se houver mais de uma subsequência que corresponda em algum local na sequência de destino, há duas maneiras de escolher o padrão correspondente. A *primeira correspondência* escolhe a subsequência que foi encontrada primeiro quando a expressão regular é correspondida. A *correspondência mais longa* escolhe a subsequência mais longa dentre aquelas com correspondência nesse local. Se houver mais de uma subsequência que tenha comprimento máximo, a correspondência mais longa escolherá aquela que foi encontrada primeiro. Por exemplo, quando a primeira correspondência é usada, uma pesquisa pela expressão regular "b&#124;bc" na sequência de destino "abcd" corresponde à subsequência "b", pois o termo da alternância do lado esquerdo corresponde a essa subsequência; portanto, a primeira correspondência não tenta o termo da alternância do lado direito. Quando a correspondência mais longa é usada, a mesma pesquisa corresponde a "bc" porque "bc" é mais longo que "b".

Uma correspondência parcial será bem-sucedida se a correspondência atingir o fim da sequência de destino sem falhar, mesmo que ela não tenha atingido o fim da expressão regular. Dessa forma, depois do êxito de uma correspondência parcial, acrescentar caracteres à sequência de destino pode causar uma falha em uma correspondência parcial posterior. No entanto, após a falha de uma correspondência parcial, acrescentar caracteres à sequência de destino não fará com uma correspondência parcial posterior seja bem-sucedida. Por exemplo, com uma correspondência parcial, "ab" corresponde à sequência de destino "a", mas não à "ac".

## <a name="formatflags"></a> Sinalizadores de formato

|Regras de formato de ECMAScript|Regras de formato sed|Texto de substituição|
|-----------------------------|----------------------|----------------------|
|"$&"|"&"|A sequência de caracteres que corresponde à expressão regular inteira (`[match[0].first, match[0].second)`)|
|"$$"||"$"|
||"\\&"|"&"|
|"$\`" (cifrão seguido de aspas de fundo)||A sequência de caracteres que precede a subsequência que corresponde à expressão regular (`[match.prefix().first, match.prefix().second)`)|
|"$'" (cifrão de dólar seguido por aspas simples)||A sequência de caracteres que segue a subsequência que corresponde à expressão regular (`[match.suffix().first, match.suffix().second)`)|
|"$n"|"\n"|A sequência de caracteres que corresponde ao grupo de captura `n`na posição `n` , em que é um número entre 0`[match[n].first, match[n].second)`e 9 ()|
||"\\\n"|"\n"|
|"$nn"||A sequência de caracteres que corresponde ao grupo de captura `nn`na posição `nn` , em que é um número entre 10`[match[nn].first, match[nn].second)`e 99 ()|

## <a name="see-also"></a>Consulte também

[Visão geral da biblioteca padrão C++](../standard-library/cpp-standard-library-overview.md)
