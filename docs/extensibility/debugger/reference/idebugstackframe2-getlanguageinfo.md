---
title: IDebugStackFrame2::GetLanguageInfo ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cefb4bdd9d0c85311c63e6a988956301a6c2cc14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719705"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo

Obtient la langue associée à ce cadre de pile.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetLanguageInfo ( 
   BSTR* pbstrLanguage,
   GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo ( 
   ref string pbstrLanguage,
   ref Guid   pguidLanguage
);
```

## <a name="parameters"></a>Paramètres

`pbstrLanguage`\
[out] Retourne le nom de la langue qui implémente la méthode associée à ce cadre de pile.

`pguidLanguage`\
[out] Retourne `GUID` la langue. Pour [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] les langues, par exemple, ce qui suit peut être retourné :

- `guidVBScriptLang`\

- `guidJScriptLang`\

- `guidCPPLang`\

- `guidVBLang`\

- `guidSQLLang`\

- `guidScriptLang`\

## <a name="return-value"></a>Valeur de retour

 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi

- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
