---
title: "Mise en œuvre et l’inscription d’un fournisseur de Port | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fa7378493c8df41b70be6fda17b2763f90fd7f04
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-and-registering-a-port-supplier"></a>Mise en œuvre et l’inscription d’un fournisseur de Port
Le rôle d’un fournisseur de port est d’effectuer le suivi et de fournir des ports, ce qui à leur tour gèrent les processus. À l’heure de qu'un port doit être créé, le fournisseur de port est instancié à l’aide de CoCreate avec le GUID du fournisseur de port (le Gestionnaire de session de débogage [SDM] utilise le fournisseur de port sélectionnée par l’utilisateur ou le fournisseur de port spécifié par le système de projet). Appelle ensuite le SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) pour voir si tous les ports peuvent être ajoutés. Si un port peut être ajouté, un nouveau port est demandé en appelant [ajouter un port](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) et en lui passant un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) qui décrit le port. `AddPort`Retourne un nouveau port représenté par une [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface.  
  
## <a name="discussion"></a>Discussion  
 Un port est créé par un fournisseur de port, qui est à son tour associé à un serveur de l’ordinateur ou de débogage. Un serveur peut énumérer ses fournisseurs de port via le[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) (méthode) et un fournisseur de port peuvent énumérer ses ports via la [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) (méthode).  
  
 En plus de l’inscription de COM classique, un fournisseur de port doit s’inscrire avec Visual Studio en plaçant son CLSID et son nom dans les emplacements de Registre spécifiques. Appel d’une fonction d’assistance de débogage Kit de développement logiciel `SetMetric` gère cette tâche : elle est appelée une fois pour chaque élément à inscrire, par conséquent :  
  
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
  
 Un fournisseur de port annule l’inscription de lui-même en appelant `RemoveMetric` (une autre fonction d’assistance de kit de développement logiciel de débogage) une fois pour chaque élément qui a été inscrit, par conséquent :  
  
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
>  Le [programmes d’assistance du Kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` et `RemoveMetric` sont des fonctions statiques définies dans dbgmetric.h et compilés dans ad2de.lib. Le `metrictypePortSupplier`, `metricCLSID`, et `metricName` applications auxiliaires sont également définies dans dbgmetric.h.  
  
 Un fournisseur de port peut fournir son nom et le GUID via les méthodes [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) et [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivement.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un fournisseur de Port](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Programmes d’assistance du Kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Fournisseurs de ports](../../extensibility/debugger/port-suppliers.md)