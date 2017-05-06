---
title: "Comment&#160;: ajouter un fichier de ressources"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "fichiers de ressources (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, fichiers de ressources"
ms.assetid: 2b4ac232-992e-4070-8e98-6f11eb88e1a8
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Comment&#160;: ajouter un fichier de ressources
  Les commandes d'ajout de fichiers de ressources figurent dans le menu contextuel du nœud de la solution et des nœuds des fonctionnalités de l'Explorateur de solutions.  Pour plus d'informations, consultez [Localisation de solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
### Pour ajouter un fichier de ressources globales à une solution SharePoint  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez une solution SharePoint.  
  
2.  Dans l'**Explorateur de solutions**, choisissez un nœud de projet SharePoint, puis, dans la barre de menus, choisissez **Project**, **Ajouter un nouvel objet**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez le modèle **Fichier de Ressources Global**, puis le bouton **Ajouter**.  
  
    > [!NOTE]  
    >  Le modèle d'élément de projet Fichier de ressources global apparaît uniquement lorsqu'un élément de projet SharePoint est sélectionné.  
  
4.  Dans la boîte de dialogue **Ajouter une ressource**, choisissez une culture pour le fichier de ressources, comme par exemple, Anglais \(États\-Unis\).  
  
     Cette étape permet d'ajouter un fichier de ressources globales à votre solution sous le format, Resource*xx* **.**culture *culture.*resx, tel que Resource1.fr\-FR.resx.  
  
5.  Lorsque l'**Éditeur de ressources** s'ouvre dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ajoutez des ressources dans le fichier de ressources.  
  
### Pour ajouter un fichier de ressources globales à une fonctionnalité SharePoint  
  
1.  Si la solution SharePoint n'est pas déjà ouverte dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez la solution.  
  
2.  Dans l'**Explorateur de solutions**, ouvrez le menu contextuel pour le nom  d'un composant sous le nœud **Composants**, puis choisissez **Ajouter une ressource de composant**.  
  
     Cette étape ajoute un fichier de ressources au composant au format, *ResourceFileName***.***culture***.**resx, comme, Feature1.en\-US.resx.  
  
3.  Lorsque l'**Éditeur de ressources** s'ouvre dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ajoutez des ressources dans le fichier de ressources.  
  
## Voir aussi  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  