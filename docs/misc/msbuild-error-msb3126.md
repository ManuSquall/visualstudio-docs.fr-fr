---
title: "MSBuild Error MSB3126 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsNotInstalled"
helpviewer_keywords: 
  - "MSB3126"
ms.assetid: 0c92cbb6-9100-4433-8113-f2f3a1432243
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3126
**MSB3126 : L'application utilise des associations de fichiers mais n'est pas marquée pour une installation.  Les associations de fichiers ne peuvent pas être utilisées pour des applications qui ne sont pas installées, par exemple les applications hébergées dans un navigateur Web.**  
  
 Cette erreur se produit lorsqu'une application est configurée pour utiliser des associations de fichiers alors que le mode En ligne uniquement est défini pour l'installation de l'application.  Les associations de fichiers ne sont pas disponibles, car les applications de type En ligne uniquement sont généralement exécutées dans un navigateur.  
  
### Pour corriger cette erreur  
  
-   Sélectionnez l'option **L'application est également disponible hors connexion \(accessible depuis le menu Démarrer\)** dans la zone **Mode et paramètres d'installation**.  Pour plus d'informations, consultez [How to: Specify the ClickOnce Offline or Online Install Mode](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md).  
  
## Voir aussi  
 [Page Publier, Concepteur de projets](../ide/reference/publish-page-project-designer.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)