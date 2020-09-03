---
title: 'Comment : localiser du code | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 6c1963ff0b6ef317dfa1a2c8154a1628710dc562
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016690"
---
# <a name="how-to-localize-code"></a>Comment : localiser du code
  Le code non localisé utilise des valeurs de chaîne codées en dur. Pour localiser des chaînes de code, remplacez-les par des appels à <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> , qui est une méthode qui fait référence aux ressources localisées.

## <a name="localize-code"></a>Localiser du code

#### <a name="to-localize-code"></a>Pour localiser du code

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel d’un élément de projet, puis choisissez **Ajouter**un  >  **module**.

     Choisissez le modèle de **fichier de ressources** .

    > [!NOTE]
    > Veillez à ajouter le fichier de ressources à un élément de projet SharePoint afin que la propriété type de déploiement soit disponible. Cette propriété est requise plus loin dans cette procédure.

2. Donnez au fichier de ressources de langue par défaut le nom de votre choix, ajouté avec une extension *. resx* , par exemple *MyAppResources. resx*.

3. Répétez les étapes 1 et 2 pour ajouter des fichiers de ressources distincts à l’élément de projet SharePoint : un pour chaque langue localisée.

     Utilisez le même nom de base pour chaque fichier de ressources localisé, mais ajoutez l’ID de culture. Par exemple, nommez une ressource localisée allemande *MyAppResources.de-de. resx*.

4. Ouvrez chaque fichier de ressources et ajoutez des chaînes localisées. Utilisez les mêmes ID de chaîne dans chaque fichier.

5. Modifiez la valeur de la propriété **type de déploiement** de chaque fichier de ressources en **AppGlobalResource** de façon à ce que chaque fichier soit déployé dans le dossier App_GlobalResources du serveur.

6. Laissez la valeur de la propriété **action de génération** de chaque fichier en tant que **ressource incorporée**.

     Les ressources incorporées sont compilées dans la DLL du projet.

7. Générez le projet pour créer les dll satellites des ressources.

8. Dans le **Concepteur de packages**, choisissez l’onglet **avancé** , puis ajoutez l’assembly satellite.

9. Dans la zone **emplacement** , ajoutez un dossier de l’ID de culture au chemin d’accès de l’emplacement, par exemple *de-de \\ \<Project Item Name>.resources.dll*.

10. Si votre solution ne fait pas déjà référence à l’assembly System. Web, ajoutez une référence à celui-ci et ajoutez une directive dans votre code à <xref:System.Web> .

11. Recherchez toutes les chaînes codées en dur dans votre code qui sont visibles par les utilisateurs, telles que le texte de l’interface utilisateur, les erreurs et le texte du message. Remplacez-les par un appel à la <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> méthode à l’aide de la syntaxe suivante :

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. Appuyez sur la touche **F5** pour générer et exécuter l’application.

13. Dans SharePoint, modifiez la langue d’affichage par défaut.

     Les chaînes localisées s’affichent dans l’application. Pour afficher les ressources localisées, le serveur SharePoint doit disposer d’un module linguistique qui correspond à la culture du fichier de ressources.

## <a name="see-also"></a>Voir aussi
- [Localiser des solutions SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Comment : localiser une fonctionnalité](../sharepoint/how-to-localize-a-feature.md)
- [Comment : localiser le balisage ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Comment : ajouter un fichier de ressources](../sharepoint/how-to-add-a-resource-file.md)
