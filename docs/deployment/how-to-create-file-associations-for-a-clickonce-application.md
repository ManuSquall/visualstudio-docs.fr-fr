---
title: "How to: Create File Associations For a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "file associations, ClickOnce applications"
  - "ClickOnce deployment, file associations"
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create File Associations For a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peuvent être associées à une ou plusieurs extensions de nom de fichier afin que l'application soit démarrée automatiquement lorsque l'utilisateur ouvre un fichier de ces types.  L'ajout du support d'extension de nom de fichier à une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] est simple.  
  
### Pour créer des associations de fichiers pour une application ClickOnce  
  
1.  Créez normalement une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ou utilisez votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] existante.  
  
2.  Ouvrez le manifeste d'application avec un éditeur de texte ou XML, tel que le Bloc\-notes.  
  
3.  Recherchez l'élément `assembly`.  Pour plus d'informations, consultez [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
4.  En tant qu'enfant de l'élément `assembly`, ajoutez un élément `fileAssociation`.  L'élément `fileAssociation` contient quatre attributs.  
  
    -   `extension` : extension de nom de fichier que vous souhaitez associer à l'application.  
  
    -   `description` : description du type de fichier, qui apparaîtra dans le shell Windows.  
  
    -   `progid` : chaîne qui identifie le type de fichier de manière unique, pour le marquer dans le Registre.  
  
    -   `defaultIcon` : icône à utiliser pour ce type de fichier.  L'icône doit être ajoutée en tant que ressource de fichier dans le manifeste de l'application.  Pour plus d'informations, consultez [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Pour obtenir un exemple des éléments `file` et `fileAssociation`, consultez [\<fileAssociation\> Element](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Si vous souhaitez associer plusieurs types de fichier à l'application, ajoutez des éléments `fileAssociation` supplémentaires.  Notez que l'attribut `progid` doit être différent pour chacun.  
  
6.  Une fois que vous avez terminé avec le manifeste de l'application, signez de nouveau le manifeste.  Vous pouvez le faire à partir de la ligne de commande à l'aide de Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Pour plus d'informations, consultez [Mage.exe \(outil Manifest Generation and Editing\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
## Voir aussi  
 [\<fileAssociation\> Element](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [Mage.exe \(outil Manifest Generation and Editing\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)