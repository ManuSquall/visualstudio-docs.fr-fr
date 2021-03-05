---
description: Obtient le langage associé à ce frame de pile.
title: 'IDebugStackFrame2 :: GetLanguageInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetLanguageInfo
helpviewer_keywords:
- IDebugStackFrame2::GetLanguageInfo
ms.assetid: 0e12fd92-f155-46a7-8272-cda279388cfb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 38d9cfcab6748aad2166bfddfb48e9a0c0dc90c0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159820"
---
# <a name="idebugstackframe2getlanguageinfo"></a>IDebugStackFrame2::GetLanguageInfo

Obtient le langage associé à ce frame de pile.

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
à Retourne le nom du langage qui implémente la méthode associée à ce frame de pile.

`pguidLanguage`\
à Retourne le `GUID` de la langue. Pour les [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] langages, par exemple, les éléments suivants peuvent être retournés :

- `guidVBScriptLang`\

- `guidJScriptLang`\

- `guidCPPLang`\

- `guidVBLang`\

- `guidSQLLang`\

- `guidScriptLang`\

## <a name="return-value"></a>Valeur renvoyée

 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi

- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
