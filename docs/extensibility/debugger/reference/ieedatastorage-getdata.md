---
title: IEEDataStorage::GetData ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 62a1295aeb2a6afad51dee0f1015e3ab01d13fbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718209"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Récupère le nombre spécifié d’octets de l’objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>Paramètres
`dataSize`\
[dans] Le nombre d’octets `data` à récupérer (le tableau doit contenir au moins ce nombre d’octets).

`sizeGotten`\
[out] Retourne le nombre d’octets effectivement récupérés.

`data`\
[dans, dehors] Array à remplir avec les données demandées.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’utilisation recommandée de cette méthode est de récupérer tous les octets de données dans un tableau local, car il n’y a aucun moyen de sauter sur les octets dans le processus de récupération. Dans ce cas, `dataSize` le paramètre doit être la valeur retournée par la méthode [GetSize.](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

## <a name="see-also"></a>Voir aussi
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
