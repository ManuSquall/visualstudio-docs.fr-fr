---
description: Appelée par un gestionnaire d’événements pour récupérer les résultats relatifs à un processus de chargement de symboles.
title: 'IDebugSymbolSearchEvent2 :: GetSymbolSearchInfo, | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9f03562f3370268f720b2d8053bbd6a2979f6a19
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145766"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Appelée par un gestionnaire d’événements pour récupérer les résultats relatifs à un processus de chargement de symboles.

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
à Objet IDebugModule3 qui représente le module pour lequel les symboles ont été chargés.

`pbstrDebugMessage`\
[in, out] Retourne une chaîne contenant tous les messages d’erreur du module. S’il n’y a pas d’erreur, cette chaîne contient uniquement le nom du module, mais elle n’est jamais vide.

> [!NOTE]
> (C++) `pbstrDebugMessage` ne peut pas être `NULL` et doit être libéré avec `SysFreeString` .

`pdwModuleInfoFlags`\
à Combinaison d’indicateurs de l’énumération [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) indiquant si des symboles ont été chargés.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Lorsqu’un gestionnaire reçoit l’événement [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) après une tentative de chargement de symboles de débogage pour un module, le gestionnaire peut appeler thismethod pour déterminer les résultats de ce chargement.

## <a name="see-also"></a>Voir aussi
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
