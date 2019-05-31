---
title: IEnumDebugObjects::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::GetCount
helpviewer_keywords:
- IEnumDebugObjects::GetCount method
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 044aa63e10db74407754392299038623fd167631
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339612"
---
# <a name="ienumdebugobjectsgetcount"></a>IEnumDebugObjects::GetCount
Cette méthode retourne le nombre d’éléments dans l’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Paramètres
`pcelt`\
[out] Retourne le nombre d’éléments dans l’énumération.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode ne fait pas partie de l’interface d’énumération COM habituel qui spécifie qu’uniquement suivant Clone, Skip et réinitialisation doivent être implémentées.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)