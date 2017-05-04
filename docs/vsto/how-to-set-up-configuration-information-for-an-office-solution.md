---
title: "Comment&#160;: configurer les informations de configuration d&#39;une solution Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "fichiers de configuration (développement Office dans Visual Studio)"
  - "solutions (développement Office dans Visual Studio), fichiers de configuration"
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Comment&#160;: configurer les informations de configuration d&#39;une solution Office
  Vous pouvez utiliser des fichiers de configuration pour configurer les paramètres spécifiques à votre solution Office.  Vous pouvez spécifier des paramètres, tels que la stratégie de liaison d'assembly, les objets de communication à distance et les paramètres de débogage et de traçage.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Pour ajouter un fichier de configuration à votre projet Office  
  
1.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
2.  Dans le volet **Catégories**, cliquez sur **Général**.  
  
3.  Dans le volet **Modèles**, sélectionnez **Fichier de configuration de l'application**.  
  
4.  Dans la zone **Nom**, tapez le même nom que celui de l'assembly avec l'extension .config.  Par exemple, un fichier de configuration pour un assembly de projet Excel appelé ExcelWorkbook1.dll serait nommé ExcelWorkbook1.dll.config.  
  
5.  Cliquez sur **Ajouter**.  
  
6.  Créez votre fichier de configuration d'après le schéma de fichier de configuration de l'application.  Pour plus d’informations, consultez [Schéma des fichiers de configuration pour le .NET Framework](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md).  
  
 L'utilisation de fichiers de configuration avec des projets Office n'implique aucune considération particulière.  
  
## Voir aussi  
 [Schéma des fichiers de configuration pour le .NET Framework](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)   
 [Conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md)   
 [Déploiement d'une solution Office](../vsto/deploying-an-office-solution.md)  
  
  