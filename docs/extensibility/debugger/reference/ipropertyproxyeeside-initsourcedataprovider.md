---
description: Initialise les données sources pour cet objet et retourne un objet contenant les données initiales.
title: 'IPropertyProxyEESide :: InitSourceDataProvider | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ed8a686b2796070d0d4116bd4af66237a217346b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082437"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Initialise les données sources pour cet objet et retourne un objet contenant les données initiales.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Paramètres
`dataOut`\
à Retourne un objet [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode effectue tout ce qui est nécessaire pour initialiser un objet afin qu’il puisse retourner une interface [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) sur les données de l’objet. Cela permet l’affichage des données de l’objet et, si elles sont autorisées, modifiées par un visualiseur de type.

## <a name="see-also"></a>Voir aussi
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
