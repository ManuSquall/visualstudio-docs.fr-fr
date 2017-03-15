---
title: "CaptureCurrentFrame | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CaptureCurrentFrame
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Capture le reste du frame actuel dans le fichier journal de graphiques.  
  
## Syntaxe  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## Remarques  
 Si une autre capture est actuellement en cours \- tel qu'une capture qui a été démarrée par la fonction `BeginCapture` \- Alors la capture est effectuée, terminée et enregistrée dans le fichier journal en tant que frame différent.  Juste après, le diagnostic du graphique commence en capturant le reste du frame actuel, qui est également stocké comme frame séparé.  La fin de frame actuel est marquée par un appel pour présenter.  
  
 Pour capturer un frame, vous devez préparer votre application pour capturer et stocker des informations graphiques \- autrement dit, vous devez avoir appelé [Init](../debugger/init.md) via une instance de la classe `VsgDbg` avant d'appeler `CaptureCurrentFrame` ou .  
  
## Voir aussi  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)