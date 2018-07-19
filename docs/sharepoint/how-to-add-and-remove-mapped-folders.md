---
title: 'Comment : ajouter et supprimer des dossiers mappés | Microsoft Docs'
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
ms.openlocfilehash: fe9868a9909dbb78bf510f18584472520948d6f9
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757646"
---
# <a name="how-to-add-and-remove-mapped-folders"></a>Comment : ajouter et supprimer des dossiers mappés
  Certains dossiers fréquemment employés dans SharePoint, tels que les Images et les dispositions, sont profondément imbriqués dans la hiérarchie des fichiers. Vous pouvez mapper ces dossiers dans un projet SharePoint pour y accéder plus facilement. Dossiers mappés sont des dossiers du projet SharePoint qui correspondent à l’emplacement physique des fichiers dans l’installation de SharePoint Server.  
  
 Lorsque vous déployez une application SharePoint, le contenu du dossier mappé et tous ses sous-dossiers sont copiés par le package de solution (.wsp) sur le serveur qui exécute SharePoint à l’emplacement spécifié dans l’arborescence de dossiers SharePoint. Cet emplacement est déterminé par le **emplacement de déploiement** propriété qui est définie pour le dossier mappé. Tous les sous-dossiers du dossier mappé sont reliés **emplacement de déploiement** du dossier mappé. Notez que le **emplacement de déploiement** propriété, pas le nom de dossier mappé, détermine où les éléments sont déployés.  
 Vous pouvez ajouter des dossiers mappés à un projet à l’aide des commandes sur la barre de menus ou le menu contextuel pour le projet. Vous pouvez utiliser la **un dossier mappé SharePoint ajouter « Images »** et **ajouter SharePoint « Dispositions » dossier** commandes pour ajouter ceux mappés dossiers les plus souvent utilisés. Vous pouvez mapper les autres dossiers SharePoint disponibles à votre projet à l’aide de la **ajouter un dossier mappé SharePoint** commande dans le menu contextuel, puis en spécifiant les dossiers dans le **ajouter un dossier mappé SharePoint** boîte de dialogue.  
  
## <a name="add-mapped-folders-to-a-project"></a>Ajouter des dossiers mappés à un projet  
 La procédure suivante décrit comment ajouter deux dossiers mappés à un projet de composant WebPart visuel. Pour commencer, vous créez un projet de composant WebPart visuel.  
  
#### <a name="to-add-mapped-folders-to-a-project"></a>Pour ajouter des dossiers mappés à un projet  
  
1.  Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue zone, développez le le **Visual Basic** ou **Visual C#** nœud, développez le **Office/SharePoint** nœud, puis Choisissez le **Solutions SharePoint** nœud.  
  
3.  Dans la liste des modèles de projet, choisissez le **2013 Visual WebPart SharePoint** modèle.  
  
4.  Dans le **nom** , entrez **TestProject1**, puis choisissez le **OK** bouton.  
  
5.  Dans le **Assistant Personnalisation de SharePoint**, choisissez le **Terminer** bouton pour conserver les paramètres par défaut.  
  
6.  Dans **l’Explorateur de solutions**, choisissez le nœud du projet, puis, dans la barre de menus, choisissez **projet** > **un dossier mappé SharePoint ajouter « Images »**.  
  
     Un dossier nommé **Images** s’affiche dans votre projet et contient un sous-dossier nommé TestProject1. Ce dossier mappé contient des images pour le projet de composant WebPart visuel.  
  
7.  Dans **l’Explorateur de solutions**, choisissez le nœud du projet, puis, dans la barre de menus, choisissez **projet** > **ajouter un dossier mappé SharePoint** pour afficher le  **Ajouter un dossier mappé SharePoint** boîte de dialogue.  
  
8.  Dans l’arborescence de dossiers qui sont disponibles pour le mappage, choisissez le **ressources** dossier, puis choisissez le **OK** bouton.  
  
     Un dossier nommé **ressources** s’affiche dans votre projet. Ce dossier peut stocker des éléments tels que les fichiers de ressources de chaîne. Sous-dossiers peuvent être utiles pour organiser le contenu d’un dossier mappé, mais elles ne sont pas automatiquement créées lorsque vous ajoutez un dossier mappé à l’aide de la **ajouter un dossier mappé SharePoint** commande. Pour ajouter un sous-dossier, choisissez le **ressources** dossier, puis, dans la barre de menus, choisissez **projet** > **nouveau dossier**.  
  
## <a name="change-the-deployment-location-of-a-mapped-folder"></a>Modifier l’emplacement de déploiement d’un dossier mappé  
 Par défaut, les dossiers mappés sont ajoutés à des emplacements spécifiques par rapport au chemin d’installation racine SharePoint, ce qui le jeton \<SharePointRoot > désigne. Toutefois, vous pouvez modifier cet emplacement en modifiant le **emplacement de déploiement** propriété du dossier mappé. Chaque dossier mappé a sa propre **emplacement de déploiement** propriété.  
  
#### <a name="to-change-the-deployment-location-of-a-mapped-folder"></a>Pour modifier l’emplacement de déploiement d’un dossier mappé  
  
1.  Dans le projet que vous avez créé précédemment, choisissez un dossier mappé.  
  
2.  Dans le **propriétés** fenêtre, choisissez le bouton de sélection (![ellipse de concepteur ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile")) situé dans le **déploiement emplacement** propriété.  
  
3.  Dans le **ajouter un dossier mappé SharePoint** boîte de dialogue, accédez au dossier auquel vous souhaitez le dossier mappé pour qu’il pointe.  
  
4.  Choisissez le nœud, puis le **OK** bouton.  
  
## <a name="rename-or-remove-mapped-folders"></a>Renommer ou supprimer des dossiers mappés  
  
#### <a name="to-rename-or-remove-a-mapped-folder"></a>Pour renommer ou supprimer un dossier mappé  
  
1.  Dans le projet que vous avez créé précédemment, choisissez un dossier mappé.  
  
2.  Pour renommer le dossier mappé, ouvrez son menu contextuel, choisissez **renommer**, entrez le nouveau nom, puis appuyez sur ENTRÉE.  
  
     Comme alternative, vous pouvez choisir le dossier mappé que vous souhaitez renommer, ouvrez le **propriétés** fenêtre, puis définissez la valeur de la **nom du dossier** propriété vers le nouveau nom.  
  
3.  Pour supprimer un dossier mappé à partir du projet, ouvrez son menu contextuel, choisissez **supprimer**, puis choisissez le **OK** bouton dans la boîte de dialogue Confirmer la suppression.  
  
## <a name="see-also"></a>Voir aussi
 [Développer des solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
