---
title: "Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
ms.assetid: 897d3798-42c1-4fff-b280-8b84b53d80c6
caps.latest.revision: 100
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 96
---
# Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension
  Cette procédure pas à pas explique comment appeler le modèle d'objet client SharePoint à partir d'une extension pour le nœud **Connexions SharePoint** dans l'**Explorateur de serveurs**.  Pour plus d'informations sur l'utilisation du modèle d'objet client SharePoint, consultez [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Création d'une extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ayant pour effet d'étendre le nœud **Connexions SharePoint** de l'**Explorateur de serveurs** des façons suivantes :  
  
    -   L'extension ajoute un nœud **galerie de composants WebPart** sous chaque nœud de site SharePoint dans **Explorateur de serveurs**.  Ce nouveau nœud contient les nœuds enfants représentant chaque composant WebPart dans la galerie de composants WebPart sur le site.  
  
    -   L'extension définit un nouveau type de nœud représentant une instance du composant WebPart.  Ce nouveau type de nœud constitue la base des nœuds enfants sous le nouveau nœud **Galerie de composants WebPart**.  Le nouveau type de nœud WebPart affiche les informations dans la fenêtre **Propriétés** relatives au composant WebPart que le nœud représente.  
  
-   Génération d'un package VSIX \(Visual Studio Extension\) pour déployer l'extension.  
  
-   Débogage et test de l'extension.  
  
> [!NOTE]  
>  L'extension que vous créez dans cette procédure pas \- à \- pas présente l'extension que vous créez dans [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  Cette procédure pas \- à \- pas utilise le modèle objet serveur SharePoint, mais elle effectue les tâches à l'aide de le modèle d'objet client.  
  
## Composants requis  
 Vous avez besoin des composants suivants sur l'ordinateur de développement pour terminer cette procédure pas à pas :  
  
-   Éditions prises windows, de SharePoint, et Visual Studio.  Pour plus d’informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Le kit de développement Visual Studio.  Cette procédure pas à pas se base sur le modèle **Projet VSIX** dans le Kit de développement logiciel pour créer un package VSIX nécessaire au déploiement de l'extension.  Pour plus d’informations, consultez [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Une connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer cette procédure pas à pas :  
  
-   Utilisation du modèle d'objet client SharePoint.  Pour plus d'informations, consultez [Modèle d'objet client géré \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177797).  
  
-   Composants webpart dans SharePoint.  Pour plus d'informations, consultez [Vue d'ensemble des composants WebPart](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## Création du projet  
 Pour exécuter cette procédure pas à pas, vous devez créer deux projets :  
  
-   Un projet VSIX pour créer le package VSIX pour déployer l'extension **Explorateur de serveurs** .  
  
-   Un projet de Bibliothèque de classes qui implémente l'extension **Explorateur de serveurs** .  
  
 Démarrez la procédure pas à pas en créant les projets.  
  
#### Pour créer le projet VSIX  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
3.  Dans la boîte de dialogue **Nouveau projet** , développez les nœuds **Visual C\#** ou **Visual Basic** , puis choisissez **Extensibilité**.  
  
    > [!NOTE]  
    >  Le nœud **Extensibilité** est disponible uniquement si vous installez le kit de développement Visual Studio.  Pour plus d'informations, consultez la section des composants requis plus haut dans cette rubrique.  
  
4.  En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework.  
  
     Les extensions d'outils SharePoint nécessitent des fonctionnalités dans cette version du .NET Framework.  
  
5.  Sélectionnez le modèle **projet VSIX** .  
  
6.  Dans la zone **Nom** , le type **WebPartNode**, puis choisissez le bouton **OK** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **WebPartNode** à l'**Explorateur de solutions**.  
  
#### Pour créer le projet d'extension  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution, choisissez **Ajouter**, puis choisissez **Nouveau projet**.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, le nœud de la solution s'affiche dans l'**Explorateur de solutions** à condition d'avoir activé la case à cocher **Toujours afficher la solution** dans la [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Dans la boîte de dialogue  **Nouveau projet** , développez les nœuds **Visual C\#** ou **Visual Basic** , puis choisissez **Fenêtres**.  
  
3.  En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework.  
  
4.  Dans la liste des modèles de projet, choisissez **Bibliothèque de classes**.  
  
5.  Dans la zone **Nom** , entrez **WebPartNodeExtension**, puis choisissez le bouton **OK** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **WebPartNodeExtension** à la solution et ouvre le fichier de code Class1 par défaut.  
  
6.  Supprimez le fichier de code Class1 du projet.  
  
## Configuration du projet d'extension  
 Avant d'écrire le code pour créer l'extension, vous devez ajouter des fichiers de code et des références d'assembly à votre projet, et vous devez mettre à jour l'espace de noms par défaut.  
  
#### Pour configurer le projet  
  
1.  Dans le projet **WebPartNodeExtension** , ajoutez deux fichiers de code SiteNodeExtension nommés et WebPartNodeTypeProvider.  
  
2.  Ouvrez le menu contextuel du projet WebPartNodeExtension, puis choisissez **Ajouter une référence**.  
  
3.  Dans la boîte de dialogue **gestionnaire de référence – WebPartNodeExtension** , sélectionnez le nœud **framework** , puis activez les cases à cocher des assemblys System.ComponentModel.Composition et System.Windows.Forms.  
  
4.  Sélectionnez le nœud **Extensions** , activez la case à cocher pour les assemblys suivants, puis choisissez le bouton **OK** :  
  
    -   Microsoft.SharePoint.Client  
  
    -   Microsoft.SharePoint.Client.Runtime  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Ouvrez le menu contextuel du projet **WebPartNodeExtension** , puis choisissez **Propriétés**.  
  
     Le **Concepteur de projets** s'ouvre.  
  
6.  Choisissez **Application** tableau.  
  
7.  Dans la zone **Est la valeur par défaut l'espace de noms** \(C\#\) ou la zone **L'espace de noms racine** \(Visual Basic\), entrez **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## Création d'icônes pour les nouveaux nœuds  
 Créez deux icônes pour l'extension **Explorateur de serveurs** : une icône pour le nouveau nœud **galerie de composants WebPart** et une icône différente pour chaque nœud enfant WebPart sous le nœud **galerie de composants WebPart** .  À une étape ultérieure de cette procédure, vous écrirez du code qui associe les icônes aux nœuds.  
  
#### Pour créer des icônes pour les nœuds  
  
1.  Dans **Concepteur de projets** pour le projet WebPartNodeExtension, choisissez **ressources** tableau.  
  
2.  Sélectionnez le lien que **ce projet ne contient pas de fichier de ressources par défaut. Cliquez ici pour créer un.**  
  
     Visual Studio crée un fichier de ressources et l'ouvre dans le concepteur.  
  
3.  En haut du concepteur, cliquez sur la flèche dans la commande de menu **ajoutez la ressource** , puis choisissez **ajoutez la nouvelle icône**.  
  
4.  Entrez **WebPartsNode** pour le nouveau nom d'icône, puis choisissez le bouton **Ajouter** .  
  
     La nouvelle icône s'ouvre dans l'**Éditeur d'images**.  
  
5.  Modifiez la version 16x16 de l'icône afin qu'elle ait une conception que vous pouvez facilement identifier.  
  
6.  Ouvrez le menu contextuel pour la version 32x32 de l'icône, puis choisissez **supprimez le type d'image**.  
  
7.  Répétez les étapes 3 à 7 pour ajouter une deuxième icône aux ressources du projet, puis nommez cette icône **Composant WebPart**.  
  
8.  Dans **Explorateur de solutions**, dans le dossier **ressources** pour le projet **WebPartNodeExtension** , choisissez **WebPartsNode.ico**.  
  
9. Dans la fenêtre **Propriétés** , ouvrez la liste **Action de génération** , puis choisissez **ressource incorporée**.  
  
10. Répétez les deux dernières étapes pour **WebPart.ico**.  
  
## Ajout du nœud Galerie de composants WebPart à l'Explorateur de serveurs  
 Créez une classe ayant pour effet d'ajouter le nouveau nœud **Galerie de composants WebPart** à chaque nœud du site SharePoint.  Pour ajouter le nouvel nœud, la classe implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Mettez en œuvre cette interface chaque fois que vous comptez améliorer le comportement d'un nœud existant dans l'**Explorateur de serveurs**, comme lorsque vous ajoutez un nouveau nœud enfant à un nœud.  
  
#### Pour ajouter le nœud Galerie de composants WebPart à l'Explorateur de serveurs  
  
1.  Collez le code suivant dans le fichier de code **SiteNodeExtension** pour le projet **WebPartNodeExtension** .  
  
    > [!NOTE]  
    >  Après avoir ajouté ce code, le projet comportera des erreurs de compilation.  Ces erreurs disparaîtront lorsque vous ajouterez du code dans les étapes ultérieures.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## Définition d'un type de nœud représentant un composant WebPart  
 Créez une classe ayant pour effet de définir un nouveau type de nœud représentant un composant WebPart.  Visual Studio utilise ce nouveau type de nœud pour afficher des nœuds enfants sous le nœud **galerie de composants WebPart** .  Chacun de ces nœuds enfants représente un composant WebPart unique sur le site SharePoint.  
  
 Pour définir le nouveau type de nœud, la classe implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Mettez en œuvre cette interface chaque fois que vous comptez définir un type nouveau de nœud dans l'**Explorateur de serveurs**.  
  
#### Pour définir le type de nœud des composants WebPart  
  
1.  Collez le code suivant dans le fichier de code **WebPartNodeTypeProvider** pour le projet **WebPartNodeExtension** .  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/cs/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnode/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## Point de contrôle  
 À ce stade de la procédure, l'intégralité du code du nœud **Galerie de composants WebPart** fait désormais partie du projet.  Générez le projet **WebPartNodeExtension** afin de garantir sa compilation sans erreur.  
  
#### Pour générer le projet  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **WebPartNodeExtension** , puis choisissez **Générer**.  
  
## Création d'un package VSIX pour déployer l'extension  
 Pour déployer l'extension, utilisez le projet VSIX inclus dans votre solution pour créer un package VSIX.  D'abord, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest inclus dans le projet.  Créez le package VSIX lors de la génération de la solution.  
  
#### Pour configurer le package VSIX  
  
1.  Dans **Explorateur de solutions**, dans le projet **WebPartNode** , ouvrez le fichier **source.extension.vsixmanifest** dans l'éditeur de manifeste.  
  
     Le fichier source.extension.vsixmanifest est la base du fichier extension.vsixmanifest que tous les packages VSIX ont besoin.  Pour plus d'informations sur ce fichier, consultez [Référence de schéma d'extensions VSIX](http://msdn.microsoft.com/fr-fr/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Dans la zone **nom de produit** , entrez **Nœud galerie de composants WebPart pour l'explorateur de serveurs**.  
  
3.  Dans la zone **Author** , entrez **Contoso**.  
  
4.  Dans la zone **Description** , entrez **Ajoute un nœud personnalisé galerie de composants WebPart au nœud connexions SharePoint dans l'explorateur de serveurs**.  
  
5.  Sous l'onglet **Composants** de l'éditeur, choisissez le bouton **Nouveau** .  
  
6.  Dans la boîte de dialogue **ajoutez le nouveau ressource** , dans la liste **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à l'élément `MefComponent` dans le fichier extension.vsixmanifest.  Cet élément spécifie le nom d'un assembly d'extension dans le package VSIX.  Pour plus d’informations, consultez [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/fr-fr/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Dans la liste **Source** , choisissez **un projet dans la solution actuelle**.  
  
8.  Dans la liste **Projet** , choisissez **WebPartNodeExtension**, puis choisissez le bouton **OK** .  
  
9. Dans la barre de menus, sélectionnez **Générer**, **Générer la solution**, puis vérifiez que les compilations de solution sans erreur.  
  
10. Assurez \-vous que le dossier de sortie de la génération pour le projet WebPartNode contient maintenant le fichier WebPartNode.vsix.  
  
     Par défaut, le dossier de sortie de la génération est le dossier ..  \\bin\\Debug sous le dossier qui contient votre fichier projet.  
  
## Test de l'extension  
 Vous êtes maintenant prêt à tester le nouveau nœud **Galerie de composants WebPart** dans l'**Explorateur de serveurs**.  D'abord, commencez à déboguer le projet d'extension dans une instance expérimentale de Visual Studio.  Utilisez le nouveau nœud **WebParts** dans l'instance expérimentale de Visual Studio.  
  
#### Pour démarrer le débogage de l'extension  
  
1.  Redémarrez Visual Studio avec les informations d'identification d'administration, puis ouvrez la solution **WebPartNode** .  
  
2.  Dans le projet WebPartNodeExtension, ouvrez le fichier de code de **SiteNodeExtension** , puis ajoutez un point d'arrêt à des premières lignes de code dans les méthodes d' `NodeChildrenRequested` et d' `CreateWebPartNodes` .  
  
3.  Choisissez la touche F5 pour démarrer le débogage.  
  
     Visual Studio installe l'extension sous %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Web Part Gallery Node Extension for Server Explorer\\1.0 and starts an experimental instance of Visual Studio.  Vous testerez l'élément de projet dans cette instance de Visual Studio.  
  
#### Pour tester l'extension  
  
1.  Dans l'instance expérimentale de Visual Studio, dans le menu, choisissez **Affichage**, **Explorateur de serveurs**.  
  
2.  Assurez\-vous que le site SharePoint réservé au test s'affiche sous le nœud **Connexions SharePoint** dans l'**Explorateur de serveurs**.  Si ce n'est pas répertorié, suivez ces étapes :  
  
    1.  Ouvrez le menu contextuel pour **Connexions SharePoint**, puis choisissez **Ajouter une connexion**.  
  
    2.  Dans la boîte de dialogue **Ajoutez la connexion SharePoint** , entrez l'URL du site SharePoint auquel vous souhaitez vous connecter, puis choisissez le bouton **OK** .  
  
         Pour spécifier le site SharePoint sur votre ordinateur de développement, tapez **http:\/\/localhost**.  
  
3.  Développez le nœud de connexion de site \(qui affiche l'URL de votre site\), puis développez le nœud enfant de site \(par exemple, **Team le site**\).  
  
4.  Vérifiez que le code dans l'autre instance de Visual Studio s'arrête au point d'arrêt que vous avez défini précédemment dans la méthode d' `NodeChildrenRequested` , puis sélectionne la touche F5 pour continuer à déboguer le projet.  
  
5.  Dans l'instance expérimentale de Visual Studio, développez le nœud **galerie de composants WebPart** , qui apparaît sous le nœud de niveau supérieur de site.  
  
6.  Vérifiez que le code dans l'autre instance de Visual Studio s'arrête au point d'arrêt que vous avez défini précédemment dans la méthode d' `CreateWebPartNodes` , puis sélectionne la touche F5 pour continuer à déboguer le projet.  
  
7.  Dans l'instance expérimentale de Visual Studio, assurez\-vous que tous les composants WebPart sur le site connecté s'affichent sous le nœud **Galerie de composants WebPart** dans l'**Explorateur de serveurs**.  
  
8.  Ouvrez le menu contextuel d'un composant WebPart, puis choisissez **Propriétés**.  
  
9. Dans la fenêtre **Propriétés** , vérifiez que les informations relatives au composant WebPart s'affichent.  
  
10. Dans **Explorateur de serveurs**, ouvrez le menu contextuel pour le même composant WebPart, puis choisissez **message d'affichage**.  
  
     Dans le message qui s'affiche, cliquez sur le bouton **OK** .  
  
## Désinstallation de l'extension de Visual Studio  
 Une fois le test de l'extension, désinstallez\- la de Visual Studio.  
  
#### Pour désinstaller l'extension  
  
1.  Dans l'instance expérimentale de Visual Studio, dans le menu, choisissez **Outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s'ouvre.  
  
2.  Dans la liste d'extensions, choisissez **Nœud galerie de composants WebPart pour l'explorateur de serveurs**, puis choisissez le bouton **Désinstaller** .  
  
3.  Dans la boîte de dialogue qui s'affiche, cliquez sur le bouton **oui** .  
  
4.  Choisissez le bouton **Redémarrez maintenant** pour terminer la désinstallation.  
  
     L'élément de projet est également désinstallé.  
  
5.  Fermez les deux instances de Visual Studio \(l'instance expérimentale et l'instance de Visual Studio dans laquelle la solution WebPartNode est ouverte\).  
  
## Voir aussi  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  