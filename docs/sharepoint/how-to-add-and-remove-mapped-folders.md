---
title: 'Comment : ajouter et supprimer des dossiers mappés | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.MappedFolder
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, mapped folders
- mapped folders [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8cf70cf7f69091590c950d6b5eccd6393708e7c9
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767207"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Comment : ajouter et supprimer des dossiers mappés
  Certains dossiers fréquemment employés dans SharePoint, tels que les Images et dispositions, sont profondément imbriqué dans la hiérarchie des fichiers. Vous pouvez mapper ces dossiers dans un projet SharePoint pour y accéder plus facilement. Dossiers mappés sont des dossiers du projet SharePoint qui correspondent à l’emplacement physique des fichiers dans l’installation de SharePoint Server.  
  
 Lorsque vous déployez une application SharePoint, le contenu du dossier mappé et tous ses sous-dossiers sont copiées par le package de solution (.wsp) sur le serveur qui exécute SharePoint à l’emplacement spécifié dans l’arborescence des dossiers SharePoint. Cet emplacement est déterminé par le **emplacement de déploiement** propriété est définie pour le dossier mappé. Tous les sous-dossiers du dossier mappé sont relatifs **emplacement de déploiement** du dossier mappé. Notez que la **emplacement de déploiement** propriété, pas le nom du dossier mappé, détermine où les éléments sont déployés.  
 Vous pouvez ajouter des dossiers mappés à un projet à l’aide des commandes sur la barre de menus ou le menu contextuel pour le projet. Vous pouvez utiliser la **un dossier mappé SharePoint d’ajouter des « Images »** et **SharePoint ajouter « Dispositions » dossier** commandes permettant d’ajouter ceux mappés dossiers les plus souvent utilisés. Vous pouvez mapper les autres dossiers SharePoint disponibles à votre projet à l’aide de la **ajouter un dossier mappé SharePoint** de commande dans le menu contextuel, puis en spécifiant les dossiers dans le **ajouter un dossier mappé SharePoint** boîte de dialogue.  
  
## <a name="add-mapped-folders-to-a-project"></a>Ajouter des dossiers mappés à un projet  
 La procédure suivante décrit comment ajouter les deux dossiers mappés à un projet de composant WebPart visual. Pour commencer, vous créez un projet de composant WebPart visual.  
  
#### <a name="to-add-mapped-folders-to-a-project"></a>Pour ajouter des dossiers mappés à un projet  
  
1.  Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue zone, développez le le **Visual Basic** ou **Visual C#** nœud, développez le **Office/SharePoint** nœud, puis Choisissez le **Solutions SharePoint** nœud.  
  
3.  Dans la liste des modèles de projet, choisissez la **2013 Visual WebPart SharePoint** modèle.  
  
4.  Dans le **nom** , entrez **TestProject1**, puis choisissez le **OK** bouton.  
  
5.  Dans le **Assistant Personnalisation de SharePoint**, choisissez le **Terminer** bouton pour conserver les paramètres par défaut.  
  
6.  Dans **l’Explorateur de solutions**, choisissez le nœud du projet, puis, dans la barre de menus, choisissez **projet** > **un dossier mappé SharePoint d’ajouter des « Images »**.  
  
     Un dossier nommé **Images** s’affiche dans votre projet et contient un sous-dossier nommé TestProject1. Ce dossier contiendra des images pour le projet de composant WebPart visual.  
  
7.  Dans **l’Explorateur de solutions**, choisissez le nœud du projet, puis, dans la barre de menus, choisissez **projet** > **ajouter un dossier mappé SharePoint** pour afficher le  **Ajouter un dossier mappé SharePoint** boîte de dialogue.  
  
8.  Dans l’arborescence des dossiers qui sont disponibles pour le mappage, choisissez le **ressources** dossier, puis choisissez le **OK** bouton.  
  
     Un dossier nommé **ressources** s’affiche dans votre projet. Ce dossier peut stocker des éléments tels que les fichiers de ressources de chaîne. Sous-dossiers peuvent être utiles pour organiser le contenu d’un dossier mappé, mais ils ne sont pas automatiquement créés lorsque vous ajoutez un dossier mappé à l’aide de la **ajouter un dossier mappé SharePoint** commande. Pour ajouter un sous-dossier, choisissez le **ressources** dossier, puis, dans la barre de menus, choisissez **projet** > **nouveau dossier**.  
  
## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Modifier l’emplacement de déploiement d’un dossier mappé  
 Par défaut, les dossiers mappés sont ajoutés à des emplacements spécifiques par rapport à la racine installation chemin d’accès SharePoint, qui identifie le jeton {SharePointRoot}. Toutefois, vous pouvez modifier cet emplacement en modifiant le **emplacement de déploiement** propriété du dossier mappé. Chaque dossier mappé a sa propre **emplacement de déploiement** propriété.  
  
#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Pour modifier l’emplacement de déploiement d’un dossier mappé  
  
1.  Dans le projet que vous avez créé précédemment, choisissez un dossier mappé.  
  
2.  Dans le **propriétés** fenêtre, choisissez le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile")) bouton sur le **déploiement emplacement** propriété.  
  
3.  Dans le **ajouter un dossier mappé SharePoint** boîte de dialogue, accédez au dossier auquel vous souhaitez que le dossier mappé au point.  
  
4.  Choisissez le nœud, puis le **OK** bouton.  
  
## <a name="rename-or-remove-mapped-folders"></a>Renommer ou supprimer des dossiers mappés  
  
#### <a name="to-rename-or-remove-a-mapped-folder"></a>Pour renommer ou supprimer un dossier mappé  
  
1.  Dans le projet que vous avez créé précédemment, choisissez un dossier mappé.  
  
2.  Pour renommer le dossier mappé, ouvrez le menu contextuel, choisissez **renommer**, entrez le nouveau nom, puis appuyez sur ENTRÉE.  
  
     En guise d’alternative, vous pouvez choisir le dossier mappé que vous souhaitez renommer, ouvrez le **propriétés** fenêtre, puis définissez la valeur de la **nom du dossier** le nouveau nom de propriété.  
  
3.  Pour supprimer un dossier mappé à partir du projet, ouvrez le menu contextuel, choisissez **supprimer**, puis choisissez le **OK** bouton dans la boîte de dialogue Confirmer la suppression.  
  
## <a name="see-also"></a>Voir aussi
 [Développement de solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
