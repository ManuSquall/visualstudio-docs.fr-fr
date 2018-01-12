---
title: "Comment : créer un contrôle utilisateur pour une Page d’Application SharePoint WebPart ou | Documents Microsoft"
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
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7fc51bae65f67a3810c6db208e5f7c6f04183c22
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Comment : créer un contrôle utilisateur pour un composant WebPart ou une page d'application SharePoint
  Vous pouvez créer des contrôles utilisateur personnalisés qui fournissent des fonctionnalités personnalisées pour votre solution SharePoint, et vous pouvez réutiliser cette fonctionnalité dans votre projet. Vous pouvez inclure les contrôles utilisateur dans une application ou un composant WebPart page, ajouter d’autres contrôles ASP.NET et les contrôles de SharePoint et définir des propriétés et méthodes pour le contrôle. Pour plus d’informations sur les contrôles utilisateur, consultez [création de contrôles réutilisables pour les composants WebPart ou les Pages d’Application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) et [les contrôles utilisateur et serveur dans SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>Pour créer un contrôle utilisateur pour SharePoint  
  
1.  Dans Visual Studio, ouvrez ou créez un projet SharePoint.  
  
     Consultez [modèles d’élément de projet SharePoint et le projet](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Dans l' **Explorateur de solutions**, choisissez le nœud du projet.  
  
3.  Dans la barre de menus, choisissez **projet**, **ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.  
  
4.  Dans le **installé** volet, choisissez la **Office/SharePoint** nœud.  
  
5.  Dans la liste de modèles SharePoint, choisissez **contrôle utilisateur (Solution de batterie uniquement)**.  
  
    > [!NOTE]  
    >  Contrôles utilisateur fonctionnent uniquement dans les solutions de batterie de serveurs.  
  
6.  Dans le **nom** zone, spécifiez un nom pour le contrôle utilisateur, puis choisissez le **ajouter** bouton.  
  
     Visual Studio ajoute plusieurs fichiers et dossiers à votre projet. Pour plus d’informations sur ces fichiers, consultez [création de contrôles réutilisables pour les composants WebPart ou les Pages d’Application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     Par défaut, le fichier de contrôle utilisateur s’affiche dans le **Source** vue du concepteur Visual Web Developer. Dans cette vue, vous pouvez modifier le balisage XML du contrôle. Vous pouvez basculer vers **conception** afficher si vous souhaitez concevoir visuellement le contrôle en faisant glisser des contrôles à partir de la **boîte à outils**. Consultez [en mode conception, le Concepteur de pages Web](http://msdn.microsoft.com/en-us/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Si vous souhaitez gérer les événements qui se produisent dans le contrôle, ajoutez le code au fichier de code du contrôle utilisateur.  
  
     Ce fichier s’affiche dans **l’Explorateur de solutions** sous le fichier de contrôle utilisateur et a une extension .cs ou .vb, selon le langage du projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de contrôles réutilisables pour les composants WebPart ou les Pages d’Application](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Création de Pages d’Application pour SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Création de composants WebPart pour SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  