---
title: 'IPropertyProxyEESide :: CreateReplacementObject | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
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
dans Objet [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenant les données à copier.

`dataOut`\
[out] Retourne un nouvel objet `IEEDataStorage`.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode reçoit un objet [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) représentant un tableau d’octets. En général, cet objet de données entrant n’est pas implémenté par EE. Toutefois, l’objet retourné par cette méthode est toujours implémenté par EE, qui permet à EE d’implémenter l' `IEEDataStorage` interface sur la classe souhaitée.

 Notez que les données fournies par l' `IEEDataStorage` objet entrant doivent être identiques à celles de l' `IEEDataStorage` objet sortant.

## <a name="see-also"></a>Voir aussi
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
