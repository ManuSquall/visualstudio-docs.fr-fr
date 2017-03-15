---
title: "Erreur&#160;: impossible de copier la d&#233;pendance &#39;fichier&#39; du projet &#39;projet&#39; dans le r&#233;pertoire d&#39;ex&#233;cution, car elle serait en conflit avec la d&#233;pendance &#39;fichier&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.copy_version_conflict"
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erreur&#160;: impossible de copier la d&#233;pendance &#39;fichier&#39; du projet &#39;projet&#39; dans le r&#233;pertoire d&#39;ex&#233;cution, car elle serait en conflit avec la d&#233;pendance &#39;fichier&#39;
Il existe un conflit entre des références, car plusieurs dépendances distinctes qui portent le même nom de fichier sont copiées dans le répertoire bin pour permettre à l’application de s’exécuter. Le répertoire d’exécution ne peut pas résoudre le conflit dans la mesure où aucune des dépendances n’est une référence principale.  
  
 Cette erreur entraîne l’échec de la build.  
  
 Le fait de double\-cliquer sur cet élément de la liste des tâches vous conduit au nœud de références du projet où le conflit se présente.  
  
 **Pour corriger cette erreur**  
  
-   Configurez l’un des assemblys en référence directe de votre projet. Cette approche présente toutefois un inconvénient potentiel, puisqu’il n’est pas garanti que l’assembly que vous choisissez fonctionne avec les assemblys qui nécessitent une autre version de l’assembly référencé.  
  
     ou  
  
-   Vérifiez que les deux copies de l’assembly portent un nom fort et se trouvent dans le Global Assembly Cache. Ceci élimine le besoin de copier les assemblys dans le répertoire bin.  
  
## Voir aussi  
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [Global Assembly Cache](../Topic/Global%20Assembly%20Cache.md)   
 [Assemblys avec nom fort](../Topic/Strong-Named%20Assemblies.md)   
 [Versioning des assemblys](../Topic/Assembly%20Versioning.md)   
 [Comment : créer et supprimer les dépendances d'un projet](../Topic/How%20to:%20Create%20and%20Remove%20Project%20Dependencies.md)