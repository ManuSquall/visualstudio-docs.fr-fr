---
title: "IDebugNoSymbolsEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interface de IDebugNoSymbolsEvent2"
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugNoSymbolsEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Signale le débogueur interface utilisateur de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] pour avertir l'utilisateur pour lequel des symboles ne peuvent pas être placés pour le fichier exécutable lancé.  
  
## Syntaxe  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Implémentée par les moteurs de débogage et consommé par le débogueur interface utilisateur de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll