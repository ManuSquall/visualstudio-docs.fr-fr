---
title: "EndCapture | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# EndCapture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Termine un intervalle de capture qui a été démarré par `BeginCapture`.  
  
## Syntaxe  
  
```cpp  
void EndCapture();  
```  
  
## Remarques  
 Un intervalle de capture couvre généralement un sous\-ensemble d'un frame, quand vous souhaitez entrer des informations graphiques uniquement sur un certain type d'appel de dessin.  Si l'intervalle de capture couvre un appel pour présenter, alors deux frames des informations graphiques sont capturées.  La première frame couvre l'intervalle entre l'appel de `BeginCapture` et l'appel pour présenter ; la deuxième frame couvre l'intervalle entre le premier événement Direct3D après l'appel pour présenter et l'appel à `EndCapture`.  
  
 Pour capturer un intervalle, vous devez préparer votre application pour capturer et stocker des informations graphiques \- autrement dit, vous devez avoir appelé [Init](../debugger/init.md) via une instance de la classe `VsgDbg` avant d'appeler `BeginCapture` ou `EndCapture`.  
  
## Voir aussi  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)