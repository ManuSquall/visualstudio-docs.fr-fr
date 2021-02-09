---
title: 'IEnumDebugCustomAttributes :: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::GetCount
helpviewer_keywords:
- IEnumDebugCustomAttributes::GetCount
ms.assetid: fafe826f-4ebf-4572-b2a3-d5dd2916c12f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1323af9d9d673e3d452882adff95b74213d7ad57
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929274"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode ne fait pas partie de l’interface d’énumération com personnalisée qui spécifie que seuls, `Next` `Clone` , `Skip` et `Reset` doivent être implémentés.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
