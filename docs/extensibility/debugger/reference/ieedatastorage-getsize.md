---
description: Retourne le nombre d’octets contenus dans cet objet.
title: 'IEEDataStorage :: obtient | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46051ae73859213b3206e27fb83d40c0561d0c0b
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222924"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Retourne le nombre d’octets contenus dans cet objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize(
   ULONG* size
);
```

```csharp
int GetSize(
   out uint size
);
```

## <a name="parameters"></a>Paramètres
`size`\
à Nombre d’octets contenus dans cet objet.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Utilisez la méthode [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) pour récupérer les octets de données réels.

## <a name="see-also"></a>Voir aussi
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
