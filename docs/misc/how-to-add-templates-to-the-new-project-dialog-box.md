---
title: "Comment&#160;: ajouter des mod&#232;les &#224; la bo&#238;te de dialogue Nouveau projet | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "boîtes de dialogue, ajouter des modèles à un projet"
  - "projets (SDK Visual Studio), ajouter des modèles à une boîte de dialogue"
  - "modèles (Visual Studio), ajouter à la boîte de dialogue de projet"
ms.assetid: fd044681-e666-410d-815c-33db923ed888
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# Comment&#160;: ajouter des mod&#232;les &#224; la bo&#238;te de dialogue Nouveau projet
L’installation de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inclut un certain nombre de modèles de projets prédéfinis. Pour obtenir une liste complète des modèles de projet prédéfinis, consultez [NIB Création de projets à partir de modèles](http://msdn.microsoft.com/fr-fr/7c36d86a-6b79-4480-8228-0f925f1204b2). Outre les modèles de projet par défaut, vous pouvez créer des modèles de projet personnalisés ou spécifiques au sous\-type. Par exemple, le sous\-type **Smart Device** fournit ses propres modèles pour les projets [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Pour obtenir des instructions sur la création d’un modèle personnalisé, consultez [Comment : créer des modèles de projet](../ide/how-to-create-project-templates.md).  
  
## Ajout d’un modèle à la boîte de dialogue Nouveau projet  
  
#### Pour ajouter un modèle à la boîte de dialogue Nouveau projet  
  
1.  Créez un modèle avec le fichier MyTemplate.vstemplate.  
  
2.  Sélectionnez les fichiers présents dans votre modèle \(y compris le fichier .vstemplate\), cliquez dessus avec le bouton droit, puis cliquez sur **Envoyer vers** et sur **Dossier compressé**. Les fichiers précédemment extraits sont compressés dans un fichier .zip.  
  
 Placez le fichier de modèle .zip dans **%USERPROFILE%\\Documents\\Visual Studio 2015\\Templates\\ProjectTemplates**.  
  
## Voir aussi  
 [Project Subtypes](d235b47b-cf11-4d47-a63f-e33d9d16105d2044a030-0795-4940-bd65-a6e44de98a0f)   
 [NIB : Modèles Visual Studio](http://msdn.microsoft.com/fr-fr/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Faisant partie de la boîte de dialogue Nouvel élément Ajouter](../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)