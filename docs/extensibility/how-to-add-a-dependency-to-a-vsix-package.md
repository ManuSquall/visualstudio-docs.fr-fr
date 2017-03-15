---
title: "Comment&#160;: ajouter une d&#233;pendance &#224; un Package VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "référence de package"
  - "assembly de package"
  - "dll de package"
  - "référence VSIX"
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Comment&#160;: ajouter une d&#233;pendance &#224; un Package VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez configurer un déploiement de package VSIX qui installe les dépendances qui ne sont pas déjà présents sur l’ordinateur cible. Pour ce faire, incluez les dépendances VSIX dans le fichier source.extension.vsixmanifest.  
  
#### Pour ajouter une dépendance  
  
1.  Ouvrez le fichier source.extension.vsixmanifest dans le **conception** affichage. Accédez à la **dépendances** onglet, cliquez sur **nouveau**.  
  
2.  Pour ajouter une extension installée : dans le **Ajouter une nouvelle dépendance** boîte de dialogue, sélectionnez **installé extension** puis, pour le **nom**, sélectionnez une extension dans la liste.  
  
3.  Pour ajouter une autre extension VSIX qui n’est pas installé : : dans le **Ajouter une nouvelle dépendance** boîte de dialogue, sélectionnez **fichier sur le système de fichiers** puis utiliser le **Parcourir** pour sélectionner l’extension VSIX.  
  
## Voir aussi  
 [Référence du schéma 1.0 Extension VSIX](http://msdn.microsoft.com/fr-fr/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomie d'un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Préparation des Extensions pour le déploiement de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)