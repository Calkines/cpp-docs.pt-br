---
title: Classe CTime | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTime
- ATLTIME/ATL::CTime
- ATLTIME/ATL::CTime::CTime
- ATLTIME/ATL::CTime::Format
- ATLTIME/ATL::CTime::FormatGmt
- ATLTIME/ATL::CTime::GetAsDBTIMESTAMP
- ATLTIME/ATL::CTime::GetAsSystemTime
- ATLTIME/ATL::CTime::GetCurrentTime
- ATLTIME/ATL::CTime::GetDay
- ATLTIME/ATL::CTime::GetDayOfWeek
- ATLTIME/ATL::CTime::GetGmtTm
- ATLTIME/ATL::CTime::GetHour
- ATLTIME/ATL::CTime::GetLocalTm
- ATLTIME/ATL::CTime::GetMinute
- ATLTIME/ATL::CTime::GetMonth
- ATLTIME/ATL::CTime::GetSecond
- ATLTIME/ATL::CTime::GetTime
- ATLTIME/ATL::CTime::GetYear
- ATLTIME/ATL::CTime::Serialize64
dev_langs:
- C++
helpviewer_keywords:
- CTime class
- shared classes, CTime
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
caps.latest.revision: 30
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 22e488a1c5760c342ce79c42cd8a48c911715b23
ms.lasthandoff: 04/01/2017

---
# <a name="ctime-class"></a>Classe CTime
Representa uma data e hora absoluta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class CTime  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CTime::CTime](#ctime)|Constrói `CTime` objetos de várias maneiras.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CTime::Format](#format)|Converte um `CTime` objeto em uma cadeia de caracteres formatada — com base no fuso horário local.|  
|[CTime::FormatGmt](#formatgmt)|Converte um `CTime` objeto em uma cadeia de caracteres formatada — com base no UTC.|  
|[CTime::GetAsDBTIMESTAMP](#getasdbtimestamp)|Converte as informações de hora armazenadas no `CTime` objeto a uma estrutura compatível com Win32 DBTIMESTAMP.|  
|[CTime::GetAsSystemTime](#getassystemtime)|Converte as informações de hora armazenadas no `CTime` objeto para um compatível com Win32 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estrutura.|  
|[CTime::GetCurrentTime](#getcurrenttime)|Cria um `CTime` objeto que representa a hora atual (função de membro estático).|  
|[CTime::GetDay](#getday)|Retorna que representa o dia pelo `CTime` objeto.|  
|[CTime::GetDayOfWeek](#getdayofweek)|Retorna o dia da semana representado pelo `CTime` objeto.|  
|[CTime::GetGmtTm](#getgmttm)|Divide um `CTime` objeto em componentes, com base no UTC.|  
|[CTime::GetHour](#gethour)|Retorna a hora representada pelo `CTime` objeto.|  
|[CTime::GetLocalTm](#getlocaltm)|Divide um `CTime` objeto em componentes, com base no fuso horário local.|  
|[CTime::GetMinute](#getminute)|Retorna o minuto representado pelo `CTime` objeto.|  
|[CTime::GetMonth](#getmonth)|Retorna o mês representado pelo `CTime` objeto.|  
|[CTime::GetSecond](#getsecond)|Retorna o segundo representado pelo `CTime` objeto.|  
|[CTime::GetTime](#gettime)|Retorna um **__time64_t** valor para o determinado `CTime` objeto.|  
|[CTime::GetYear](#getyear)|Retorna o ano que representa o `CTime` objeto.|  
|[CTime::Serialize64](#serialize64)|Serializa os dados de ou para um arquivo morto.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador + -](#operator_add_-)|Esses operadores de adição e subtração `CTimeSpan` e `CTime` objetos.|  
|[+ = do operador-=](#operator_add_eq_-_eq)|Esses operadores adicionar e subtrair um `CTimeSpan` objeto neste `CTime` objeto.|  
|[operador =](#operator_eq)|O operador de atribuição.|  
|[operador = =,< ,="">](#ctime_comparison_operators)|Operadores de comparação.|  
  
## <a name="remarks"></a>Comentários  
 `CTime`não tem uma classe base.  
  
 `CTime`valores são baseados em tempo universal coordenado (UTC), que é equivalente ao horário coordenado Universal (hora de Greenwich, GMT). Consulte [gerenciamento de tempo](../../c-runtime-library/time-management.md) para obter informações sobre como o fuso horário é determinado.  
  
 Quando você cria um `CTime` do objeto, defina o `nDST` parâmetro como 0 para indicar que hora padrão está em vigor, ou para um valor maior que 0 para indicar que o horário de verão está em vigor ou para um valor menor que zero para que a computação de código de biblioteca de tempo de execução C se o horário de verão ou de hora padrão está em vigor. `tm_isdst` é um campo obrigatório. Se não estiver definida, seu valor será indefinido e o valor de retorno [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) é imprevisível. Se `timeptr` aponta para uma estrutura de tm retornada por uma chamada anterior a [asctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md), [gmtime_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), ou [localtime_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), o `tm_isdst` campo contém o valor correto.  
  
 Uma classe complementar, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), representa um intervalo de tempo.  
  
 O `CTime` e `CTimeSpan` classes não são projetadas para derivação. Porque não há nenhuma função virtual, o tamanho de `CTime` e `CTimeSpan` objetos é exatamente 8 bytes. A maioria das funções de membro são embutidos.  
  
> [!NOTE]
>  O limite superior de data é 31/12/3000. O limite mínimo é 1/1/1970 12:00:00 AM GMT.  
  
 Para obter mais informações sobre como usar `CTime`, consulte os artigos [data e hora](../../atl-mfc-shared/date-and-time.md), e [gerenciamento de tempo](../../c-runtime-library/time-management.md) na referência de biblioteca de tempo de execução.  
  
> [!NOTE]
>  O `CTime` estrutura alterada do MFC 7.1 para MFC 8.0. Se você serializar um `CTime` estrutura usando o `operator <<` em MFC 8.0 ou posterior, o arquivo resultante não será legível em versões mais antigas do MFC.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** atltime.h  
  
##  <a name="ctime_comparison_operators"></a>Operadores de comparação CTime  
 Operadores de comparação.  
  
```  
bool operator==(CTime time) const throw(); 
bool operator!=(CTime time) const throw();
bool operator<(CTime time) const throw();
bool operator>(CTime time) const throw();
bool operator<=(CTime time) const throw();
bool operator>=(CTime time) const throw(); 
```  
  
### <a name="parameters"></a>Parâmetros  
 `time`  
 O objeto `CTime` a ser comparado.  
  
### <a name="return-value"></a>Valor de retorno  
 Esses operadores comparar duas vezes absolutos e retornar **true** se a condição for true; caso contrário **false**.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #161](../../atl-mfc-shared/codesnippet/cpp/ctime-class_1.cpp)]  
  
##  <a name="ctime"></a>CTime::CTime  
 Cria um novo `CTime` objeto inicializado com o tempo especificado.  
  
```  
CTime() throw(); 
CTime(__time64_t time) throw();
CTime(int nYear, int nMonth, int nDay,
      int nHour, int nMin, int nSec, int nDST = -1);
CTime(WORD wDosDate, WORD wDosTime, int nDST = -1);
CTime(const SYSTEMTIME& st, int nDST = - 1) throw();
CTime(const FILETIME& ft, int nDST = - 1);
CTime(const DBTIMESTAMP& dbts,int nDST = -1) throw();
```  
  
### <a name="parameters"></a>Parâmetros  
 `timeSrc`  
 Indica um `CTime` objeto já existe.  
  
 `time`  
 Um **__time64_t** valor de tempo, que é o número de segundos após 1º de janeiro de 1970 UTC. Observe que isso será ajustado para o horário local. Por exemplo, se você estiver em Nova York e cria um `CTime` objeto passando um parâmetro de 0, [CTime::GetMonth](#getmonth) retornará 12.  
  
 Em versões do Visual C++ 6.0 e versões anteriores, `time` era um valor de `time_t`. Visual C++ .NET e posterior converte um `time_t` parâmetro **__time64_t**.  
  
 `nYear`, `nMonth`, `nDay`, `nHour`, `nMin`, `nSec`  
 Indica os valores de data e hora a ser copiado para a nova `CTime` objeto.  
  
 `nDST`  
 Indica se o horário de verão está em vigor. Pode ter um dos três valores:  
  
- `nDST`definido como tempo 0Standard está em vigor.  
  
- `nDST`Defina como um valor maior que 0Daylight horário está em vigor.  
  
- `nDST`definido como um valor menor que 0The padrão. Calcula automaticamente se o horário de verão ou de hora padrão está em vigor.  
  
 `wDosDate`, `wDosTime`  
 Valores de data e hora do MS-DOS a ser convertido em um valor de data/hora e copiado para o novo `CTime` objeto.  
  
 `st`  
 Um [SYSTEMTIME](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/d6609fff-1931-4818-8a26-f042630af0b0/locales/en-us) estrutura a ser convertido em um valor de data/hora e copiados para a nova `CTime` objeto.  
  
 `ft`  
 Um [FILETIME](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/979ce746-dc17-4147-89f8-41d05c5fcc5f/locales/en-us) estrutura a ser convertido em um valor de data/hora e copiados para a nova `CTime` objeto.  
  
 DBTS  
 Uma referência a uma estrutura DBTIMESTAMP que contém a hora local atual.  
  
### <a name="remarks"></a>Comentários  
 Cada construtor é descrito abaixo:  
  
- **CTime();** Constrói um não inicializada `CTime` objeto. Este construtor permite que você defina `CTime` matrizes do objeto. Você deve inicializar esses matrizes com horas válidas antes de usar.  
  
- **CTime (CTime const &);** Constrói um `CTime` objeto de outro `CTime` valor.  
  
- **CTime (__time64_t);** Constrói um `CTime` de objeto um **__time64_t** tipo. Este construtor espera uma hora UTC e converte o resultado em uma hora local antes de armazenar o resultado.  
  
- **CTime (int, int,...);** Constrói um `CTime` objeto dos componentes de hora local com cada componente restrita para os seguintes intervalos:  
  
    |Componente|Intervalo|  
    |---------------|-----------|  
    |`nYear`|1970-3000|  
    |`nMonth`|1-12|  
    |`nDay`|1-31|  
    |`nHour`|0-23|  
    |`nMin`|0-59|  
    |`nSec`|0-59|  
  
     Este construtor faz a conversão apropriada para UTC. A versão de depuração da biblioteca de classes Microsoft Foundation declara se um ou mais dos componentes de tempo estão fora do intervalo. Você deve validar os argumentos antes de chamar. Este construtor espera que a hora local.  
  
- **CTime (WORD, palavra);** Constrói um `CTime` objeto entre os valores de data e hora de MS-DOS especificados. Este construtor espera que a hora local.  
  
- **CTime (SYSTEMTIME const &);** Constrói um `CTime` de objeto um `SYSTEMTIME` estrutura. Este construtor espera que a hora local.  
  
- **CTime (FILETIME const &);** Constrói um `CTime` de objeto um `FILETIME` estrutura. Você provavelmente não usará `CTime FILETIME` inicialização diretamente. Se você usar um `CFile` objeto para manipular um arquivo, `CFile::GetStatus` recupera o carimbo de hora do arquivo para você por meio de um `CTime` objeto inicializado com um `FILETIME` estrutura. Este construtor assume um tempo com base no UTC e converte o valor automaticamente para a hora local antes de armazenar o resultado.  
  
    > [!NOTE]
    >  Usando o construtor **DBTIMESTAMP** parâmetro está disponível apenas quando OLEDB é incluído.  
  
 Para obter mais informações, consulte o [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) e [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284) estrutura no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Consulte também o [MS-DOS data e hora](http://msdn.microsoft.com/library/windows/desktop/ms724503) entrada o [!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #148](../../atl-mfc-shared/codesnippet/cpp/ctime-class_2.cpp)]  
  
##  <a name="format"></a>CTime::Format  
 Chame essa função de membro para criar uma representação formatada do valor de data e hora.  
  
```  
CString Format(LPCTSTR pszFormat) const; 
CString Format(UINT nFormatID) const; 
```  
  
### <a name="parameters"></a>Parâmetros  
 `pszFormat`  
 Uma formatação de cadeia de caracteres semelhante de `printf` cadeia de caracteres de formatação. Códigos de formatação, precedidos por uma porcentagem ( `%`) entre, são substituídos por correspondente `CTime` componente. Outros caracteres na cadeia de formatação são copiados inalterada para cadeia de caracteres retornada. Consulte a função de tempo de execução [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para obter uma lista de códigos de formatação.  
  
 `nFormatID`  
 A ID da cadeia de caracteres que identifica esse formato.  
  
### <a name="return-value"></a>Valor de retorno  
 Um [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contém a hora formatada.  
  
### <a name="remarks"></a>Comentários  
 Se o status deste `CTime` objeto é nulo, o valor de retorno é uma cadeia de caracteres vazia.  
  
 Este método lança uma exceção se o valor de data e hora para o formato não desde a meia-noite de 1 de janeiro de 1970 por meio de 31 de dezembro de 3000 Horário Coordenado Universal (UTC).  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #149](../../atl-mfc-shared/codesnippet/cpp/ctime-class_3.cpp)]  
  
##  <a name="formatgmt"></a>CTime::FormatGmt  
 Gera uma cadeia de caracteres formatada que corresponde a este `CTime` objeto.  
  
```  
CString FormatGmt(LPCTSTR pszFormat) const; 
CString FormatGmt(UINT nFormatID) const; 
```  
  
### <a name="parameters"></a>Parâmetros  
 `pszFormat`  
 Especifica uma cadeia de formatação semelhante para o `printf` cadeia de caracteres de formatação. Consulte a função de tempo de execução [strftime](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md) para obter detalhes.  
  
 `nFormatID`  
 A ID da cadeia de caracteres que identifica esse formato.  
  
### <a name="return-value"></a>Valor de retorno  
 Um [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contém a hora formatada.  
  
### <a name="remarks"></a>Comentários  
 O valor de tempo não é convertido e, portanto, reflete o UTC.  
  
 Este método lança uma exceção se o valor de data e hora para o formato não desde a meia-noite de 1 de janeiro de 1970 por meio de 31 de dezembro de 3000 Horário Coordenado Universal (UTC).  
  
### <a name="example"></a>Exemplo  
 Consulte o exemplo para [CTime::Format](#format).  
  
##  <a name="getasdbtimestamp"></a>CTime::GetAsDBTIMESTAMP  
 Chamar essa função de membro para converter as informações de hora armazenadas no `CTime` objeto a uma estrutura compatível com Win32 DBTIMESTAMP.  
  
```  
bool GetAsDBTIMESTAMP(DBTIMESTAMP& dbts) const throw();
```  
  
### <a name="parameters"></a>Parâmetros  
 `dbts`  
 Uma referência a uma estrutura DBTIMESTAMP que contém a hora local atual.  
  
### <a name="return-value"></a>Valor de retorno  
 Diferente de zero se for bem-sucedida; Caso contrário, 0.  
  
### <a name="remarks"></a>Comentários  
 Armazena a hora resultante referenciado `dbts` estrutura. O **DBTIMESTAMP** estrutura de dados inicializada por essa função terá seu **fração** membro definido como zero.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #150](../../atl-mfc-shared/codesnippet/cpp/ctime-class_4.cpp)]  
  
##  <a name="getassystemtime"></a>CTime::GetAsSystemTime  
 Chamar essa função de membro para converter as informações de hora armazenadas no `CTime` objeto para um compatível com Win32 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estrutura.  
  
```  
bool GetAsSystemTime(SYSTEMTIME& st) const throw();
```  
  
### <a name="parameters"></a>Parâmetros  
 *timeDest*  
 Uma referência a um [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estrutura que conterá o valor de data/hora convertido do `CTime` objeto.  
  
### <a name="return-value"></a>Valor de retorno  
 VERDADEIRO se bem-sucedido; Caso contrário, false.  
  
### <a name="remarks"></a>Comentários  
 `GetAsSystemTime`armazena a hora resultante referenciado *timeDest* estrutura. O `SYSTEMTIME` estrutura de dados inicializada por essa função terá seu **Wsegundo** membro definido como zero.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #151](../../atl-mfc-shared/codesnippet/cpp/ctime-class_5.cpp)]  
  
##  <a name="getcurrenttime"></a>CTime::GetCurrentTime  
 Retorna um `CTime` objeto que representa a hora atual.  
  
```  
static CTime WINAPI GetCurrentTime() throw();
```  
  
### <a name="remarks"></a>Comentários  
 Retorna a data atual do sistema e a hora em tempo Universal Coordenado (UTC).  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #152](../../atl-mfc-shared/codesnippet/cpp/ctime-class_6.cpp)]  
  
##  <a name="getday"></a>CTime::GetDay  
 Retorna que representa o dia pelo `CTime` objeto.  
  
```  
int GetDay() const throw(); 
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna o dia do mês, com base na hora local, no intervalo de 1 a 31.  
  
### <a name="remarks"></a>Comentários  
 Esta função chama `GetLocalTm`, que utiliza um buffer interno, em alocados estaticamente. Os dados nesse buffer são substituídos por causa de chamadas para outros `CTime` funções de membro.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #153](../../atl-mfc-shared/codesnippet/cpp/ctime-class_7.cpp)]  
  
##  <a name="getdayofweek"></a>CTime::GetDayOfWeek  
 Retorna o dia da semana representado pelo `CTime` objeto.  
  
```  
int GetDayOfWeek() const throw(); 
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna o dia da semana com base na hora local; 1 = domingo, 2 = segunda-feira, 7 = sábado.  
  
### <a name="remarks"></a>Comentários  
 Esta função chama `GetLocalTm`, que usa um interno estaticamente buffer alocado. Os dados nesse buffer são substituídos por causa de chamadas para outros `CTime` funções de membro.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #154](../../atl-mfc-shared/codesnippet/cpp/ctime-class_8.cpp)]  
  
##  <a name="getgmttm"></a>CTime::GetGmtTm  
 Obtém um **struct tm** que contém uma Decomposição da hora contida na `CTime` objeto.  
  
```  
struct tm* GetGmtTm(struct tm* ptm) const; 
```  
  
### <a name="parameters"></a>Parâmetros  
 `ptm`  
 Aponta para um buffer que receberá os dados de tempo. Se esse ponteiro for **nulo**, uma exceção será lançada.  
  
### <a name="return-value"></a>Valor de retorno  
 Um ponteiro para um preenchido **struct tm** conforme definido no arquivo de inclusão do tempo. H. Consulte [gmtime, gmtime32, gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) para o layout da estrutura.  
  
### <a name="remarks"></a>Comentários  
 `GetGmtTm`Retorna o UTC.  
  
 `ptm` não pode ser `NULL`. Se você deseja reverter para o comportamento antigo, no qual `ptm` poderia ser `NULL` para indicar que um buffer interno, em alocados estaticamente deve ser usado, em seguida, exclua `_SECURE_ATL`.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #155](../../atl-mfc-shared/codesnippet/cpp/ctime-class_9.cpp)]  
  
##  <a name="gethour"></a>CTime::GetHour  
 Retorna a hora representada pelo `CTime` objeto.  
  
```  
int GetHour() const throw(); 
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna a hora, com base na hora local, no intervalo de 0 a 23.  
  
### <a name="remarks"></a>Comentários  
 Esta função chama `GetLocalTm`, que usa um interno estaticamente buffer alocado. Os dados nesse buffer são substituídos por causa de chamadas para outros `CTime` funções de membro.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #156](../../atl-mfc-shared/codesnippet/cpp/ctime-class_10.cpp)]  
  
##  <a name="getlocaltm"></a>CTime::GetLocalTm  
 Obtém um **struct tm** contendo uma Decomposição da hora contida na `CTime` objeto.  
  
```  
struct tm* GetLocalTm(struct tm* ptm) const; 
```  
  
### <a name="parameters"></a>Parâmetros  
 `ptm`  
 Aponta para um buffer que receberá os dados de tempo. Se esse ponteiro for **nulo**, uma exceção será lançada.  
  
### <a name="return-value"></a>Valor de retorno  
 Um ponteiro para um preenchido **struct tm** conforme definido no arquivo de inclusão do tempo. H. Consulte [gmtime, gmtime32, gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md) para o layout da estrutura.  
  
### <a name="remarks"></a>Comentários  
 `GetLocalTm`Retorna a hora local.  
  
 `ptm` não pode ser `NULL`. Se você deseja reverter para o comportamento antigo, no qual `ptm` poderia ser `NULL` para indicar que um buffer interno, em alocados estaticamente deve ser usado, em seguida, exclua `_SECURE_ATL`.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #157](../../atl-mfc-shared/codesnippet/cpp/ctime-class_11.cpp)]  
  
##  <a name="getminute"></a>CTime::GetMinute  
 Retorna o minuto representado pelo `CTime` objeto.  
  
```  
int GetMinute() const throw(); 
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna o minuto, com base na hora local, no intervalo de 0 a 59.  
  
### <a name="remarks"></a>Comentários  
 Esta função chama `GetLocalTm`, que usa um interno estaticamente buffer alocado. Os dados nesse buffer são substituídos por causa de chamadas para outros `CTime` funções de membro.  
  
### <a name="example"></a>Exemplo  
 Consulte o exemplo para [GetHour](#gethour).  
  
##  <a name="getmonth"></a>CTime::GetMonth  
 Retorna o mês representado pelo `CTime` objeto.  
  
```  
int GetMonth() const throw(); 
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna o mês, com base na hora local, no intervalo de 1 a 12 (1 = janeiro).  
  
### <a name="remarks"></a>Comentários  
 Esta função chama `GetLocalTm`, que usa um interno estaticamente buffer alocado. Os dados nesse buffer são substituídos por causa de chamadas para outros `CTime` funções de membro.  
  
### <a name="example"></a>Exemplo  
 Consulte o exemplo para [GetDay](#getday).  
  
##  <a name="getsecond"></a>CTime::GetSecond  
 Retorna o segundo representado pelo `CTime` objeto.  
  
```  
int GetSecond() const throw(); 
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna o segundo, com base na hora local, no intervalo de 0 a 59.  
  
### <a name="remarks"></a>Comentários  
 Esta função chama `GetLocalTm`, que usa um interno estaticamente buffer alocado. Os dados nesse buffer são substituídos por causa de chamadas para outros `CTime` funções de membro.  
  
### <a name="example"></a>Exemplo  
 Consulte o exemplo para [GetHour](#gethour).  
  
##  <a name="gettime"></a>CTime::GetTime  
 Retorna um **__time64_t** valor para o determinado `CTime` objeto.  
  
```  
__time64_t GetTime() const throw(); 
```  
  
### <a name="return-value"></a>Valor de retorno  
 **GetTime** retornará o número de segundos entre o momento `CTime` objeto e 1º de janeiro de 1970.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #158](../../atl-mfc-shared/codesnippet/cpp/ctime-class_12.cpp)]  
  
##  <a name="getyear"></a>CTime::GetYear  
 Retorna o ano que representa o `CTime` objeto.  
  
```  
int GetYear();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna o ano, com base na hora local, no intervalo de janeiro 1,1970 para 18 de janeiro de 2038 (inclusivo).  
  
### <a name="remarks"></a>Comentários  
 Esta função chama `GetLocalTm`, que usa um interno estaticamente buffer alocado. Os dados nesse buffer são substituídos por causa de chamadas para outros `CTime` funções de membro.  
  
### <a name="example"></a>Exemplo  
 Consulte o exemplo para [GetDay](#getday).  
  
##  <a name="operator_eq"></a>CTime::operator =  
 O operador de atribuição.  
  
```  
CTime& operator=(__time64_t time) throw();
```  
  
### <a name="parameters"></a>Parâmetros  
 `time`  
 O valor de data/hora de novo.  
  
### <a name="return-value"></a>Valor de retorno  
 A atualização `CTime` objeto.  
  
### <a name="remarks"></a>Comentários  
 Este operador sobrecarregado atribuição copia a fonte de tempo a esta `CTime` objeto. O armazenamento de horário interno em um `CTime` objeto é independente do fuso horário. Conversão de fuso horário não é necessário durante a atribuição.  
  
##  <a name="operator_add_-"></a>CTime::operator +, -  
 Esses operadores de adição e subtração `CTimeSpan` e `CTime` objetos.  
  
```  
CTime operator+(CTimeSpan timeSpan) const throw(); 
CTime operator-(CTimeSpan timeSpan) const throw(); 
CTimeSpan operator-(CTime time) const throw(); 
```  
  
### <a name="parameters"></a>Parâmetros  
 *período de tempo*  
 O `CTimeSpan` objeto a ser adicionado ou subtraído.  
  
 `time`  
 O `CTime` objeto a ser subtraído.  
  
### <a name="return-value"></a>Valor de retorno  
 Um `CTime` ou `CTimeSpan` objeto que representa o resultado da operação.  
  
### <a name="remarks"></a>Comentários  
 `CTime`objetos representam tempo absoluto, `CTimeSpan` representar tempo relativo. Os dois primeiros operadores permitem adicionar e subtrair `CTimeSpan` objetos para e de `CTime` objetos. O terceiro operador permite que você subtrair um `CTime` objeto de outro para produzir um `CTimeSpan` objeto.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #159](../../atl-mfc-shared/codesnippet/cpp/ctime-class_13.cpp)]  
  
##  <a name="operator_add_eq_-_eq"></a>+ = De CTime::operator-=  
 Esses operadores adicionar e subtrair um `CTimeSpan` objeto neste `CTime` objeto.  
  
```  
CTime& operator+=(CTimeSpan span) throw();
CTime& operator-=(CTimeSpan span) throw();
```  
  
### <a name="parameters"></a>Parâmetros  
 `span`  
 O `CTimeSpan` objeto a ser adicionado ou subtraído.  
  
### <a name="return-value"></a>Valor de retorno  
 A atualização `CTime` objeto.  
  
### <a name="remarks"></a>Comentários  
 Esses operadores permitem adicionar e subtrair um `CTimeSpan` objeto neste `CTime` objeto.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATLMFC_Utilities #160](../../atl-mfc-shared/codesnippet/cpp/ctime-class_14.cpp)]  
  
##  <a name="serialize64"></a>CTime::Serialize64  
  
> [!NOTE]
>  Este método só está disponível nos projetos MFC.  
  
 Serializa os dados associados com a variável de membro para ou de um arquivo morto.  
  
```  
CArchive& Serialize64(CArchive& ar);
```  
  
### <a name="parameters"></a>Parâmetros  
 `ar`  
 O `CArchive` objeto que você deseja atualizar.  
  
### <a name="return-value"></a>Valor de retorno  
 A atualização `CArchive` objeto.  
  
## <a name="see-also"></a>Consulte também  
 [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ftime_s _ftime32_s, _ftime64_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)   
 [gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [Classe CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Gráfico de hierarquia](../../mfc/hierarchy-chart.md)   
 [Classes compartilhadas do ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)


