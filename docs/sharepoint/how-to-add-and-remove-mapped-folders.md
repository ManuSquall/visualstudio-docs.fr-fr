---
title: "Comment&#160;: ajouter et supprimer des dossiers mapp&#233;s"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.MappedFolder"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "dossiers mappés (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, dossiers mappés"
ms.assetid: 115c8b00-7d4c-4fbe-b42c-e82dca944504
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Comment&#160;: ajouter et supprimer des dossiers mapp&#233;s
  Certains dossiers fréquemment employés dans SharePoint, tel que les dossiers Images et Dispositions, sont profondément imbriqués dans la hiérarchie des fichiers.  Il peut être intéressant, par conséquent, de mapper ces dossiers dans un projet SharePoint afin d'y accéder plus facilement.  Les dossiers mappés sont des dossiers du projet SharePoint qui correspondent à l'emplacement physique des fichiers dans le répertoire d'installation de SharePoint Server.  
  
 Lorsque vous déployez une application SharePoint, le contenu du dossier mappé et de tous ses sous\-dossiers est copié par le package de solution \(.wsp\) sur le serveur qui exécute SharePoint à l'emplacement spécifié dans l'arborescence de dossiers SharePoint.  Cet emplacement est déterminé par la propriété **Deployment Location** configurée pour le dossier mappé.  Tous les sous\-dossiers du dossier mappé sont relatifs à la propriété **Deployment Location** du dossier mappé.  C'est la propriété **Deployment Location** qui détermine le lieu de déploiement des éléments, et non le nom du dossier mappé.  
  
 Ajoutez des dossiers mappés à un projet à l'aide des commandes proposées dans la barre d'outils ou dans le menu contextuel du projet.  Utilisez les commandes **Ajoutez le dossier mappé « images » SharePoint** et **Ajoutez le dossier « dispositions » SharePoint** pour ajouter ces dossiers mappé qui sont utilisés le plus souvent.  Mappez l'un des autres dossiers disponibles SharePoint à votre projet à l'aide **Ajouter un dossier mappé SharePoint** dans le menu contextuel puis en spécifiant les dossiers dans la boîte de dialogue **Ajouter un dossier mappé SharePoint**.  
  
## Ajout de dossiers mappés à un projet  
 La procédure suivante décrit comment ajouter deux dossiers mappés à un projet de partie web visuel.  Pour démarrrer, vous créez un projet de partie web visuel.  
  
#### Pour ajouter des dossiers mappés à un projet  
  
1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, développez sous le noeud **Visual C\#** ou **Visual Basic**, développez le noeud **Office\/SharePoint**, puis choisissez le noeud **Solutions SharePoint**.  
  
3.  Dans la liste des modèles de projet, sélectionnez le modèle **Les parties visuelles web de SharePoint 2013**.  
  
4.  Dans la zone de texte **Nom**, entrez TestProject1, puis choisissez le bouton **OK**.  
  
5.  Dans l'**Assistant Personnalisation de SharePoint**, cliquez sur le bouton **Terminer** pour conserver les paramètres par défaut.  
  
6.  Dans l'**Explorateur de solutions**, choisissez le nœud du projet, dans la barre de menus, choisissez **Project**, **Add SharePoint “Images” Mapped Folder**.  
  
     Un dossier nommé **Images** apparaît dans votre projet et contient un sous\-dossier nommé TestProject1.  Ce dossier mappé contiendra les images des parties web visuelles du projet.  
  
7.  Dans l'**Explorateur de solutions**, choisissez le nœud du projet, sur la barre de menu, choisissez **Project**, **Add SharePoint Mapped Folder** pour afficher la boîte de dialogue **Project**, **Add SharePoint Mapped FolderAjouter un dossier mappé SharePoint**.  
  
8.  Dans l'arborescence des dossiers disponibles pour le mappage, sélectionnez le dossier **Ressources**, puis cliquez sur le bouton **OK**.  
  
     Un dossier nommé **Ressources** apparâit dans votre projet.  Ce dossier peut stocker des éléments tels que des fichiers de ressources de type chaîne.  Les sous\-dossiers peuvent être utiles pour organiser le contenu d'un dossier mappé, mais ils ne sont pas créés automatiquement lorsque vous ajoutez un dossier mappé à l'aide de la commande  **Ajouter un Dossier mappé SharePoint**.  Pour ajouter un sous\-dossier, choisissez le dossier **Ressources**, puis, dans la barre de menus, choisissez **Projet**, **Nouveau dossier**.  
  
## Modification de l'emplacement de déploiement d'un dossier mappé  
 Par défaut, les dossiers mappés sont ajoutés à un emplacement spécifique relatif au tracé d'installation racine de SharePoint que le jeton {SharePointRoot} symbolise.  Il est possible, cependant, de changer cet emplacement en redéfinissant la propriété **Deployment location** du dossier mappé.  Chaque dossier mappé a sa propre propriété **Deployment location**.  
  
#### Pour changer l'emplacement de déploiement d'un dossier mappé  
  
1.  Dans le projet que vous avez créé précédemment, choisissez un dossier mappé.  
  
2.  Dans la fenêtre **Propriétés**, placez le bouton de sélection \(![Bouton de sélection du concepteur ASP.NET mobile](~/docs/sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile")\) sur la propriété **Deployment location**.  
  
3.  Dans la boîte de dialogue **Ajouter un dossier mappé SharePoint**, recherchez le dossier vers lequel le dossier mappé doit renvoyer.  
  
4.  Choisissez le noeud, puis choisissez le bouton **OK**.  
  
## Modification du nom ou suppression des dossiers mappés  
  
#### Pour renommer ou supprimer un dossier mappé  
  
1.  Dans le projet que vous avez créé précédemment, choisissez un dossier mappé.  
  
2.  Pour changer le nom du dossier mappé, ouvrez son menu contextuel, choisissez **Renommer**, tapez le nouveau nom, puis appuyez sur ENTRÉE.  
  
     Vous pouvez alternativement choisir le dossier mappé à renommer, ouvrir la fenêtre **Propriétés**, puis définir la valeur de la propriété **Folder name** avec le nouveau nom.  
  
3.  Pour supprimer un dossier mappé du projet, ouvrez le menu contextuel ,choisissez **Supprimer**, puis cliquez sur **OK** dans la boîte de dialogue pour confirmer la suppression.  
  
## Voir aussi  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  