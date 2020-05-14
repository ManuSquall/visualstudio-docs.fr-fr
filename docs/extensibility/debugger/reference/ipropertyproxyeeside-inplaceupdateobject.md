---
title: IPropertyProxyEESide::InPlaceUpdateObject (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79167b0f7e8094fabf80bb9b2d83c94ac874aa31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714891"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Mise à jour des données de l’objet avec l’objet de données donnée et renvoie un nouvel objet de données représentant les nouvelles données de l’objet.

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
[dans] Un objet [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenant les nouvelles données.

`dataOut`\
[out] Renvoie `IEEDataStorage` un nouvel objet contenant les données remplacées.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode met à jour les données de l’objet. Les données de l’objet [IEEDataStorage retournés](../../../extensibility/debugger/reference/ieedatastorage.md) n’ont pas `IEEDataStorage` besoin d’être les mêmes que les données de l’objet entrant, mais l’objet retourné doit refléter la valeur actuelle de la propriété.

 L’objet de données entrants n’est généralement pas implémenté par l’EE. Cependant, l’objet retourné par cette méthode est toujours implémenté `IEEDataStorage` par l’EE, qui permet à l’EE d’implémenter l’interface sur n’importe quelle classe désirée.

 La méthode [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) crée un objet de données basé sur l’objet de données entrant mais n’affecte pas les données originales de la propriété.

## <a name="see-also"></a>Voir aussi
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
