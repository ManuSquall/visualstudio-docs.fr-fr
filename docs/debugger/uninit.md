---
title: "UnInit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# UnInit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Finalise le fichier journal de graphiques, le ferme, et libère les ressources utilisées lorsque l'application enregistrait les informations graphiques.  
  
## Syntaxe  
  
```cpp  
void UnInit();  
```  
  
## Remarques  
 `UnInit` est appelé automatiquement lorsqu'une instance de la classe `VsgDbg` est détruite.  Si l'instance de `VsgDbg` n'était pas en train d'enregistrer des informations graphiques, cela n'a aucun effet.  
  
 Après que `UnInit` a été appelé une instance de la classe `VsgDbg`, un fichier journal graphiques peut être créé en appelant `Init` et finalisation en appelant `UnInit`.  Vous pouvez répéter cette opération autant de fois que vous souhaitez utiliser la même instance de `VsgDbg` pour créer plusieurs fichiers journaux indépendants de graphiques.  
  
## Voir aussi  
 [Init](../debugger/init.md)