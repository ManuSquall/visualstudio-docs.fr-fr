---
title: "MSBuild Error MSB3172 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.ReadInputManifestFailed"
helpviewer_keywords: 
  - "MSB3172"
ms.assetid: aa7291db-1f36-41e7-a510-90cd4daaa89d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3172
**MSB3172 : Impossible de lire le manifeste '\<fichier\>'. '  \<erreur\>'**  
  
 Cette erreur est générée lorsque le processus de génération rencontre un problème général lors de la lecture d'un fichier manifeste.  Le message d'erreur contient le nom du fichier, suivi d'informations plus détaillées sur le problème.  
  
 Il se peut que vous ayez ajouté un assembly ou un fichier manifeste comme fichier de contenu.  Vous devez utiliser la commande **Ajouter une référence** au lieu d'**Ajouter un fichier** afin que l'assembly dépendant soit référencé correctement par le système de projet.  Les projets plus sophistiqués marquent communément le .exe.manifest du dossier Bin comme fichier projet, mais vous devez éviter de procéder ainsi.  Le fichier caché app.manifest devient le fichier .exe.manifest et peut être modifié manuellement pour les scénarios avancés.  
  
## Voir aussi  
 [\<PackageFiles\>, élément](../deployment/packagefiles-element-bootstrapper.md)