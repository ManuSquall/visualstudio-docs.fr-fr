---
description: Retourne le nombre d’éléments DEBUG_PROPERTY_INFO dans l’énumération.
title: 'IEnumDebugPropertyInfo2 :: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::GetCount
helpviewer_keywords:
- IEnumDebugPropertyInfo2::GetCount
ms.assetid: 9b0b3ce6-08cb-46fd-a6d9-92b36e60da19
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e841d1a7057f788c59832daaca7f74a838f2bd06
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102224250"
---
# <a name="ienumdebugpropertyinfo2getcount"></a>IEnumDebugPropertyInfo2::GetCount
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

## <a name="parameters"></a>Paramètres
`pcelt`\
à Retourne le nombre d’éléments dans l’énumération.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode ne fait pas partie de l’interface d’énumération com personnalisée qui spécifie que seules les `Next` `Clone` méthodes,, `Skip` et `Reset` doivent être implémentées.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
