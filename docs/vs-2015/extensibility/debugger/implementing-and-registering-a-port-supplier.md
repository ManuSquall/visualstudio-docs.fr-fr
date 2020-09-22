---
title: Implémentation et inscription d’un fournisseur de port | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377aa88df71fd0d3c42745fe2d3ce3b648191aa4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840045"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implémentation et inscription d’un fournisseur de ports
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le rôle d’un fournisseur de ports consiste à suivre et à fournir des ports qui, à leur tour, gèrent des processus. Au moment de la création d’un port, le fournisseur de port est instancié à l’aide de CoCreate avec le GUID du fournisseur de port (session Debug Manager [SDM] utilise le fournisseur de port que l’utilisateur a sélectionné ou le fournisseur de port spécifié par le système de projet). Le SDM appellera ensuite [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) pour voir si des ports peuvent être ajoutés. Si un port peut être ajouté, un nouveau port est demandé en appelant [addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) et en lui transmettant un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) qui décrit le port. `AddPort` retourne un nouveau port représenté par une interface [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .  
  
## <a name="discussion"></a>Discussion  
 Un port est créé par un fournisseur de port, qui est à son tour associé à un ordinateur ou à un serveur de débogage. Un serveur peut énumérer ses fournisseurs de ports par le biais de la méthode[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) , et un fournisseur de ports peut énumérer ses ports via la méthode [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .  
  
 En plus de l’inscription COM classique, un fournisseur de port doit s’inscrire auprès de Visual Studio en plaçant son CLSID et son nom dans des emplacements de Registre spécifiques. Une fonction d’assistance du kit de développement logiciel (SDK) de débogage appelée `SetMetric` gère cette corvée : elle est appelée une fois pour chaque élément à inscrire, donc :  
  
```cpp#  
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
  
```cpp#  
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
> Les [applications auxiliaires du kit de développement logiciel (SDK) pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` et `RemoveMetric` sont des fonctions statiques définies dans dbgmetric. h et compilées dans ad2de. lib. Les `metrictypePortSupplier` `metricCLSID` `metricName` assistances, et sont également définies dans dbgmetric. h.  
  
 Un fournisseur de ports peut fournir son nom et son GUID par le biais des méthodes [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) et [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivement.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un fournisseur de port](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Applications auxiliaires du kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Fournisseurs de ports](../../extensibility/debugger/port-suppliers.md)
