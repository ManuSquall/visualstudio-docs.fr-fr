---
title: IEnumDebugCodeContexts2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::GetCount
helpviewer_keywords:
- IEnumDebugCodeContexts2::GetCount
ms.assetid: 74c52fcf-688c-40df-9acd-29b3b84e6216
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9cf2aef80f833961b9af13da4fa9f9b97e43435
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681060"
---
# <a name="ienumdebugcodecontexts2getcount"></a>IEnumDebugCodeContexts2::GetCount
Retourne le nombre d’éléments dans l’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

#### <a name="parameters"></a>Paramètres
 `pcelt`

 [out] Retourne le nombre d’éléments dans l’énumération.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode ne fait pas partie de l’interface d’énumération COM habituel qui spécifie que seules les `Next`, `Clone`, `Skip`, et `Reset` méthodes doivent être implémentées.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)