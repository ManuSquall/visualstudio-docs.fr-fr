---
title: "Comment : créer un composant WebPart SharePoint à l’aide d’un concepteur | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
ms.assetid: 6b88f3ef-02ff-4135-80ff-b4acacf8c695
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b993512350e6bd27d0dce8ef359bc33fccde5ff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Comment : créer un composant WebPart SharePoint à l'aide d'un concepteur
  Vous pouvez créer un composant WebPart en ajoutant un **composant Visual Web Part** élément à un projet SharePoint. Cela ouvre le concepteur Visual Web Developer dans Visual Studio où vous pouvez ajouter des contrôles et du code pour le composant WebPart. Visual WebPart fonctionne de la même façon comme composants WebPart. La seule différence est que vous concevez visual WebPart dans le concepteur Visual Web Developer.  
  
### <a name="to-create-a-project-for-visual-web-parts"></a>Pour créer un projet pour visual WebPart  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
2.  Dans le **nouveau projet** boîte de dialogue, sous **Visual C#** ou **Visual Basic**, développez le **Office/SharePoint** nœud, puis choisissez le **Solutions SharePoint** catégorie.  
  
3.  Dans la liste des modèles de projet, choisissez **SharePoint 2013 - composant Visual Web Part**, puis choisissez le **OK** bouton.  
  
     Le **Assistant Personnalisation de SharePoint** s’affiche.  
  
4.  Sur le **spécifier le niveau de site et de sécurité pour le débogage** page, spécifiez l’URL d’un site SharePoint qui se trouve sur l’ordinateur local, puis choisissez le **Terminer** bouton.  
  
     Dans **l’Explorateur de solutions**, un composant WebPart s’affiche. Après avoir créé le composant WebPart dans le concepteur Visual Web Developer, vous devez la tester sur le site que vous spécifiez.  
  
### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Pour ajouter un composant visual web part à un projet SharePoint existant  
  
1.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, choisissez le **Office/SharePoint** nœud.  
  
3.  Dans la liste des modèles de projet, choisissez **composant Visual Web Part**, nom, puis sélectionnez le **ajouter** bouton.  
  
     Dans **l’Explorateur de solutions**, votre composant WebPart s’affiche. Après avoir créé le composant WebPart dans le concepteur Visual Web Developer, vous devez la tester sur le site que vous spécifiez.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Comment : créer un composant WebPart SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)   
 [Procédure pas à pas : Création d’un composant WebPart pour SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Procédure pas à pas : création d’un composant WebPart pour SharePoint à l’aide d’un concepteur](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  