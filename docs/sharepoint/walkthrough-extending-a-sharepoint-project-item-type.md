---
title: "Walkthrough: Extending a SharePoint Project Item Type"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 1cea4e0f-ce33-4cd7-a664-800184865456
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Walkthrough: Extending a SharePoint Project Item Type
  Vous pouvez utiliser l'élément de projet **Modèle BDC \(Business Data Connectivity** afin de créer un modèle pour le service BDC dans SharePoint.  Par défaut, lorsque vous créez un modèle à l'aide de cet élément de projet, les données du modèle ne sont pas présentées aux utilisateurs.  Pour qu'ils puissent consulter les données, vous êtes tenu de générer une liste externe dans SharePoint.  
  
 Au cours de cette procédure, vous allez créer une extension pour l'élément de projet **Modèle de connectivité de données métiers**.  Les développeurs peuvent tirer parti de cette extension pour créer une liste externe au sein de leur projet dans le but d'afficher les données dans le modèle BDC.  Cette procédure pas à pas présente les tâches suivantes :  
  
-   Création d'une extension Visual Studio qui exécute deux tâches principales :  
  
    -   Elle établit une liste externe présentant les données dans un modèle BDC.  L'extension utilise le modèle d'objet pour le système de projet SharePoint afin de générer un fichier Elements.xml qui définit la liste.  Elle ajoute, en outre, le fichier au projet afin de le déployer en même temps que le modèle BDC.  
  
    -   Elle ajoute un élément de menu contextuel aux éléments de projet **Modèle de connectivité de données métiers** dans l'**Explorateur de solutions**.  Les développeurs peuvent cliquer sur cet élément de menu pour générer une liste externe pour le modèle BDC.  
  
-   Génération d'un package Visual Studio Extension \(VSIX\) pour déployer l'assembly de l'extension.  
  
-   Test de l'extension.  
  
## Composants requis  
 Vous avez besoin des composants suivants sur l'ordinateur de développement pour terminer cette procédure pas à pas :  
  
-   Éditions de Microsoft Windows, SharePoint et Visual Studio prises en charge.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  Cette procédure pas à pas utilise le modèle **Projet VSIX** du Kit de développement logiciel \(SDK\) pour créer un package VSIX afin de déployer l'élément de projet.  Pour plus d'informations, consultez [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Une connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer cette procédure pas à pas :  
  
-   Service BDC dans [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)].  Pour plus d'informations et d'exemples, consultez [Architecture BDC](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
-   Schéma XML pour les modèles BDC.  Pour plus d'informations, consultez [Infrastructure de modèle BDC](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## Création du projet  
 Pour exécuter cette procédure pas à pas, vous devez créer deux projets :  
  
-   Un projet VSIX pour créer le package VSIX afin de déployer l'extension d'élément de projet.  
  
-   Un projet de bibliothèque de classes qui implémente l'extension d'élément de projet.  
  
 Démarrez la procédure pas à pas en créant les projets.  
  
#### Pour créer le projet VSIX  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
3.  Dans la boîte de dialogue **Nouveau projet**, développez les nœuds **Visual C\#** ou **Visual Basic**, puis sélectionnez le nœud **Extensibilité**.  
  
    > [!NOTE]  
    >  Le nœud **Extensibilité** est disponible uniquement si vous installez le Kit de développement logiciel de Visual Studio.  Pour plus d'informations, consultez la section des composants requis plus haut dans cette rubrique.  
  
4.  Dans la liste en haut de la boîte de dialogue **Nouveau projet**, sélectionnez **.NET Framework 4.5**.  
  
     Les extensions des outils SharePoint nécessitent des fonctionnalités dans cette version du .NET Framework.  
  
5.  Choisissez le modèle **VSIX Project**.  
  
6.  Dans la zone de texte **Nom**, entrez **GenerateExternalDataLists**, puis choisissez le bouton **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **GenerateExternalDataLists** à l'**Explorateur de solutions**.  
  
7.  Si le fichier source.extension.vsixmanifest ne s'ouvre pas automatiquement, ouvrez le menu contextuel dans le projet GenerateExternalDataLists, puis choisissez **Ouvrir**  
  
8.  Vérifiez que le fichier source.extension.vsixmanifest a une entrée non vide \(entrez Contoso\) pour le champ d'auteur, enregistrez le fichier, puis fermez\-le.  
  
#### Pour créer le projet d'extension  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution **GenerateExternalDataLists**, choisissez **Ajouter**, puis choisissez **Nouveau Projet**.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, le nœud de la solution s'affiche dans l'**Explorateur de solutions** à condition d'avoir activé la case à cocher **Toujours afficher la solution** dans la [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Dans la boîte de dialogue **Ajouter un nouveau projet**, développez les nœuds **Visual C\#** ou **Visual Basic**, puis cliquez sur le nœud **Windows**.  
  
3.  Dans la zone de liste déroulante en haut de la boîte de dialogue, sélectionnez **.NET Framework 4.5**.  
  
4.  Dans la liste des modèles de projet, sélectionnez **Bibliothèque de classes**.  
  
5.  Dans la zone de texte **Nom**, entrez **BdcProjectItemExtension**, puis choisissez le bouton **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **BdcProjectItemExtension** à la solution et ouvre le fichier de code Class1 par défaut.  
  
6.  Supprimez le fichier de code Class1 du projet.  
  
## Configuration du projet d'extension  
 Avant d'écrire le code pour créer l'extension d'élément de projet, ajoutez les fichiers de code et les références d'assembly au projet d'extension.  
  
#### Pour configurer le projet  
  
1.  Dans le projet BdcProjectItemExtension, ajoutez deux fichiers de code portant les noms suivants :  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  Sélectionnez le projet BdcProjectItemExtension, puis, dans la barre de menus, sélectionnez **Projet**, **Ajouter une référence**.  
  
3.  Sous le nœud **Assemblys**, choisissez le nœud **Framework**, et sélectionnez la case à cocher pour chacun des assemblys suivants :  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  Sous le nœud **Assemblys**, choisissez le nœud **Extensions**, puis activez la case à cocher de l'assembly suivant :  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Cliquez sur le bouton **OK**.  
  
## Définition de l'extension d'élément de projet  
 Créez une classe qui définit l'extension pour l'élément de projet **Modèle de connectivité de données métiers**.  Pour définir l'extension, la classe implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  Mettez en œuvre cette interface chaque fois que vous souhaitez étendre un type d'élément de projet existant.  
  
#### Pour définir l'extension d'élément de projet  
  
1.  Collez le code suivant dans le fichier de code ProjectItemExtension.  
  
    > [!NOTE]  
    >  Après l'ajout de ce code, le projet comportera des erreurs de compilation.  Ces erreurs disparaîtront lorsque vous ajouterez du code dans les étapes ultérieures.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/cs/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/vb/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## Création des listes de données externes  
 Ajoutez une définition partielle de la classe `GenerateExternalDataListsExtension` prévue pour créer une liste de données externes pour chaque entité dans le modèle BDC.  Pour établir la liste de données externes, ce code commence par lire les données d'entité dans le modèle BDC en analysant les données XML du fichier du modèle BDC.  Il génère ensuite une instance de liste basée sur le modèle BDC et ajoute cette instance de liste au projet.  
  
#### Pour créer les listes de données externes  
  
1.  Collez l'exemple de code suivant dans le fichier GenerateExternalDataLists.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/cs/bdcprojectitemextension/generateexternaldatalists.cs#2)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.bdcgenerateexternaldatalists/vb/bdcprojectitemextension/generateexternaldatalists.vb#2)]  
  
## Point de contrôle  
 À ce stade de la procédure, l'intégralité du code de l'extension de l'élément de projet fait désormais partie du projet.  Générez la solution afin de garantir sa compilation sans erreur.  
  
#### Pour générer la solution  
  
1.  Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
## Création d'un package VSIX pour déployer l'extension d'élément de projet  
 Pour déployer l'extension, utilisez le projet VSIX inclus dans votre solution pour créer un package VSIX.  En premier lieu, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest qui est inclus dans le projet VSIX.  Ensuite, créez le package VSIX en générant la solution.  
  
#### Pour configurer et créer le package VSIX  
  
1.  Dans l' **Explorateur de Solutions**, ouvrez le menu contextuel pour le fichier source.extension.vsixmanifest dans le projet GenerateExternalDataLists project, et cliquez sur **Ouvrir**.  
  
     Visual Studio ouvre le fichier dans l'éditeur de manifeste.  Le fichier source.extension.vsixmanifest est la base du fichier extension.vsixmanifest requis par tous les packages VSIX.  Pour plus d'informations sur ce fichier, consultez [Référence de schéma d'extensions VSIX](http://msdn.microsoft.com/fr-fr/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Dans la zone **Nom du produit**, tapez **Générateur de liste de données externe**.  
  
3.  Dans la zone **Auteur**, tapez **Contoso**.  
  
4.  Dans la zone **Description**, tapez **Extension pour les éléments de projet Modèle de connectivité de données métiers permettant de générer des listes de données externes**.  
  
5.  Sous l'onglet **Composants** de l'éditeur, choisissez le bouton **Nouveau**.  
  
     La boîte de dialogue **Ajouter un nouveau composant** s'affiche.  
  
6.  Dans la liste **Type**, choisissez **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à l'élément `MefComponent` dans le fichier extension.vsixmanifest.  Cet élément spécifie le nom d'un assembly d'extension dans le package VSIX.  Pour plus d'informations, consultez [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/fr-fr/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Dans la liste **Source**, choisissez **Un projet dans la solution actuelle**.  
  
8.  Dans la liste **Projet**, choisissez **BdcProjectItemExtension**, puis choisissez le bouton **OK**.  
  
9. Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
10. Faites en sorte que le projet compile et se génère sans erreurs.  
  
11. Assurez\-vous que le dossier de sortie de la génération pour le projet GenerateExternalDataLists contient maintenant le fichier GenerateExternalDataLists.vsix.  
  
     Par défaut, le dossier de sortie de génération est le dossier ..\\bin\\Debug dans le dossier qui contient votre fichier projet.  
  
## Test de l'extension d'élément de projet  
 Vous êtes maintenant prêt à tester l'extension d'élément de projet.  Tout d'abord, commencez à déboguer le projet d'extension dans l'instance expérimentale de Visual Studio.  Utilisez ensuite l'extension dans l'instance expérimentale de Visual Studio pour générer une liste externe pour un modèle BDC.  Pour finir, ouvrez la liste externe sur le site SharePoint pour vérifier si elle fonctionne comme prévu.  
  
#### Pour démarrer le débogage de l'extension  
  
1.  Si nécessaire, redémarrez Visual Studio avec les droits d'administrateur, et ouvrez la solution GenerateExternalDataLists.  
  
2.  Dans le projet BdcProjectItemExtension, ouvrez le fichier de code ProjectItemExtension et ajoutez un point d'arrêt au niveau de la ligne de code dans la méthode `Initialize`.  
  
3.  Ouvrez le fichier de code GenerateExternalDataLists et ajoutez un point d'arrêt au niveau de la première ligne de code dans la méthode `GenerateExternalDataLists_Execute`.  
  
4.  Démarrez le débogage en appuyant sur la touche F5 ou, dans la barre de menus, choisissez **Déboguer**, **Démarrer le débogage**.  
  
     Visual Studio installe l'extension sous %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\10.0Exp\\Extensions\\Contoso\\Générateur de liste de données externe\\1.0 et démarre une instance expérimentale de Visual Studio.  Vous testerez l'élément de projet dans cette instance de Visual Studio.  
  
#### Pour tester l'extension  
  
1.  Dans l'instance expérimentale de Visual Studio, dans la barre de menu, sélectionnez **Fichier**, **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau Projet**, développez le nœud **Modèles**, puis le nœud **Visual C\#**, et le nœud **SharePoint**, et choisissez **2010**.  
  
3.  Dans la zone de liste déroulante en haut de la boîte de dialogue, vérifiez que **.NET Framework 3.5** est sélectionné.  Les projets pour [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] requièrent cette version du .NET Framework.  
  
4.  Dans la liste des modèles de projet, cliquez sur **Projet SharePoint 2010**.  
  
5.  Dans la zone de texte **Nom**, entrez **SharePointProjectTestBDC**, puis choisissez le bouton **OK**.  
  
6.  Dans l'Assistant Personnalisation de SharePoint, entrez l'URL du site que vous souhaitez utiliser pour le débogage, sélectionnez **Déployer en tant que solution de batterie**, puis cliquez sur le bouton **Terminer**.  
  
7.  Ouvrez le menu contextuel pour le projet SharePointProjectTestBDC, sélectionnez **Ajouter**, puis **Nouvel élément**.  
  
8.  Dans la boîte de dialogue **Ajoutez NewItem – SharePointProjectTestBDC**, développez le nœud de langue installée, et développez le nœud **SharePoint**.  
  
9. Sélectionnez le nœud **2010**, puis choisissez le modèle **Modèle de connectivité de données métiers \(solution de batterie uniquement\)**.  
  
10. Dans la boîte **Nom**, entrez **TestBDCModel**, et sélectionnez le bouton **Ajouter**.  
  
11. Assurez\-vous que le code dans l'autre instance de Visual Studio s'arrête au niveau du point d'arrêt que vous avez défini précédemment dans la méthode `Initialize` du fichier de code ProjectItemExtension.  
  
12. Dans l'instance arrêtée Visual Studio, appuyez sur la touche **F5**, ou sur la barre de menus, sélectionnez **Déboguer**, **Continuer** pour continuer de déboguer le projet.  
  
13. Dans l'instance expérimentale de Visual Studio, appuyez sur la touche **F5**, ou, dans la barre de menus, sélectionnez **Déboguer**, **Démarrer le débogage** pour générer, déployer, et exécuter le projet **TestBDCModel**.  
  
     Le navigateur Web s'ouvre à la page par défaut du site SharePoint spécifié pour le débogage.  
  
14. Vérifiez si la section **Listes** dans la zone Lancement rapide ne contient pas déjà une liste basée sur le modèle BDC par défaut dans le projet.  Vous devez commencer par créer une liste de données externes, via l'interface utilisateur SharePoint ou via l'extension d'élément de projet.  
  
15. Fermez le navigateur Web.  
  
16. Dans l'instance de Visual Studio dans laquelle le projet TestModèleBDC est ouvert, ouvrez le menu contextuel du noeud **TestBDCModel** dans l' **Explorateur de solutions**, puis cliquez sur **Générer une liste de données externes**.  
  
17. Assurez\-vous que le code dans l'autre instance de Visual Studio s'arrête au niveau du point d'arrêt que vous avez défini précédemment dans la méthode `GenerateExternalDataLists_Execute`.  Sélectionnez la clé **F5**, ou, dans la barre de menus, sélectionnez **Déboguer**, **Continuer** pour continuer de déboguer le projet.  
  
18. L'instance expérimentale de Visual Studio ajoute une instance de liste nommée **Entity1DataList** au projet TestModèleBDC et génère une fonctionnalité appelée **Feature2** pour l'instance de liste.  
  
19. Appuyez sur **F5**, ou, dans la barre de menus, sélectionnez **Déboguer**, **Démarrer le débogage** pour générer, déployer, et exécuter le projet TestModèleBDC.  
  
     Le navigateur Web s'ouvre à la page par défaut du site SharePoint utilisé pour le débogage.  
  
20. Dans la section **Listes** de la zone de lancement rapide, sélectionnez la liste **Entity1DataList**.  
  
21. Assurez\-vous que la liste contient des colonnes nommées Identifier1 et Message, et un élément avec une valeur Identifier1 équivalente à 0 et une valeur Message équivalente à Hello World.  
  
     Le modèle de projet **Modèle de Connectivité de Données Métier** génère le modèle BDC par défaut qui fournit l'ensemble de ces données.  
  
22. Fermez le navigateur Web.  
  
## Nettoyage de l'ordinateur de développement  
 Une fois le test de l'extension d'élément de projet terminé, supprimez la liste externe et le modèle BDC du site SharePoint et faites de même avec l'extension d'élément de projet dans Visual Studio.  
  
#### Pour supprimer la liste de données externe du site SharePoint  
  
1.  Dans la zone Lancement rapide du site SharePoint, cliquez sur la liste **Entity1DataList**.  
  
2.  Dans le Ruban du site SharePoint, cliquez sur l'onglet **Liste**.  
  
3.  Dans l'onglet **Liste**, dans le groupe **Paramètres**, sélectionnez **Paramètres de liste**.  
  
4.  Sous **Autorisations et gestion**, choisissez **Supprimer cette liste**, puis choisissez **OK** pour confirmer l'envoi de la liste à la Corbeille.  
  
5.  Fermez le navigateur Web.  
  
#### Pour supprimer le modèle BDC du site SharePoint  
  
1.  Dans l'instance expérimentale de Visual Studio, dans la barre de menu, sélectionnez **Générer**, puis **Retirer**.  
  
     Visual Studio supprime le modèle BDC du site SharePoint.  
  
#### Pour supprimer l'extension d'élément de projet de Visual Studio  
  
1.  Dans l'instance expérimentale de Visual Studio, dans la barre de menu, cliquez sur **Outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s'ouvre.  
  
2.  Dans la liste d'extensions, cliquez sur **Générateur de liste de données externe**, puis sur **Désinstaller**.  
  
3.  Dans la boîte de dialogue qui s'affiche, cliquez sur **Oui** pour confirmer que vous voulez désinstaller l'extension.  
  
4.  Cliquez sur **Redémarrer maintenant** pour terminer la désinstallation.  
  
5.  Fermez les deux instances de Visual Studio \(l'instance expérimentale et l'instance de Visual Studio dans laquelle la solution GenerateExternalDataLists est ouverte\).  
  
## Voir aussi  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Création d'un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Conception d'un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  