---
title: "IDebugSourceServerModule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugSourceServerModule"
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSourceServerModule
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Représente les informations du serveur source contenues dans un fichier PDB.  
  
## Syntaxe  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface est implémentée par les moteurs de débogage et consommée par le débogueur interface utilisateur.  
  
## Méthodes  
 Le tableau suivant répertorie les méthodes d' `IDebugSourceServerModule`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Récupère un tableau des informations du serveur source.|  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll