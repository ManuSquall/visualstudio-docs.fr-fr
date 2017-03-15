---
title: "MSBuild Error MSB3149 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.NoResources"
helpviewer_keywords: 
  - "MSB3149"
ms.assetid: 63857405-d420-457d-9ba7-80e1a2a9dcb7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3149
**MSB3149 : Aucune ressource disponible pour générer un programme d'amorçage.**  
  
 Cette erreur se produit lorsque aucun fichier de ressources du programme d'amorçage \(setup.xml\) correspondant à une culture n'a pu être trouvé.  
  
### Pour corriger cette erreur  
  
-   Ouvrez le **Panneau de configuration**, sélectionnez **Ajout\/Suppression de programmes** et réparez le Kit de développement Visual Studio SDK, ou copiez les fichiers dans le répertoire approprié \(\<chemin d'installation du Kit de développement\>\\bootstrapper\\engine\\\<culture\>\\setup.xml\).  
  
## Voir aussi  
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)