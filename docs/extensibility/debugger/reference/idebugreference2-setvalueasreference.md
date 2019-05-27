---
title: IDebugReference2::SetValueAsReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 203e9741afa832ba0515a06b21ba1899e1355e1c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66211873"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Définit la valeur d’une référence à partir d’une autre référence. Réservé à un usage ultérieur.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Paramètres
`rgpArgs`\
[in] Un tableau de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objets utilisés pour déterminer comment définir la valeur de référence.

`dwArgCount`\
[in] Le nombre de références dans le tableau.

`pValue`\
[in] Un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objet à partir duquel définir la valeur de propriété.

`dwTimeout`\
[in] Durée maximale, en millisecondes, à attendre avant de retourner à partir de cette méthode. Utilisez `INFINITE` pour attendre indéfiniment.

## <a name="return-value"></a>Valeur de retour
 Retourne toujours `E_NOTIMPL`.

## <a name="see-also"></a>Voir aussi
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)