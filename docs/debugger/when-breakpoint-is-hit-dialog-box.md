---
title: "Lorsque le point d&#39;arr&#234;t est atteint, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.whenbreakpointishit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Lorsque le point d&#39;arr&#234;t est atteint, bo&#238;te de dialogue
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette boîte de dialogue vous permet de personnaliser l'action qui se produit lorsqu'un point d'arrêt est atteint.  
  
## Liste UIElement  
 **Afficher un message**  
 Affiche un message, dans la syntaxe DebuggerDisplay.  Pour plus d'informations, consultez [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Cette zone de texte prend également en charge des mots clé spéciaux \(tels que $ADDRESS\) qui peuvent être utilisés tels quels ou entre les accolades d'une expression DebuggerDisplay.  Les mots clés disponibles sont répertoriés dans la boîte de dialogue.  
  
 **Continuer l'exécution**  
 Ce contrôle est activé uniquement lorsque l'option **Afficher un message** est sélectionnée.  Avec ce contrôle sélectionné, vous pouvez utiliser un point d'arrêt comme point de trace pour tracer l'exécution de votre programme, plutôt que de provoquer un arrêt lorsque l'emplacement est atteint.  
  
## Voir aussi  
 [Utilisation des points d'arrêt](../debugger/using-breakpoints.md)   
 [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)