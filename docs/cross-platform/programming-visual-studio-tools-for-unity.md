---
title: "Programmation de Visual Studio Tools pour Unity | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 3
---
# Programmation de Visual Studio Tools pour Unity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans cette section, vous trouverez des exemples de l'utilisation de l'API Visual Studio Tools pour Unity.  
  
## Exemples  
 Voici quelques exemples qui montrent comment vous pouvez utiliser les outils Visual Studio pour les API Unity.  
  
### Personnaliser les fichiers projet créés par VSTU  
 Visual Studio Tools pour Unity fournit un rappel de type Unity pendant la génération du fichier projet.  Pour savoir comment vous pouvez modifier le fichier de projet chaque fois qu'il est régénéré, consultez [Exemple : génération de fichier projet](../cross-platform/customize-project-files-created-by-vstu.md).  
  
### Partager le rappel de journal Unity avec VSTU  
 Visual Studio Tools pour Unity enregistre un rappel de journal avec Unity pour pouvoir diffuser sa console vers Visual Studio.  Si vos scripts de l'éditeur enregistrent également un rappel de journal avec Unity, le rappel VSTU peut interférer avec lui.   Pour savoir comment vous pouvez partager le rappel de journal Unity avec VSTU, consultez [Exemple : rappel de journal](../cross-platform/share-the-unity-log-callback-with-vstu.md).