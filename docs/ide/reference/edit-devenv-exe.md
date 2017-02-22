---
title: "/Edit (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/Edit (commutateur Devenv)"
  - "Devenv, /Edit (commutateur)"
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ouvre le fichier spécifié dans une instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Syntaxe  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## Arguments  
 `file1`  
 Facultatif.  Fichier à ouvrir dans une instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Si aucune instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] n'existe, une nouvelle instance est créée avec une disposition de fenêtre simplifiée, et `file1` est ouvert dans la nouvelle instance.  
  
 `file2`  
 Facultatif.  Un ou plusieurs fichiers supplémentaires à ouvrir dans l'instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Notes  
 Si aucun fichier n'est spécifié et qu'il existe une instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l'instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] reçoit le focus.  Si aucun fichier n'est spécifié et qu'il n'y a aucune instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], une nouvelle instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est créée avec une disposition de fenêtre simplifiée.  
  
 Si l'instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est dans un état modal, par exemple, si la [boîte de dialogue Options](../../ide/reference/options-dialog-box-visual-studio.md) est ouverte, le fichier s'ouvre dans l'instance existante lorsque [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] quitte l'état modal.  
  
## Exemple  
 Cet exemple ouvre le fichier `MyFile.cs` dans une instance existante de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ou ouvre le fichier dans une nouvelle instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si l'une n'existe pas déjà.  
  
```  
devenv /edit MyFile.cs  
```  
  
## Voir aussi  
 [Commutateurs de la ligne de commande de Devenv](../../ide/reference/devenv-command-line-switches.md)