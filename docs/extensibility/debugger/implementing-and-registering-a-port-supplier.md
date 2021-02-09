---
title: Implémentation et inscription d’un fournisseur de port | Microsoft Docs
description: Apprenez à implémenter et à inscrire un fournisseur de port, qui assure le suivi et fournit des ports qui gèrent les processus.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d5639c45fd6dff6702ebc197d46c2eafe482e1d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926365"
---
# <a name="implement-and-register-a-port-supplier"></a>Implémenter et inscrire un fournisseur de port
Le rôle d’un fournisseur de ports consiste à suivre et à fournir des ports qui, à leur tour, gèrent des processus. Lorsqu’un port doit être créé, le fournisseur de port est instancié à l’aide de CoCreate avec le GUID du fournisseur de port (le gestionnaire de débogage de session [SDM] utilise le fournisseur de port que l’utilisateur a sélectionné ou le fournisseur de port spécifié par le système de projet). Le SDM appelle ensuite [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) pour voir si des ports peuvent être ajoutés. Si un port peut être ajouté, un nouveau port est demandé en appelant [addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) et en lui transmettant un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) qui décrit le port. `AddPort` retourne un nouveau port représenté par une interface [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .

## <a name="discussion"></a>Discussions
 Un port est créé par un fournisseur de ports, qui est associé à un ordinateur ou à un serveur de débogage. Un serveur énumère ses fournisseurs de ports par le biais de la méthode[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) , et un fournisseur de port énumère ses ports par le biais de la méthode [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .

 En plus de l’inscription COM classique, un fournisseur de port doit s’inscrire auprès de Visual Studio en plaçant son CLSID et son nom dans des emplacements de Registre spécifiques. Une fonction d’assistance du kit de développement logiciel (SDK) de débogage appelée `SetMetric` gère cette corvée : elle est appelée une fois pour chaque élément à inscrire, donc :

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

 Un fournisseur de ports se désinscrit lui-même en appelant `RemoveMetric` (une autre fonction d’assistance du kit de développement logiciel (SDK) de débogage) une fois pour chaque élément qui a été enregistré, par conséquent :

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
> Les [applications auxiliaires du kit de développement logiciel (SDK) pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` et `RemoveMetric` sont des fonctions statiques définies dans *dbgmetric. h* et compilées dans *ad2de. lib*. Les `metrictypePortSupplier` `metricCLSID` `metricName` assistances, et sont également définies dans *dbgmetric. h*.

 Un fournisseur de ports peut fournir son nom et son GUID par le biais des méthodes [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) et [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivement.

## <a name="see-also"></a>Voir aussi
- [Implémenter un fournisseur de port](../../extensibility/debugger/implementing-a-port-supplier.md)
- [Applications auxiliaires du kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)
