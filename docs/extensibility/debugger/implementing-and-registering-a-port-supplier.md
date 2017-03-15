---
title: "L&#39;impl&#233;mentation et l&#39;inscription d&#39;un fournisseur de Port | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (débogage SDK), l'enregistrement des fournisseurs de port"
  - "fournisseurs de port, l'inscription"
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# L&#39;impl&#233;mentation et l&#39;inscription d&#39;un fournisseur de Port
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le rôle d'un fournisseur de port a des orifices suivre et de puissance, qui gèrent ensuite des processus.  Ensuite un port doit être créé, le fournisseur de port est instancié à l'aide de CoCreate avec un GUID du fournisseur de port \(la session que le gestionnaire de débogage \[SDM\] utilise le fournisseur de port l'utilisateur a sélectionné ou le fournisseur de port spécifié par le système de projet\).  Le SDM appelle ensuite [CanAddPort](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) pour voir si les ports peuvent être ajoutés.  Si un port peut être ajouté, un nouveau port est demandé en appelant [Ajouter un port](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) et en lui passant [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) qui décrit le port.  `AddPort` retourne un nouveau port représenté par une interface d' [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) .  
  
## Discussion  
 Un port est créé par un fournisseur de port, qui est ensuite associé à un ordinateur ou un serveur de débogage.  Un serveur peut énumérer ses fournisseurs de port via la méthode d'[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) , et un fournisseur de port peut énumérer ses ports via la méthode d' [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) .  
  
 En plus de l'inscription COM classique, un fournisseur de port doit s'inscrire dans Visual Studio en plaçant son CLSID et nom dans des emplacements de Registre spécifiques.  Un Kit de développement logiciel débogage `SetMetric` appelé par fonction d'assistance gère cette corvée : il est appelé une fois pour chaque élément enregistré, ceci :  
  
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
  
 Un fournisseur de port s'annule l'enregistrement en appelant `RemoveMetric` \(une autre fonction d'assistance de débogage du Kit de développement logiciel windows\) une fois pour chaque élément qui a été enregistré, ceci :  
  
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
>  [« Helpers » du Kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) `SetMetric` et `RemoveMetric` sont des fonctions static définies dans dbgmetric.h et compilées dans ad2de.lib.  `metrictypePortSupplier`, `metricCLSID`, et programmes d'assistance d'`metricName` sont également définies dans dbgmetric.h.  
  
 Un fournisseur de port peut fournir son nom et GUID via les méthodes [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) et [GetPortSupplierId](../Topic/IDebugPortSupplier2::GetPortSupplierId.md), respectivement.  
  
## Voir aussi  
 [L'implémentation d'un fournisseur de Port](../../extensibility/debugger/implementing-a-port-supplier.md)   
 [« Helpers » du Kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md)