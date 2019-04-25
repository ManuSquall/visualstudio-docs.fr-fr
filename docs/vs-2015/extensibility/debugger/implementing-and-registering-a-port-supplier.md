---
title: Implémentation et inscription d’un fournisseur de Port | Microsoft Docs
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
ms.openlocfilehash: 9d0546a357ce9d50b8e17e1543d12246d5fd5574
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953300"
---
# <a name="implementing-and-registering-a-port-supplier"></a>Implémentation et inscription d’un fournisseur de ports
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le rôle d’un fournisseur de port consiste à effectuer le suivi et fournir des ports, qui à son tour gérer les processus. Parallèlement à qu'un port doit être créé, le fournisseur de port est instancié à l’aide de CoCreate avec le GUID du fournisseur de port (le Gestionnaire de session de débogage [SDM] utilisez le fournisseur de port sélectionnée par l’utilisateur ou le fournisseur de port spécifié par le système de projet). Appelle ensuite le SDM [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) pour voir si tous les ports peuvent être ajoutés. Si un port peut être ajouté, un nouveau port est demandé en appelant [ajouter un port](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) et en lui passant un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) qui décrit le port. `AddPort` Retourne un nouveau port représenté par un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interface.  
  
## <a name="discussion"></a>Discussion  
 Un port est créé par un fournisseur de port, ce qui est à son tour associé à un serveur de l’ordinateur ou de débogage. Un serveur peut énumérer ses fournisseurs de port via le[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) (méthode) et un fournisseur de port peuvent énumérer ses ports via la [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) (méthode).  
  
 En plus de l’inscription de COM classique, un fournisseur de port doit s’inscrire dans Visual Studio en plaçant son CLSID et son nom dans des emplacements spécifiques du Registre. Une fonction d’assistance de débogage de SDK appelé `SetMetric` gère cette tâche : elle est appelée une fois pour chaque élément à être enregistré, par conséquent :  
  
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
  
 Un fournisseur de port annule l’inscription de lui-même en appelant `RemoveMetric` (une autre fonction d’assistance de kit de développement logiciel de débogage) une fois pour chaque élément qui a été inscrite, par conséquent :  
  
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
>  Le [aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` et `RemoveMetric` sont des fonctions statiques définies dans dbgmetric.h et compilés dans ad2de.lib. Le `metrictypePortSupplier`, `metricCLSID`, et `metricName` helpers sont également définis dans dbgmetric.h.  
  
 Un fournisseur de port peut fournir son nom et le GUID via les méthodes [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) et [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md), respectivement.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un fournisseur de Port](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [Aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Fournisseurs de ports](../../extensibility/debugger/port-suppliers.md)
