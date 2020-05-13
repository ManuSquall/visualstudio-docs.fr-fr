---
title: IDebugCodeContext2::GetLanguageInfo ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 465cc07b3ca75835afe0737fb22ba403acc4098b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734245"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Obtient les informations linguistiques pour ce contexte de code.

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
[dans, dehors] Retourne une chaîne qui contient le nom de la langue, comme « C ».

`pguidLanguage`\
[dans, dehors] Retourne le GUID pour la langue du `guidCPPLang`contexte du code, par exemple, .

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Au moins un des paramètres doit retourner une valeur non nulle.

## <a name="see-also"></a>Voir aussi
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
