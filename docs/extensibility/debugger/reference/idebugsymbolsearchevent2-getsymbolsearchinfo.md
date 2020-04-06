---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: be498154a8141c61f114682893d0aaf8b841cf95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718888"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Appelé par un gestionnaire d’événements pour récupérer les résultats sur un processus de charge de symbole.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSymbolSearchInfo(
   IDebugModule3**    pModule,
   BSTR*              pbstrDebugMessage,
   MODULE_INFO_FLAGS* pdwModuleInfoFlags
);
```

```csharp
int GetSymbolSearchInfo(
   IDebugModule3              pModule,
   ref string                 pbstrDebugMessage,
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags
);
```

## <a name="parameters"></a>Paramètres
`pModule`\
[out] Un objet IDebugModule3 représentant le module pour lequel les symboles ont été chargés.

`pbstrDebugMessage`\
[dans, dehors] Renvoie une chaîne contenant tous les messages d’erreur du module. S’il n’y a pas d’erreur, alors cette chaîne contiendra simplement le nom du module, mais il n’est jamais vide.

> [!NOTE]
> [C] `pbstrDebugMessage` ne `NULL` peut pas être `SysFreeString`et doit être libéré avec .

`pdwModuleInfoFlags`\
[out] Une combinaison de drapeaux de [l’MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) énumération indiquant si des symboles ont été chargés.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; renvoie autrement un code d’erreur.

## <a name="remarks"></a>Notes
 Lorsqu’un gestionnaire reçoit [l’événement IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) après une tentative de chargement des symboles de débogage pour un module, le gestionnaire peut appeler thismethod pour déterminer les résultats de cette charge.

## <a name="see-also"></a>Voir aussi
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
