---
title: "MSBuild Error MSB3150 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.NoStringsForCulture"
helpviewer_keywords: 
  - "MSB3150"
ms.assetid: 90d86aef-f4df-4070-8ecc-173eb40668aa
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3150
**MSB3150 : Aucune ressource de type chaîne disponible pour générer un programme d'amorçage avec la culture '{0}'.**  
  
 Cette erreur se produit lorsque setup.xml a été détecté, mais ne contient pas le nœud Strings.  Le fichier XML a été probablement endommagé.  
  
### Pour corriger cette erreur  
  
-   Ouvrez le **Panneau de configuration**, sélectionnez **Ajout\/Suppression de programmes** et réparez le Kit de développement Visual Studio SDK, ou copiez les fichiers dans le répertoire approprié \(\<chemin d'installation du Kit de développement\>\\bootstrapper\\engine\\\<culture\>\\setup.xml\).