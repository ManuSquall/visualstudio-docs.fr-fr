---
title: "Windows Script Hosts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Windows Script Host, implémenter les hôtes"
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Windows Script Hosts
En implémentant l'hôte de script Microsoft Windows, vous pouvez ignorer sans risque supposer qu'un moteur de script appelle uniquement l'interface d' [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) dans le contexte du thread de base tant que l'hôte effectue les opérations suivantes :  
  
-   Choisit un thread de base \(généralement le thread qui contient la boucle de message\).  
  
-   Instancie le moteur de script dans le thread de base.  
  
-   Méthodes du moteur de script d'appels uniquement le thread de base, sauf dans spécifiquement autorisé, comme lorsqu'il s'agit d' [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) et d' [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
-   Appelle l'objet de l'expédition du moteur de script que le thread de base.  
  
-   Garantit que la boucle de message s'exécute dans le thread de base si un handle de fenêtre est fournie.  
  
-   Garantit que les objets des événements de source du modèle objet de l'hôte uniquement dans le thread de base.  
  
 Ces règles sont automatiquement suivies par tous les hôtes monothread.  Le modèle décrit ci\-dessus est limité volontairement assez faible pour permettre à un hôte pour interrompre un script coincé en appelant [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) d'un autre thread \(initialisé par un gestionnaire de CTRL\+ATTN ou analogues\), ou pour reproduire un script dans un nouveau thread à l'aide de [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
## Remarques  
 Aucune de ces restrictions n'applique à un hôte qui choisit d'implémenter une interface libre de threads d' [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) et un modèle objet libre de threads.  Un tel hôte peut utiliser l'interface d' [IActiveScript](../winscript/reference/iactivescript.md) de n'importe quel thread, sans restriction.  
  
## Voir aussi  
 [\<PAVE OVER\> Interfaces de script Microsoft Windows \- Introduction](../Topic/%3CPAVE%20OVER%3E%20Microsoft%20Windows%20Script%20Interfaces%20-%20Introduction.md)