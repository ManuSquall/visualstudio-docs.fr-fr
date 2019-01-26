---
title: 'Procédure : Localiser le Code | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d61f9f0dff98d25185233fcf07bc937de3a6455
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862797"
---
# <a name="how-to-localize-code"></a>Procédure : Localiser le code
  Code non localisé utilise des valeurs de chaîne codées en dur. Pour localiser les chaînes de code, remplacez-les par des appels à <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, qui est une méthode qui fait référence à des ressources localisées.  
  
## <a name="localize-code"></a>Localiser le code  
  
#### <a name="to-localize-code"></a>Pour localiser le code  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour un élément de projet, puis choisissez **ajouter** > **Module**.  
  
     Choisissez le **fichier de ressources** modèle.  
  
    > [!NOTE]  
    >  Veillez à ajouter le fichier de ressources à un élément de projet SharePoint afin que la propriété Type de déploiement est disponible. Cette propriété est requise plus loin dans cette procédure.  
  
2.  Nommez le fichier de ressources de langue par défaut de votre choix, avec un *.resx* extension, tel que *exemple MyAppResources.resx*.  
  
3.  Répétez les étapes 1 et 2 pour ajouter des fichiers de ressources séparés à l’élément de projet SharePoint : un pour chaque langue localisée.  
  
     Utiliser le même nom de base pour chaque fichier de ressources localisé, mais ajoutez l’ID de culture. Par exemple, nom un allemand localisé ressource *MyAppResources.de-de.resx*.  
  
4.  Ouvrez chaque fichier de ressources et ajoutez des chaînes localisées. Utilisez la même chaîne ID dans chaque fichier.  
  
5.  Modifiez la valeur de la **Type de déploiement** propriété de chaque fichier de ressources à **AppGlobalResource** pour que chaque fichier à déployer sur le dossier App_GlobalResources du serveur.  
  
6.  Laissez la valeur de la **Action de génération** propriété de chaque fichier en tant que **ressource incorporée**.  
  
     Les ressources incorporées sont compilés dans les DLL du projet.  
  
7.  Générez le projet pour créer la ressource DLL satellites.  
  
8.  Dans le **Concepteur de packages**, choisissez le **avancé** onglet et ajoutez l’assembly satellite.  
  
9. Dans le **emplacement** zone, ajoutez un dossier de code de culture pour le chemin d’accès de l’emplacement, tel que *fr-fr\\\<nom d’élément de projet >. resources.dll*.  
  
10. Si votre solution ne référence pas déjà l’assembly System.Web, ajoutez une référence à celle-ci et ajoutez une directive dans votre code pour <xref:System.Web>.  
  
11. Recherchez toutes les chaînes codées en dur dans votre code qui sont visibles aux utilisateurs, telles que l’interface utilisateur texte, erreurs et texte du message. Remplacez-les par un appel à la <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> méthode à l’aide de la syntaxe suivante :  
  
    ```csharp  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Choisissez le **F5** clé pour générer et exécuter l’application.  
  
13. Dans SharePoint, modifiez la langue d’affichage à partir de la valeur par défaut.  
  
     Les chaînes localisées s’affichent dans l’application. Pour afficher les ressources localisées, le serveur SharePoint doit avoir installé un module linguistique qui correspond à la culture du fichier de ressources.  
  
## <a name="see-also"></a>Voir aussi
 [Localiser des solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Guide pratique pour Localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md)   
 [Guide pratique pour Localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Guide pratique pour Ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)  
