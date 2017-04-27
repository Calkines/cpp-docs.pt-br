---
title: "Declarações de matriz | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: e4e3f584f020ef1492b05a04a64e590c3ddd5761
ms.lasthandoff: 02/25/2017

---
# <a name="array-declarations"></a>Declarações de matriz
Uma "declaração de matriz" nomeia a matriz e especifica o tipo dos respectivos elementos. Também pode definir o número de elementos na matriz. Uma variável com tipo de matriz é considerada um ponteiro para o tipo dos elementos da matriz.  
  
## <a name="syntax"></a>Sintaxe  
 `declaration`:  
 *declaration-specifiers init-declarator-list* opt**;**  
  
 *init-declarator-list*:  
 *init-declarator*  
  
 *init-declarator-list* **,**  *init-declarator*  
  
 *init-declarator*:  
 *declarator*  
  
 *declarator*  **=**  *initializer*  
  
 `declarator`:  
 *pointer* opt*direct-declarator*  
  
 *direct-declarator*:  
 *direct-declarator*  **[**  *constant-expression* opt**]**  
  
 Como *constant-expression* é opcional, a sintaxe tem dois formatos:  
  
-   O primeiro formato define uma variável de matriz. O argumento *constant-expression* entre colchetes especifica o número de elementos na matriz. O *constant-expression*, se estiver presente, deve ter um tipo integral e um valor maior que zero. Cada elemento tem o tipo indicado por *type-specifier*, que pode ser qualquer tipo exceto `void`. Um elemento de matriz não pode ser um tipo de função.  
  
-   O segundo formato declara uma variável que foi definida em outro lugar. Ele omite o argumento *constant-expression* entre colchetes, mas não os colchetes. Você só poderá usar esse formato se tiver inicializado a matriz anteriormente, se a tiver declarado como um parâmetro ou se a tiver declarado como uma referência a uma matriz definida explicitamente em outro lugar no programa.  
  
 Nos dois formatos, *direct-declarator* nomeia a variável e pode modificar o tipo dela. Os colchetes (**[ ]**) depois de *direct-declarator* modificam o declarador para um tipo de matriz.  
  
 Qualificadores de tipo podem aparecer na declaração de um objeto de tipo de matriz, mas se aplicam aos elementos, e não à própria matriz.  
  
 Você pode declarar uma matriz de matrizes (uma matriz "multidimensional") colocando uma lista de expressões de constantes entre colchetes após o declarador de matriz, neste formato:  
  
```  
  
type-specifier  
declarator [constant-expression] [constant-expression] ...  
```  
  
 Cada *constant-expression* entre colchetes define o número de elementos em uma determinada dimensão: as matrizes bidimensionais têm duas expressões entre colchetes, as matrizes tridimensionais têm três e assim por diante. Você poderá omitir a primeira expressão de constante se tiver inicializado a matriz, se a tiver declarado como um parâmetro ou se a tiver declarado como uma referência a uma matriz definida explicitamente em outro lugar no programa.  
  
 É possível definir matrizes de ponteiros para diversos tipos de objetos usando declaradores complexos, conforme descrito em [Interpretar declaradores mais complexos](../c-language/interpreting-more-complex-declarators.md).  
  
 As matrizes são armazenadas por linha. Por exemplo, a seguinte matriz consiste em duas linhas com três colunas cada:  
  
```  
char A[2][3];  
```  
  
 As três colunas da primeira linha são armazenadas primeiro, seguidas pelas três colunas da segunda linha. Isso significa que o último subscrito varia mais rapidamente.  
  
 Para fazer referência a um elemento individual de uma matriz, use uma expressão de subscrito, conforme descrito em [Operadores pós-fixados](../c-language/postfix-operators.md).  
  
## <a name="examples"></a>Exemplos  
 Estes exemplos ilustram declarações de matrizes:  
  
```  
float matrix[10][15];  
```  
  
 A matriz bidimensional nomeada `matrix` tem 150 elementos, cada um deles com o tipo **float**.  
  
```  
struct {  
    float x, y;  
} complex[100];  
```  
  
 Essa é uma declaração de uma matriz de estruturas. Essa matriz tem 100 elementos; cada elemento é uma estrutura que contém dois membros.  
  
```  
extern char *name[];  
```  
  
 Essa instrução declara o tipo e o nome de uma matriz de ponteiros para `char`. A definição real de `name` ocorre em outro lugar.  
  
 **Seção específica da Microsoft**  
  
 O tipo de inteiro necessário para manter o tamanho máximo de uma matriz é o tamanho de **size_t**. Definido no arquivo de cabeçalho STDDEF.H, **size_t** é um `unsigned int` com o intervalo de 0x00000000 a 0x7CFFFFFF.  
  
 **Fim da seção específica da Microsoft**  
  
## <a name="see-also"></a>Consulte também  
 [Declaradores e declarações de variável](../c-language/declarators-and-variable-declarations.md)