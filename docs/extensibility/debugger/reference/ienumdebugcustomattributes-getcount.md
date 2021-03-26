---
description: Obtient le nombre d’attributs personnalisés dans un énumérateur.
title: 'IEnumDebugCustomAttributes :: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::GetCount
helpviewer_keywords:
- IEnumDebugCustomAttributes::GetCount
ms.assetid: fafe826f-4ebf-4572-b2a3-d5dd2916c12f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4d0d61565d57b7e025d67689420dcbf82c93707a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083113"
---
# <a name="ienumdebugcustomattributesgetcount"></a>IEnumDebugCustomAttributes::GetCount
Obtient le nombre d’attributs personnalisés dans un énumérateur.

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
 Cette méthode ne fait pas partie de l’interface d’énumération com personnalisée qui spécifie que seuls, `Next` `Clone` , `Skip` et `Reset` doivent être implémentés.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
