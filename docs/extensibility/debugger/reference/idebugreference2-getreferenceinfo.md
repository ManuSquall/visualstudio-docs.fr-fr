---
description: Obtient la structure DEBUG_REFERENCE_INFO qui décrit une référence.
title: 'IDebugReference2 :: GetReferenceInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01a36cbf7d1ca9ec56d7785c06d16e0071abc177
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087221"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Obtient la structure [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) qui décrit une référence. Réservé pour un usage futur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetReferenceInfo ( 
   DEBUGREF_INFO_FLAGS   dwFields,
   DWORD                 nRadix,
   DWORD                 dwTimeout,
   IDebugReference2**    rgpArgs,
   DWORD                 dwArgCount,
   DEBUG_REFERENCE_INFO* pReferenceInfo
);
```

```csharp
int GetReferenceInfo ( 
   enum_DEBUGREF_INFO_FLAGS  dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_REFERENCE_INFO[]    pReferenceInfo
);
```

## <a name="parameters"></a>Paramètres
`dwFields`\
dans Combinaison d’indicateurs de l’énumération [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) qui déterminent les champs à remplir dans la structure [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .

`nRadix`\
dans Base à utiliser pour mettre en forme les informations numériques.

`dwTimeout`\
dans Durée d’attente maximale, en millisecondes, avant le retour de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.

`rgpArgs`\
dans Tableau d’objets [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) . Réservé à une utilisation ultérieure ; défini sur une valeur null.

`dwArgCount`\
dans Nombre d’arguments de référence dans le `rgpArgs` tableau. Réservé à une utilisation ultérieure ; défini sur 0.

`pReferenceInfo`\
à Structure [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) qui est remplie avec une description de la propriété.

## <a name="return-value"></a>Valeur renvoyée
 Retourne toujours `E_NOTIMPL`.

## <a name="see-also"></a>Voir aussi
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
