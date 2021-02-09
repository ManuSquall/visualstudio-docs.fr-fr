---
title: 'IDebugCodeContext2 :: GetLanguageInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6719968d2e828340b16f84f3195f722803d8d9d8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928729"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Obtient les informations de langage pour ce contexte de code.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetLanguageInfo( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo( 
   ref string pbstrLanguage,
   ref Guid pguidLanguage
);
```

## <a name="parameters"></a>Paramètres
`pbstrLanguage`\
[in, out] Retourne une chaîne qui contient le nom du langage, tel que « C++ ».

`pguidLanguage`\
[in, out] Retourne le GUID de la langue du contexte de code, par exemple, `guidCPPLang` .

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Au moins un des paramètres doit retourner une valeur non null.

## <a name="see-also"></a>Voir aussi
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
