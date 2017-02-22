---
title: "Comment&#160;: cr&#233;er des mod&#232;les de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ExportTemplateWizard"
helpviewer_keywords: 
  - "modèles de projet, créer"
  - "modèles de projet, emplacements de modèles personnalisés"
  - "modèles de projet, fichiers des métadonnées"
  - "modèles Visual Studio, créer des modèles de projets"
  - "modèles Visual Studio, modèles de projet"
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Comment&#160;: cr&#233;er des mod&#232;les de projet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure permet de créer un modèle à l'aide de l'Assistant **Exporter le modèle**, qui vous permet d'empaqueter votre modèle dans un fichier .zip.  Vous pouvez également créer des modèles au format VSIX pour un meilleur déploiement à l'aide de l'extension Assistant exportation de modèle, à l'aide de modèles inclus dans [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)], ou bien manuellement.  
  
### Pour créer un modèle de projet personnalisé avec l'Assistant Exportation de modèle standard  
  
1.  Créez un projet.  
  
    > [!NOTE]
    >  Utilisez uniquement des caractères d'identificateur valides lorsque vous nommez un projet qui sera source d'un modèle.  Un modèle exporté depuis un projet nommé avec des caractères non valides peut provoquer des erreurs de compilation dans les futurs projets basés sur le modèle.  Pour plus d'informations sur les caractères d'identificateur valides, consultez [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
2.  Modifiez le projet jusqu'à ce qu'il soit prêt à exporter en tant que modèle.  
  
3.  Modifiez les fichiers de code pour indiquer où le remplacement de paramètres doit avoir lieu.  Pour plus d'informations sur le remplacement de paramètres, consultez [Comment : substituer des paramètres dans un modèle](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  Dans le menu **Fichier**, cliquez sur **Exporter le modèle**.  L'Assistant **Exportation de modèle** s'ouvre.  
  
5.  Cliquez sur **Modèle de projet**.  
  
6.  Si votre solution comporte plusieurs projets, sélectionnez ceux que vous souhaitez exporter vers un modèle.  
  
7.  Cliquez sur **Suivant**.  
  
8.  Sélectionnez une icône et une image d'aperçu pour votre modèle.  Elles apparaissent dans la boîte de dialogue **Nouveau projet**.  
  
9. Entrez un nom de modèle et une description.  
  
10. Cliquez sur **Terminer**.  Votre projet est exporté dans un fichier .zip et placé à l'emplacement de sortie spécifié, et, si la sélection en a été faite, importé dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Si le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] est installé, vous pouvez encapsuler le modèle fini dans un fichier .vsix en vue de le déployer à l'aide du modèle **Projet VSIX**.  Pour plus d'informations, consultez [Mise en route avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## Voir aussi  
 [Création de modèles de projets et d'éléments personnalisés](../ide/creating-project-and-item-templates.md)   
 [Comment : créer des modèles d'élément](../ide/how-to-create-item-templates.md)