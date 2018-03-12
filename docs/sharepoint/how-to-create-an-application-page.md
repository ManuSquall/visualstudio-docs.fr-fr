---
title: "Comment : créer une Page d’Application | Documents Microsoft"
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
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9429f2834997ce5ad2c3359fb04c164995dd2e12
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-an-application-page"></a>Comment : créer une page d'application
  Vous pouvez créer une page web d’ASP.NET pour un ou plusieurs sites SharePoint. Dans SharePoint, ces pages sont appelées pages d’application. Contrairement à une page de site, une page d’application contient le code qui s’exécute derrière la page. Pour plus d’informations, consultez [création de Pages d’Application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### <a name="to-create-an-application-page"></a>Pour créer une page d’application  
  
1.  Dans Visual Studio, ouvrez ou créez un projet SharePoint.  
  
     Pour plus d’informations, consultez [projets et modèles d’élément de projet SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Dans l' **Explorateur de solutions**, choisissez le nœud du projet.  
  
3.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
4.  Dans le **ajouter un nouvel élément** boîte de dialogue, développez le **SharePoint** nœud, puis choisissez le **2010** élément.  
  
5.  Dans la liste de modèles SharePoint, choisissez **Page Application**.  
  
6.  Dans le **nom** zone, spécifiez un nom pour la page d’application, puis choisissez le **ajouter** bouton.  
  
     Visual Studio ajoute plusieurs fichiers et dossiers à votre projet. Pour plus d’informations sur ces fichiers, consultez [création de Pages d’Application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     Dans le **Source** du concepteur Visual Web Developer, le fichier de page ASP.NET s’affiche. Vous pouvez concevoir la page en ajoutant des contrôles à partir de la **boîte à outils** et en les plaçant sur des espaces réservés de contenu. Pour plus d’informations, consultez [mode Source, le Concepteur de pages Web](http://msdn.microsoft.com/en-us/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Si vous souhaitez gérer les événements de contrôle, ajoutez le code au fichier de code pour la page de l’application.  
  
     Le fichier de code s’affiche si vous développez le nœud pour le fichier de page ASP.NET et a une extension .cs ou .vb, selon le langage du projet. Pour obtenir un exemple de bout en bout de la création d’une page d’application, consultez [procédure pas à pas : création d’une Page d’Application SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création de Pages d’Application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Procédure pas à pas : création d’une page d’application SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  