---
description: Met à jour les données de l’objet avec l’objet de données spécifié et retourne un nouvel objet de données représentant les nouvelles données de l’objet.
title: 'IPropertyProxyEESide :: InPlaceUpdateObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6fb6c098d26148db39493b25f199c6819fb81d27
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082411"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Met à jour les données de l’objet avec l’objet de données spécifié et retourne un nouvel objet de données représentant les nouvelles données de l’objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT InPlaceUpdateObject(
   [in] IEEDataStorage*   dataIn,
   [out] IEEDataStorage** dataOut
);
```

```csharp
int InPlaceUpdateObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Paramètres
`dataIn`\
dans Objet [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenant les nouvelles données.

`dataOut`\
à Retourne un nouvel `IEEDataStorage` objet contenant les données remplacées.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode met à jour les données de l’objet. Les données de l’objet [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) retourné n’ont pas besoin d’être identiques à celles de l’objet entrant `IEEDataStorage` , mais l’objet retourné doit refléter la valeur actuelle de la propriété.

 L’objet de données entrant n’est généralement pas implémenté par EE. Toutefois, l’objet retourné par cette méthode est toujours implémenté par EE, qui permet à EE d’implémenter l' `IEEDataStorage` interface sur la classe souhaitée.

 La méthode [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) crée un objet de données basé sur l’objet de données entrant, mais n’affecte pas les données d’origine de la propriété.

## <a name="see-also"></a>Voir aussi
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
