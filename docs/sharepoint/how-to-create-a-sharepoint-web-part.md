---
title: "Comment&#160;: cr&#233;er un composant WebPart SharePoint | Microsoft Docs"
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
  - "WebParts (développement SharePoint dans Visual Studio), ajouter"
  - "WebParts (développement SharePoint dans Visual Studio), créer"
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Comment&#160;: cr&#233;er un composant WebPart SharePoint
  Créez et personnalisez un composant WebPart en ajoutant un élément **Composant WebPart** à tout projet SharePoint puis en modifiant le fichier de code de WebPart ou en utilisant un concepteur.  Pour plus d'informations, consultez [Comment : créer un composant WebPart SharePoint à l'aide d'un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### Pour créer un composant WebPart SharePoint  
  
1.  Ouvrez ou créez un projet SharePoint.  
  
     Pour plus d'informations, consultez [Modèles de projets et d'éléments de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Dans l'**Explorateur de solutions**, sélectionnez le nœud du projet Sharepoint, puis cliquez sur **Ajouter un nouvel élément** dans le menu **Projet**.  
  
3.  Dans la boîte de dialogue **Ajouter un nouvel élément**, développez le noeud **SharePoint**, puis sélectionnez le noeud **2010**.  
  
4.  Dans la liste de modèles SharePoint, sélectionnez **Composant WebPart**.  
  
5.  Dans la zone **Nom**, indiquez un nom pour la WebPart, puis choisissez le bouton **Ajouter**.  
  
     Le composant WebPart s'affiche dans l'**Explorateur de solutions**.  Pour plus d'informations sur les fichiers inclus dans un élément WebPart, consultez [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  Dans **Explorateur de solutions**, ouvrez le fichier de code du composant WebPart que vous venez de créer.  
  
     Par exemple, si le nom du composant WebPart est WebPart1, double\-cliquez sur WebPart1.vb \(en Visual Basic\) ou WebPart1.cs \(en C\#\).  
  
7.  Ajoutez des contrôles à la méthode <xref:System.Web.UI.Control.CreateChildControls%2A> du fichier de code du composant WebPart.  
  
     Pour obtenir un exemple, consultez [Procédure pas à pas : création d'un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## Voir aussi  
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Comment : créer un composant WebPart SharePoint à l'aide d'un concepteur](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Procédure pas à pas : création d'un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Procédure pas à pas : création d'un composant WebPart pour SharePoint à l'aide d'un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  