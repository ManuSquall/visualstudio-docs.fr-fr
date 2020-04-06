---
title: Mise en œuvre et enregistrement d’un fournisseur de port Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efa9cdd8740648b66fe7190177b5fe769c4b2539
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738534"
---
# <a name="implement-and-register-a-port-supplier"></a>Mettre en œuvre et enregistrer un fournisseur portuaire
Le rôle d’un fournisseur portuaire est de suivre et d’approvisionner les ports, qui à leur tour gèrent les processus. Lorsqu’un port doit être créé, le fournisseur du port est instantané à l’aide de CoCreate avec le GUID du fournisseur du port (le gestionnaire de débociation de session [SDM] utilisera le fournisseur portuaire que l’utilisateur a choisi ou le fournisseur portuaire spécifié par le système de projet). Le SDM appelle ensuite [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) pour voir si des ports peuvent être ajoutés. Si un port peut être ajouté, un nouveau port est demandé en appelant [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) et en le passant un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) qui décrit le port. `AddPort`retourne un nouveau port représenté par une interface [IDebugPort2.](../../extensibility/debugger/reference/idebugport2.md)

## <a name="discussion"></a>Discussions
 Un port est créé par un fournisseur de port, qui est associé à une machine ou un serveur de débogé. Un serveur énumère ses fournisseurs portuaires par la méthode[EnumPortSuppliers,](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) et un fournisseur portuaire énumère ses ports par la méthode [EnumPorts.](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)

 En plus de l’enregistrement TYPIQUE de COM, un fournisseur de port doit s’inscrire auprès de Visual Studio en plaçant son CLSID et son nom dans des emplacements de registre spécifiques. Une fonction d’aide SDK `SetMetric` de Débogage appelée gère cette corvée : elle est appelée une fois pour chaque article à enregistrer, ainsi :

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 Un fournisseur de port se `RemoveMetric` débourse en appelant (une autre fonction d’aide SDK Debugging) une fois pour chaque article qui a été enregistré, ainsi:

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
> Les [aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` et `RemoveMetric` sont des fonctions statiques définies en *dbgmetric.h* et compilées dans *ad2de.lib*. Le `metrictypePortSupplier` `metricCLSID`, `metricName` , et les aides sont également définis en *dbgmetric.h*.

 Un fournisseur de port peut fournir son nom et GUID grâce aux méthodes [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) et [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivement.

## <a name="see-also"></a>Voir aussi
- [Mettre en œuvre un fournisseur portuaire](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Fournisseurs portuaires](../../extensibility/debugger/port-suppliers.md)
