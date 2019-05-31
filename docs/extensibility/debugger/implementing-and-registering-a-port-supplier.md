---
title: Implémentation et inscription d’un fournisseur de Port | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26767193c4489405432054ee94beb195ce8448d7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344271"
---
# <a name="implement-and-register-a-port-supplier"></a>Implémenter et inscrire un fournisseur de port
Le rôle d’un fournisseur de port consiste à effectuer le suivi et fournir des ports, qui à son tour gérer les processus. Lorsqu’un port doit être créé, le fournisseur de port est instancié à l’aide de CoCreate avec le GUID du fournisseur de port (le Gestionnaire de session de débogage [SDM] utilisez le fournisseur de port sélectionnée par l’utilisateur ou le fournisseur de port spécifié par le système de projet). Le SDM appelle ensuite [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) pour voir si tous les ports peuvent être ajoutés. Si un port peut être ajouté, un nouveau port est demandé en appelant [ajouter un port](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) et en lui passant un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) qui décrit le port. `AddPort` Retourne un nouveau port représenté par un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface.

## <a name="discussion"></a>Discussion
 Un port est créé par un fournisseur de port qui est associé à un serveur de l’ordinateur ou de débogage. Un serveur énumère ses fournisseurs de port via le[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) (méthode) et un fournisseur de port énumère ses ports via la [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) (méthode).

 En plus de l’inscription de COM classique, un fournisseur de port doit s’inscrire dans Visual Studio en plaçant son CLSID et son nom dans des emplacements spécifiques du Registre. Une fonction d’assistance de débogage de SDK appelé `SetMetric` gère cette tâche : elle est appelée une fois pour chaque élément à être enregistré, par conséquent :

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

 Un fournisseur de port annule l’inscription de lui-même en appelant `RemoveMetric` (une autre fonction d’assistance de kit de développement logiciel de débogage) une fois pour chaque élément qui a été inscrite, par conséquent :

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
> Le [aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` et `RemoveMetric` sont des fonctions statiques définies dans *dbgmetric.h* et est compilé en *ad2de.lib*. Le `metrictypePortSupplier`, `metricCLSID`, et `metricName` helpers sont également définies dans *dbgmetric.h*.

 Un fournisseur de port peut fournir son nom et le GUID via les méthodes [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) et [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivement.

## <a name="see-also"></a>Voir aussi
- [Implémenter un fournisseur de port](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)