---
title: IPropertyProxyEESide::CreateReplacementObject (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f449a505c56c180f1bab021007f1b635a2461996
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715038"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Crée une copie d’un objet de données spécifique à l’évaluateur d’expression (EE).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Paramètres
`dataIn`\
[dans] Un objet [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenant les données à copier.

`dataOut`\
[out] Retourne un nouvel objet `IEEDataStorage`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est donnée un objet [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) représentant un tableau d’octets. Cet objet de données entrants n’est généralement pas implémenté par l’EE. Cependant, l’objet retourné par cette méthode est toujours implémenté `IEEDataStorage` par l’EE, qui permet à l’EE d’implémenter l’interface sur n’importe quelle classe désirée.

 Notez que les données `IEEDataStorage` fournies par l’objet `IEEDataStorage` entrant doivent être les mêmes données dans l’objet sortant.

## <a name="see-also"></a>Voir aussi
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
