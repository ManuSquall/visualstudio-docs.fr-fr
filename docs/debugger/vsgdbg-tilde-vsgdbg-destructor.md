---
title: "VsgDbg::~VsgDbg, destructeur | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg::~VsgDbg, destructeur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Détruit une instance de la classe `VsgDbg`.  Si les informations graphiques sont en train d'être enregistrées, le fichier journal de graphique est finalisé, fermé et les ressources qui étaient utilisées pendant que les informations graphiques sont libérées.  
  
## Syntaxe  
  
```cpp  
~VsgDbg();  
```  
  
## Voir aussi  
 [VsgDbg::VsgDbg, constructeur](../Topic/VsgDbg::VsgDbg%20\(Constructor\).md)