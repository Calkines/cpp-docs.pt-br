---
title: Funções de caminho da ATL
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, path
f1_keywords:
- ATLPATH/ATL::ATLPath::AddBackslash
- ATLPATH/ATL::ATLPath::AddExtension
- ATLPATH/ATL::ATLPath::Append
- ATLPATH/ATL::ATLPath::BuildRoot
- ATLPATH/ATL::ATLPath::Canonicalize
- ATLPATH/ATL::ATLPath::Combine
- ATLPATH/ATL::ATLPath::CommonPrefix
- ATLPATH/ATL::ATLPath::CompactPath
- ATLPATH/ATL::ATLPath::CompactPathEx
- ATLPATH/ATL::ATLPath::FileExists
- ATLPATH/ATL::ATLPath::FindExtension
- ATLPATH/ATL::ATLPath::FindFileName
- ATLPATH/ATL::ATLPath::GetDriveNumber
- ATLPATH/ATL::ATLPath::IsDirectory
- ATLPATH/ATL::ATLPath::IsFileSpec
- ATLPATH/ATL::ATLPath::IsPrefix
- ATLPATH/ATL::ATLPath::IsRelative
- ATLPATH/ATL::ATLPath::IsRoot
- ATLPATH/ATL::ATLPath::IsSameRoot
- ATLPATH/ATL::ATLPath::IsUNC
- ATLPATH/ATL::ATLPath::IsUNCServer
- ATLPATH/ATL::ATLPath::IsUNCServerShare
- ATLPATH/ATL::ATLPath::MakePretty
- ATLPATH/ATL::ATLPath::MatchSpec
- ATLPATH/ATL::ATLPath::QuoteSpaces
- ATLPATH/ATL::ATLPath::RelativePathTo
- ATLPATH/ATL::ATLPath::RemoveArgs
- ATLPATH/ATL::ATLPath::RemoveBackslash
- ATLPATH/ATL::ATLPath::RemoveBlanks
- ATLPATH/ATL::ATLPath::RemoveExtension
- ATLPATH/ATL::ATLPath::RemoveFileSpec
- ATLPATH/ATL::ATLPath::RenameExtension
- ATLPATH/ATL::ATLPath::SkipRoot
- ATLPATH/ATL::ATLPath::StripPath
- ATLPATH/ATL::ATLPath::StripToRoot
- ATLPATH/ATL::ATLPath::UnquoteSpaces
ms.assetid: d1ec2b8d-7ec7-43ea-90dd-0a740d2a742b
ms.openlocfilehash: 76efbb0bd43b800f186eac1afa168fc2a0c939f6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497982"
---
# <a name="atl-path-functions"></a>Funções de caminho da ATL

A ATL fornece a classe ATLPath para manipular caminhos na forma de [CPathT](cpatht-class.md). Esse código pode ser encontrado em atlpath. h.

### <a name="related-classes"></a>Classes relacionadas

|||
|-|-|
|[Classe CPathT](cpatht-class.md)|Essa classe representa um caminho.|

### <a name="related-typedefs"></a>TYPEDEFs relacionados

|||
|-|-|
|`CPath`|Uma especialização de [CPathT](cpatht-class.md) usando `CString`.|
|`CPathA`|Uma especialização de [CPathT](cpatht-class.md) usando `CStringA`.|
|`CPathW`|Uma especialização de [CPathT](cpatht-class.md) usando `CStringW`.|

### <a name="functions"></a>Funções

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|Essa função é um wrapper sobrecarregado para [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).|
|[ATLPath::AddExtension](#addextension)|Essa função é um wrapper sobrecarregado para [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).|
|[ATLPath::Append](#append)|Essa função é um wrapper sobrecarregado para [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).|
|[ATLPath::BuildRoot](#buildroot)|Essa função é um wrapper sobrecarregado para [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).|
|[ATLPath::Canonicalize](#canonicalize)|Essa função é um wrapper sobrecarregado para [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).|
|[ATLPath::Combine](#combine)|Essa função é um wrapper sobrecarregado para [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).|
|[ATLPath::CommonPrefix](#commonprefix)|Essa função é um wrapper sobrecarregado para [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).|
|[ATLPath::CompactPath](#compactpath)|Essa função é um wrapper sobrecarregado para [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).|
|[ATLPath::CompactPathEx](#compactpathex)|Essa função é um wrapper sobrecarregado para [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).|
|[ATLPath::FileExists](#fileexists)|Essa função é um wrapper sobrecarregado para [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).|
|[ATLPath::FindExtension](#findextension)|Essa função é um wrapper sobrecarregado para [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).|
|[ATLPath::FindFileName](#findfilename)|Essa função é um wrapper sobrecarregado para [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).|
|[ATLPath::GetDriveNumber](#getdrivenumber)|Essa função é um wrapper sobrecarregado para [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).|
|[ATLPath::IsDirectory](#isdirectory)|Essa função é um wrapper sobrecarregado para [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).|
|[ATLPath::IsFileSpec](#isfilespec)|Essa função é um wrapper sobrecarregado para [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).|
|[ATLPath::IsPrefix](#isprefix)|Essa função é um wrapper sobrecarregado para [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).|
|[ATLPath::IsRelative](#isrelative)|Essa função é um wrapper sobrecarregado para [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).|
|[ATLPath::IsRoot](#isroot)|Essa função é um wrapper sobrecarregado para [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).|
|[ATLPath::IsSameRoot](#issameroot)|Essa função é um wrapper sobrecarregado para [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).|
|[ATLPath::IsUNC](#isunc)|Essa função é um wrapper sobrecarregado para [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).|
|[ATLPath::IsUNCServer](#isuncserver)|Essa função é um wrapper sobrecarregado para [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).|
|[ATLPath::IsUNCServerShare](#isuncservershare)|Essa função é um wrapper sobrecarregado para [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).|
|[ATLPath::MakePretty](#makepretty)|Essa função é um wrapper sobrecarregado para [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).|
|[ATLPath::MatchSpec](#matchspec)|Essa função é um wrapper sobrecarregado para [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).|
|[ATLPath::QuoteSpaces](#quotespaces)|Essa função é um wrapper sobrecarregado para [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).|
|[ATLPath::RelativePathTo](#relativepathto)|Essa função é um wrapper sobrecarregado para [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).|
|[ATLPath::RemoveArgs](#removeargs)|Essa função é um wrapper sobrecarregado para [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).|
|[ATLPath::RemoveBackslash](#removebackslash)|Essa função é um wrapper sobrecarregado para [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).|
|[ATLPath::RemoveBlanks](#removeblanks)|Essa função é um wrapper sobrecarregado para [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).|
|[ATLPath::RemoveExtension](#removeextension)|Essa função é um wrapper sobrecarregado para [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).|
|[ATLPath::RemoveFileSpec](#removefilespec)|Essa função é um wrapper sobrecarregado para [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).|
|[ATLPath::RenameExtension](#renameextension)|Essa função é um wrapper sobrecarregado para [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).|
|[ATLPath::SkipRoot](#skiproot)|Essa função é um wrapper sobrecarregado para [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).|
|[ATLPath::StripPath](#strippath)|Essa função é um wrapper sobrecarregado para [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).|
|[ATLPath::StripToRoot](#striptoroot)|Essa função é um wrapper sobrecarregado para [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).|
|[ATLPath::UnquoteSpaces](#unquotespaces)|Essa função é um wrapper sobrecarregado para [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlpath. h

## <a name="addbackslash"></a> ATLPath::AddBackSlash

Essa função é um wrapper sobrecarregado para [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

### <a name="syntax"></a>Sintaxe

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw) para obter detalhes.

## <a name="addextension"></a> ATLPath::AddExtension

Essa função é um wrapper sobrecarregado para [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Comentários

Consulte [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw) para obter detalhes.

## <a name="append"></a>ATLPath:: Append

Essa função é um wrapper sobrecarregado para [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Comentários

Consulte [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw) para obter detalhes.

## <a name="buildroot"></a> ATLPath::BuildRoot

Essa função é um wrapper sobrecarregado para [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

### <a name="syntax"></a>Sintaxe

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Comentários

Consulte [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw) para obter detalhes.

## <a name="canonicalize"></a>ATLPath:: canonize

Essa função é um wrapper sobrecarregado para [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

### <a name="syntax"></a>Sintaxe

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Comentários

Consulte [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew) para obter detalhes.

## <a name="combine"></a>ATLPath:: Combine

Essa função é um wrapper sobrecarregado para [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

### <a name="syntax"></a>Sintaxe

```
inline char* Combine(
   char* pszDest,
   const char* pszDir,
   const char* pszFile
);

inline wchar_t* Combine(
   wchar_t* pszDest,
   const wchar_t* pszDir,
   const wchar_t* pszFile);
```

### <a name="remarks"></a>Comentários

Consulte PathCombine para obter detalhes.

## <a name="commonprefix"></a> ATLPath::CommonPrefix

Essa função é um wrapper sobrecarregado para [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

### <a name="syntax"></a>Sintaxe

```
inline int CommonPrefix(
   const char* pszFile1,
   const char* pszFile2,
   char* pszDest);

inline int CommonPrefix(
   const wchar_t* pszFile1,
   const wchar_t* pszFile2,
   wchar_t* pszDest);
```

### <a name="remarks"></a>Comentários

Consulte [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw) para obter detalhes.

## <a name="compactpath"></a> ATLPath::CompactPath

Essa função é um wrapper sobrecarregado para [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL CompactPath(
   HDC hDC,
   char* pszPath,
   UINT dx);

inline BOOL CompactPath(
   HDC hDC,
   wchar_t* pszPath,
   UINT dx);
```

### <a name="remarks"></a>Comentários

Consulte [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw) para obter detalhes.

## <a name="compactpathex"></a> ATLPath::CompactPathEx

Essa função é um wrapper sobrecarregado para [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL CompactPathEx(
   char* pszDest,
   const char* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);

inline BOOL CompactPathEx(
   wchar_t* pszDest,
   const wchar_t* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);
```

### <a name="remarks"></a>Comentários

Consulte [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw) para obter detalhes.

## <a name="fileexists"></a> ATLPath::FileExists

Essa função é um wrapper sobrecarregado para [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw) para obter detalhes.

## <a name="findextension"></a>ATLPath::FindExtension

Essa função é um wrapper sobrecarregado para [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

### <a name="syntax"></a>Sintaxe

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw) para obter detalhes.

## <a name="findfilename"></a> ATLPath::FindFileName

Essa função é um wrapper sobrecarregado para [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

### <a name="syntax"></a>Sintaxe

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) para obter detalhes.

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber

Essa função é um wrapper sobrecarregado para [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

### <a name="syntax"></a>Sintaxe

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw) para obter detalhes.

## <a name="isdirectory"></a>  ATLPath::IsDirectory

Essa função é um wrapper sobrecarregado para [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte PathIsDirectory para obter detalhes.

## <a name="isfilespec"></a> ATLPath::IsFileSpec

Essa função é um wrapper sobrecarregado para [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw) para obter detalhes.

## <a name="isprefix"></a> ATLPath::IsPrefix

Essa função é um wrapper sobrecarregado para [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw) para obter detalhes.

## <a name="isrelative"></a> ATLPath::IsRelative

Essa função é um wrapper sobrecarregado para [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

### <a name="syntax"></a>Sintaxe

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew) para obter detalhes.

## <a name="isroot"></a> ATLPath::IsRoot

Essa função é um wrapper sobrecarregado para [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw) para obter detalhes.

## <a name="issameroot"></a> ATLPath::IsSameRoot

Essa função é um wrapper sobrecarregado para [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Comentários

Consulte [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw) para obter detalhes.

## <a name="isunc"></a> ATLPath::IsUNC

Essa função é um wrapper sobrecarregado para [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw) para obter detalhes.

## <a name="isuncserver"></a> ATLPath::IsUNCServer

Essa função é um wrapper sobrecarregado para [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw) para obter detalhes.

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare

Essa função é um wrapper sobrecarregado para [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

### <a name="syntax"></a>Sintaxe

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew) para obter detalhes.

## <a name="makepretty"></a> ATLPath::MakePretty

Essa função é um wrapper sobrecarregado para [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw) para obter detalhes.

## <a name="matchspec"></a> ATLPath::MatchSpec

Essa função é um wrapper sobrecarregado para [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Comentários

Consulte [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw) para obter detalhes.

## <a name="quotespaces"></a> ATLPath::QuoteSpaces

Essa função é um wrapper sobrecarregado para [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

### <a name="syntax"></a>Sintaxe

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw) para obter detalhes.

## <a name="relativepathto"></a> ATLPath::RelativePathTo

Essa função é um wrapper sobrecarregado para [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

### <a name="syntax"></a>Sintaxe

```
inline BOOL RelativePathTo(
   char* pszPath,
   const char* pszFrom,
   DWORD dwAttrFrom,
   const char* pszTo,
   DWORD dwAttrTo);

inline BOOL RelativePathTo(
   wchar_t* pszPath,
   const wchar_t* pszFrom,
   DWORD dwAttrFrom,
   const wchar_t* pszTo,
   DWORD dwAttrTo);
```

### <a name="remarks"></a>Comentários

Consulte [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow) para obter detalhes.

## <a name="removeargs"></a> ATLPath::RemoveArgs

Essa função é um wrapper sobrecarregado para [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

### <a name="syntax"></a>Sintaxe

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw) para obter detalhes.

## <a name="removebackslash"></a>ATLPath::RemoveBackslash

Essa função é um wrapper sobrecarregado para [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

### <a name="syntax"></a>Sintaxe

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw) para obter detalhes.

## <a name="removeblanks"></a> ATLPath::RemoveBlanks

Essa função é um wrapper sobrecarregado para [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

### <a name="syntax"></a>Sintaxe

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw) para obter detalhes.

## <a name="removeextension"></a>ATLPath::RemoveExtension

Essa função é um wrapper sobrecarregado para [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

### <a name="syntax"></a>Sintaxe

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw) para obter detalhes.

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec

Essa função é um wrapper sobrecarregado para [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw) para obter detalhes.

## <a name="renameextension"></a> ATLPath::RenameExtension

Essa função é um wrapper sobrecarregado para [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Comentários

Consulte [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw) para obter detalhes.

## <a name="skiproot"></a> ATLPath::SkipRoot

Essa função é um wrapper sobrecarregado para [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

### <a name="syntax"></a>Sintaxe

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw) para obter detalhes.

## <a name="strippath"></a> ATLPath::StripPath

Essa função é um wrapper sobrecarregado para [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

### <a name="syntax"></a>Sintaxe

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw) para obter detalhes.

## <a name="striptoroot"></a> ATLPath::StripToRoot

Essa função é um wrapper sobrecarregado para [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

### <a name="syntax"></a>Sintaxe

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw) para obter detalhes.

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces

Essa função é um wrapper sobrecarregado para [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

### <a name="syntax"></a>Sintaxe

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Comentários

Consulte [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw) para obter detalhes.
