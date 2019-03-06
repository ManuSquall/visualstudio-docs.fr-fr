---
title: IDebugCodeContext2::GetLanguageInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugCodeContext2::GetLanguageInfo
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4afcb2a8fd9de89b74fccec373e71e19264fe56
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712487"
---
# <a name="idebugcodecontext2getlanguageinfo"></a>IDebugCodeContext2::GetLanguageInfo
Obtient les informations de langue pour ce contexte de code.

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

#### <a name="parameters"></a>Paramètres
 `pbstrLanguage`

 [in, out] Retourne une chaîne qui contient le nom du langage, tels que « C++ ».

 `pguidLanguage`

 [in, out] Retourne le GUID pour le langage de contexte de code, par exemple, `guidCPPLang`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Au moins un des paramètres doit retourner une valeur non null.

## <a name="see-also"></a>Voir aussi
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)