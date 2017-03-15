---
title: "IDebugDynamicField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDynamicField"
helpviewer_keywords: 
  - "Interface de IDebugDynamicField"
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDynamicField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente un type d'une variable.  
  
## Syntaxe  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface est implémentée par les fournisseurs de symbole comme classe de base pour tout type qui peut être déterminée au moment de l'exécution.  C'est pour le code managé uniquement.  
  
## Remarques pour les appelants  
 Cette interface représente une classe de base dont plus spécialisé des interfaces peut être dérivé.  
  
## méthodes en commande de Vtable  
 Cette interface ne fournit pas de méthodes autres que celles héritées d' `IDebugField`.  
  
## Configuration requise  
 en\-tête : sh.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)