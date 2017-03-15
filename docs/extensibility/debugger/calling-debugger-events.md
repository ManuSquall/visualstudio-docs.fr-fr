---
title: "Appeler les &#233;v&#233;nements de d&#233;bogueur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage [Debugging SDK], événements"
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Appeler les &#233;v&#233;nements de d&#233;bogueur
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les événements dans les sessions de débogage se produisent dans un ordre spécifique.  
  
## Discussion  
 Pour comprendre le modèle des appels entre le moteur de débogage \(DE\) et la session déboguez le gestionnaire \(SDM\), le suivant représente l'ordre d'appel des événements qui se produisent dans une session de débogage classique :  
  
1.  [Attachement et de détachement à un programme](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [lancer le débogueur](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [terminer un programme](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [créer un point d'arrêt](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Lorsqu'un point d'arrêt des liens ou devenant annulé la liaison](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [erreurs de point d'arrêt](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Atteindre un point d'arrêt](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [supprimer un point d'arrêt](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Le passage en mode arrêt](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Progression en mode arrêt](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Évaluation de l'expression en mode arrêt](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Gestion des exceptions](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## Voir aussi  
 [Création d'un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)