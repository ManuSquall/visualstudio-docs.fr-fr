---
title: "IDebugPortNotify2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortNotify2"
helpviewer_keywords: 
  - "Interface de IDebugPortNotify2"
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface enregistre ou annule l'inscription d'un programme qui peut être débogué avec le port qu'elle s'exécute.  
  
## Syntaxe  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Un fournisseur de port implémente cette interface pour prendre en charge l'ajout et des programmes de supprimer du port.  Il est généralement implémenté sur le même objet qui implémente l'interface d' [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) .  
  
## Remarques pour les appelants  
 Un appel à [QueryInterface](/visual-cpp/atl/queryinterface) sur l'interface d' `IDebugPort2` retourne cette interface.  En outre, un appel à [GetPortNotify](../Topic/IDebugDefaultPort2::GetPortNotify.md) retourne cette interface.  Un moteur de débogage peut consulter cette interface en tant que paramètre à [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugPortNotify2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Enregistre un programme qui peut être débogué avec le port qu'elle s'exécute.|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Annule l'inscription d'un programme qui peut être mis au point du port qu'elle s'exécute.|  
  
## Notes  
 À moins qu'un port de débogage a un moyen de savoir avec des programmes sont chargés ou déchargés, un fournisseur de port doit implémenter cette interface.  Tous les programmes qui sont chargés pour déboguer via un port particulier sont suivis à l'aide de cette interface.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)