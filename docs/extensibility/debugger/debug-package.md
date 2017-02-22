---
title: "D&#233;boguer le Package | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (débogage SDK), packages"
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# D&#233;boguer le Package
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les passes de package de débogage dans Visual Studio écossent et les handles l'ensemble de l'interface utilisateur.  Elle consomme le débogage Visual Studio sert d'interface et communique au gestionnaire de débogage de session \(SDM\).  
  
 Désactivez les événements envoyés par le biais de le SDM changez le débogueur du mode exécution en mode arrêt et modifier le focus au programme où l'arrêt s'est produit.  Le package de débogage suit le frame de pile et le thread les informations qui lui sont envoyées par les événements.  
  
 Le package de débogage n'a aucune dépendance de langage ou l'environnement d'exécution.  il n'est pas nécessaire d'implémenter ou modifier le package de débogage.  
  
 le package de débogage est implémenté par vsdebug.dll.  
  
## Voir aussi  
 [Gestionnaire de session de débogage](../../extensibility/debugger/session-debug-manager.md)   
 [Frames de pile](../../extensibility/debugger/stack-frames.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)