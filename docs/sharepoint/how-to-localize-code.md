---
title: "Comment : localiser du Code | Documents Microsoft"
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
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 0e852052-5ad4-4517-81cf-8865ec304441
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7c283f8e2b73fdb4ba44322ca09f8fb436d729ec
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-localize-code"></a>Comment : localiser du code
  Code non localisé utilise des valeurs de chaîne codée en dur. Pour localiser des chaînes de code, remplacez-les par des appels à <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, qui est une méthode qui fait référence à des ressources localisées.  
  
## <a name="localizing-code"></a>Localisation du Code  
  
#### <a name="to-localize-code"></a>Pour localiser le code  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour un élément de projet, puis choisissez **ajouter**, **Module**.  
  
     Choisissez le **fichier de ressources** modèle.  
  
    > [!NOTE]  
    >  Veillez à ajouter le fichier de ressources à un élément de projet SharePoint afin que la propriété Type de déploiement est disponible. Cette propriété est requise plus loin dans cette procédure.  
  
2.  Nommez le fichier de ressources de langue par défaut de votre choix, avec l’extension .resx, par exemple MyAppResources.resx.  
  
3.  Répétez les étapes 1 et 2 pour ajouter des fichiers de ressources séparés à l’élément de projet SharePoint : un pour chaque langue localisée.  
  
     Utiliser le même nom de base pour chaque fichier de ressources localisé, mais ajouter l’ID de culture. Par exemple, nommez une ressource localisée en allemand MyAppResources.de-de.resx.  
  
4.  Ouvrez chaque fichier de ressources et ajouter des chaînes localisées. Utilisez la même chaîne ID dans chaque fichier.  
  
5.  Modifiez la valeur de la **Type de déploiement** propriété de chaque fichier de ressources à **par AppGlobalResource** pour que chaque fichier à déployer sur le dossier du serveur App_GlobalResources.  
  
6.  Laissez la valeur de la **Action de génération** propriété de chaque fichier en tant que **ressource incorporée**.  
  
     Les ressources incorporées sont compilées dans DLL du projet.  
  
7.  Générez le projet pour créer la ressource DLL satellites.  
  
8.  Dans le **Concepteur de packages**, choisissez le **avancé** onglet et ajoutez l’assembly satellite.  
  
9. Dans le **emplacement** zone, ajoutez un dossier ID de culture pour le chemin d’accès, tel que fr-fr\\*nom d’élément de projet*. resources.dll.  
  
10. Si votre solution ne référence pas déjà l’assembly System.Web, ajoutez une référence à celle-ci et ajoutez une directive dans votre code pour <xref:System.Web>.  
  
11. Recherchez toutes les chaînes codées en dur dans votre code qui sont visibles par les utilisateurs, telles que le texte, les erreurs et les texte du message de l’interface utilisateur. Remplacez-les par un appel à la <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> méthode à l’aide de la syntaxe suivante :  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Appuyez sur la touche F5 pour générer et exécuter l’application.  
  
13. Dans SharePoint, modifiez la langue d’affichage à partir de la valeur par défaut.  
  
     Les chaînes localisées s’affichent dans l’application. Pour afficher les ressources localisées, le serveur SharePoint doit disposer d’un module linguistique qui correspond à la culture du fichier de ressources.  
  
## <a name="see-also"></a>Voir aussi  
 [Localisation de Solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md)   
 [Comment : localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Guide pratique pour ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)  
  
  