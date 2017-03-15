---
title: "ToggleHUD | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ToggleHUD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bascule la superposition de diagnostique graphique *HUD* \(Head\-Up Display\) sur on ou off.  
  
## Syntaxe  
  
```cpp  
void ToggleHUD();  
```  
  
## Remarques  
 Le diagnostique graphique HUD est affiché dans l'angle supérieur gauche de l'application qui s'exécute sous le diagnostic graphiques.  Il affiche des informations d'exécution sur l'application et sur la capture d'informations graphiques, et les messages qui sont ajoutés en appelant la fonction membre [AddMessage](../debugger/addmessage.md).  
  
 Pour basculer HUD, vous ne devez pas nécesairement capturer des informations graphiques \-, c'est\-à\-dire qu'il peut être basculé via une instance de la classe `VsgDbg`, mais la fonction membre [Init](../debugger/init.md) ne doit pas être appelée en premier.