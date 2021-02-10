---
title: 'IEEDataStorage :: GetData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c0ff27438ad4a7d0106c1b452f55966dda3f7e07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965562"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Récupère le nombre d’octets spécifié à partir de l’objet.

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
dans Nombre d’octets à récupérer (le `data` tableau doit contenir au moins ce nombre d’octets).

`sizeGotten`\
à Retourne le nombre d’octets réellement récupérés.

`data`\
[in, out] Tableau à remplir avec les données demandées.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 L’utilisation recommandée de cette méthode consiste à récupérer tous les octets de données dans un tableau local, car il n’existe aucun moyen d’ignorer les octets dans le processus de récupération. Dans ce cas, le paramètre `dataSize` doit être la valeur retournée par [](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) la méthode de la méthode.

## <a name="see-also"></a>Voir aussi
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize,](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
