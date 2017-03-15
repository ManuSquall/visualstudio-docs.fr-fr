---
title: "MSBuild Error MSB3152 | Microsoft Docs"
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
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
helpviewer_keywords: 
  - "MSB3152"
ms.assetid: 5a3859d4-4107-4e46-bb42-04de92b551de
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3152
**MSB3152 : L'emplacement d'installation pour les composants requis n'a pas été défini à 'site Web du fabricant du composant' et le fichier '\<fichier\>' dans l'élément '\<package\>' est introuvable sur le disque.  Pour plus d'informations, consultez l'aide.**  
  
 Cette erreur se produit lorsqu'il manque un fichier nécessaire au programme d'installation des composants requis.  Les fichiers du programme d'installation accèdent à un dossier spécifique que Visual Studio a réservé pour les packages redistribuables.  Ce dossier varie en fonction de la version de Visual Studio avec laquelle vous développez.  Pour plus d'informations sur l'emplacement du dossier spécifique, consultez [Création de packages de programme d'amorçage](../deployment/creating-bootstrapper-packages.md).  
  
### Pour corriger cette erreur  
  
-   Vérifiez si le fichier est présent sur le disque.  
  
-   Utilisez HomeSite pour essayer de résoudre le problème de package.  
  
-   Affectez la valeur `false` à `CopyComponents` dans le fichier projet.  
  
-   N'utilisez pas le package de programme d'amorçage altéré.  
  
## Voir aussi  
 [Création de packages de programme d'amorçage](../deployment/creating-bootstrapper-packages.md)