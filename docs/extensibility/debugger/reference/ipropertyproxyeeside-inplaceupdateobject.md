---
title: IPropertyProxyEESide::InPlaceUpdateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a083b3d2eeb05a07837b826b5cb35ccedb0c1722
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66198721"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
Met à jour des données de l’objet avec l’objet de données spécifié et retourne un nouvel objet de données représentant les nouvelles données de l’objet.

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
[in] Un [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objet contenant les nouvelles données.

`dataOut`\
[out] Retourne un nouvel `IEEDataStorage` objet contenant les données remplacées.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode met à jour les données de l’objet. Les données dans la liste retournée [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) objet n’a pas besoin être le même que les données d’entrant `IEEDataStorage` objet, mais l’objet retourné doit refléter la valeur actuelle de la propriété.

 L’objet de données entrantes n’est pas généralement implémentée par le EE. Toutefois, l’objet retourné par cette méthode est toujours implémentée par EE, ce qui vous permet de l’implémenter EE la `IEEDataStorage` interface sur toute classe est souhaitée.

 Le [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) méthode crée un objet de données basé sur l’objet de données entrantes mais n’affecte pas les données d’origine de la propriété.

## <a name="see-also"></a>Voir aussi
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)