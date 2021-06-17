---
title: 'Procédure : ajouter et supprimer des dossiers mappés | Microsoft Docs'
description: Ajoutez et supprimez des dossiers mappés à un projet dans SharePoint.  Modifier l’emplacement de déploiement d’un dossier mappé. Renommez ou supprimez des dossiers mappés.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a9b74ba786c9d1104fd507442d959e75afb17bf2
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112418"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Procédure : ajouter et supprimer des dossiers mappés

  Certains dossiers couramment utilisés dans SharePoint, tels que les images et les mises en page, sont profondément incorporés dans la hiérarchie des fichiers. Vous pouvez mapper ces dossiers à un projet SharePoint pour y accéder plus facilement. Les dossiers mappés sont des dossiers du projet SharePoint qui correspondent à l’emplacement physique des fichiers dans l’installation de SharePoint Server.

 Lorsque vous déployez une application SharePoint, le contenu du dossier mappé et de tous ses sous-dossiers est copié par le package de solution (. wsp) sur le serveur qui exécute SharePoint à l’emplacement spécifié dans l’arborescence de dossiers SharePoint. Cet emplacement est déterminé par la propriété d' **emplacement de déploiement** définie pour le dossier mappé. Tous les sous-dossiers du dossier mappé sont relatifs à l' **emplacement de déploiement** du dossier mappé. Notez que la propriété d' **emplacement de déploiement** , et non le nom du dossier mappé, détermine où les éléments sont déployés.
Vous pouvez ajouter des dossiers mappés à un projet à l’aide des commandes de la barre de menus ou du menu contextuel du projet. Vous pouvez utiliser le **dossier mappé « images » SharePoint** et ajouter des commandes de **dossier « dispositions » SharePoint** pour ajouter ces dossiers mappés qui sont utilisés le plus souvent. Vous pouvez mapper l’un des autres dossiers SharePoint disponibles à votre projet à l’aide de la commande **Ajouter un dossier mappé SharePoint** du menu contextuel, puis en spécifiant les dossiers dans la boîte de dialogue **Ajouter un dossier mappé SharePoint** .

## <a name="add-mapped-folders-to-a-project"></a>Ajouter des dossiers mappés à un projet

 La procédure suivante décrit comment ajouter deux dossiers mappés à un projet de composant Visual Web part. Pour commencer, vous créez un projet de composant Visual Web part.

## <a name="to-add-mapped-folders-to-a-project"></a>Pour ajouter des dossiers mappés à un projet

1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.
::: moniker range="=vs-2017"
2. Dans la boîte de dialogue **nouveau projet** , développez le nœud **Visual Basic** ou **Visual C#** , développez le nœud **Office/SharePoint** , puis choisissez le nœud **solutions SharePoint** .

3. Dans la liste des modèles de projet, choisissez le modèle **Visual Web Part SharePoint 2013** .

4. Dans la zone **nom** , entrez **TestProject1**, puis cliquez sur le bouton **OK** .
::: moniker-end
::: moniker range=">=vs-2019"
2. Dans la boîte de dialogue **créer un nouveau projet** , sélectionnez le *composant Visual Web part de SharePoint** pour la version particulière de SharePoint que vous avez installée. Par exemple, si vous avez SharePoint 2019 install, sélectionnez le modèle **Visual Web part sharepoint 2019** .
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. Dans la zone **nom** , entrez **TestProject1**
4. Cliquez ensuite sur le bouton **créer** .
::: moniker-end

5. Dans l' **Assistant Personnalisation de SharePoint**, choisissez le bouton **Terminer** pour conserver les paramètres par défaut.

6. Dans **Explorateur de solutions**, choisissez le nœud de projet, puis, dans la barre de menus, choisissez **projet**  >  **Ajouter un dossier mappé SharePoint « images »**.

     Un dossier nommé **images** s’affiche dans votre projet et contient un sous-dossier nommé TestProject1. Ce dossier mappé contient des images pour le projet de composant Visual Web part.

7. Dans **Explorateur de solutions**, choisissez le nœud de projet, puis dans la barre de menus, choisissez **projet**  >  **Ajouter un dossier mappé SharePoint** pour afficher la boîte de dialogue **Ajouter un dossier mappé SharePoint** .

8. Dans l’arborescence des dossiers qui sont disponibles pour le mappage, choisissez le dossier **ressources** , puis choisissez le bouton **OK** .

     Un dossier nommé **Resources** s’affiche dans votre projet. Ce dossier peut stocker des éléments tels que des fichiers de ressources de type chaîne. Les sous-dossiers peuvent être utiles pour organiser le contenu d’un dossier mappé, mais ils ne sont pas créés automatiquement lorsque vous ajoutez un dossier mappé à l’aide de la commande **Ajouter un dossier mappé SharePoint** . Pour ajouter un sous-dossier, choisissez le dossier **ressources** , puis, dans la barre de menus, choisissez **projet**  >  **nouveau dossier**.

## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Modifier l’emplacement de déploiement d’un dossier mappé

 Par défaut, les dossiers mappés sont ajoutés à des emplacements spécifiques par rapport au chemin d’installation racine SharePoint, que le jeton \<SharePointRoot> désigne. Toutefois, vous pouvez modifier cet emplacement en modifiant la propriété d' **emplacement de déploiement** du dossier mappé. Chaque dossier mappé possède sa propre propriété d' **emplacement de déploiement** .

### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Pour modifier l’emplacement de déploiement d’un dossier mappé

1. Dans le projet que vous avez créé précédemment, choisissez un dossier mappé.

2. Dans la fenêtre **Propriétés** , choisissez le bouton des points de suspension (![ellipse ASP.net Mobile designer](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")) dans la propriété **emplacement de déploiement** .

3. Dans la boîte de dialogue **Ajouter un dossier mappé SharePoint** , accédez au dossier dans lequel vous souhaitez que le dossier mappé pointe.

4. Choisissez le nœud, puis choisissez le bouton **OK** .

## <a name="rename-or-remove-mapped-folders"></a>Renommer ou supprimer des dossiers mappés

### <a name="to-rename-or-remove-a-mapped-folder"></a>Pour renommer ou supprimer un dossier mappé

1. Dans le projet que vous avez créé précédemment, choisissez un dossier mappé.

2. Pour renommer le dossier mappé, ouvrez le menu contextuel, choisissez **Renommer**, entrez le nouveau nom, puis appuyez sur la touche entrée.

     Vous pouvez également choisir le dossier mappé que vous souhaitez renommer, ouvrir la fenêtre **Propriétés** , puis définir la valeur de la propriété **nom du dossier** sur le nouveau nom.

3. Pour supprimer un dossier mappé du projet, ouvrez le menu contextuel, choisissez **supprimer**, puis choisissez le bouton **OK** dans la boîte de dialogue pour confirmer la suppression.

## <a name="see-also"></a>Voir aussi

- [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)
