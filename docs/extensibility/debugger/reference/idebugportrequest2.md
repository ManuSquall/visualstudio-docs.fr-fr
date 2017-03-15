---
title: "IDebugPortRequest2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortRequest2"
helpviewer_keywords: 
  - "Interface de IDebugPortRequest2"
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface décrit un port.  cette description est utilisée pour ajouter le port à un fournisseur de port.  
  
## Syntaxe  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Visual Studio implémente généralement cette interface en cours d'un port de débogage d'un fournisseur de port.  
  
## Remarques pour les appelants  
 Cette interface est passée à [Ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) pour créer un port de débogage.  Un appel à [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) retourne cette interface, qui représente la requête utilisée pour créer le port en premier.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugPortRequest2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Obtient le nom du port de sa création.|  
  
## Notes  
 Un moteur de débogage en général n'interagissent pas avec un fournisseur de port et ne présente aucune utilisation de l'interface.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)