---
title: "Walkthrough: Extending Server Explorer to Display Web Parts"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 5b1f104a-0eaf-4929-9f1f-d7afcfc8b707
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Walkthrough: Extending Server Explorer to Display Web Parts
  Dans Visual Studio, vous pouvez utiliser le nœud **Connexions SharePointExplorateur de serveurs** pour afficher des composants sur les sites sharepoint.  Toutefois, **Explorateur de serveurs** n'affiche pas certains composants par défaut.  Dans cette procédure pas \- à \- pas, vous étendez **Explorateur de serveurs** afin qu'il affiche la galerie de composants WebPart sur chaque site SharePoint connecté.  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Création d'une extension Visual Studio offrant les capacités supplémentaires suivantes à l'**Explorateur de serveurs** :  
  
    -   L'extension ajoute un nœud **galerie de composants WebPart** sous chaque nœud de site SharePoint dans **Explorateur de serveurs**.  Ce nouveau nœud contient les nœuds enfants représentant chaque composant WebPart dans la galerie de composants WebPart sur le site.  
  
    -   L'extension définit un nouveau type de nœud représentant une instance du composant WebPart.  Ce nouveau type de nœud constitue la base des nœuds enfants sous le nouveau nœud **Galerie de composants WebPart**.  Le nouveau type de nœud WebPart affiche les informations relatives au composant WebPart qu'il représente dans la fenêtre **Propriétés**.  Le type de nœud inclut également un élément de menu contextuel personnalisé que vous pouvez utiliser comme point de départ pour effectuer d'autres tâches relatives au composant WebPart.  
  
-   Création de deux commandes SharePoint personnalisées que le l'assembly d'extension appelle.  Les commandes SharePoint sont des méthodes susceptibles d'être appelées par des assemblys d'extension pour utiliser des API dans le modèle d'objet serveur pour SharePoint.  Dans cette procédure pas à pas, vous allez apprendre à créer des commandes utilisées pour extraire les informations WebPart du site SharePoint local sur l'ordinateur de développement.  Pour plus d’informations, consultez [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Génération d'un package VSIX \(Visual Studio Extension\) pour déployer l'extension.  
  
-   Débogage et test de l'extension.  
  
> [!NOTE]  
>  Pour une autre version de cette procédure pas \- à \- pas qui utilise le modèle d'objet client pour SharePoint au lieu de son modèle d'objet serveur, consultez [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## Composants requis  
 Vous avez besoin des composants suivants sur l'ordinateur de développement pour terminer cette procédure pas à pas :  
  
-   Éditions prises windows, de SharePoint et Visual Studio.  Pour plus d’informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Le kit de développement Visual Studio.  Cette procédure pas à pas utilise le modèle **Projet VSIX** du Kit de développement logiciel \(SDK\) pour créer un package VSIX afin de déployer l'élément de projet.  Pour plus d’informations, consultez [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Une connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer cette procédure pas à pas :  
  
-   Utilisation du modèle d'objet serveur pour SharePoint.  Pour plus d'informations, consultez [Utilisation du modèle d'objet serveur SharePoint Foundation \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Composants WebPart dans les solutions SharePoint.  Pour plus d'informations, consultez [Vue d'ensemble des composants WebPart](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## Création du projet  
 Pour exécuter cette procédure, vous devez créer trois projets :  
  
-   Un projet VSIX pour créer le package VSIX afin de déployer l'extension.  
  
-   Un projet de bibliothèque de classes qui implémente l'extension.  Ce projet doit cibler .NET Framework 4,5.  
  
-   Un projet de bibliothèque de classes qui définit les commandes SharePoint personnalisées.  Ce projet doit cibler .NET Framework 3.5.  
  
 Démarrez la procédure pas à pas en créant les projets.  
  
#### Pour créer le projet VSIX  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
3.  Dans la boîte de dialogue  **Nouveau projet** , développez les nœuds **Visual C\#** ou **Visual Basic** , puis sélectionnez le nœud **Extensibilité** .  
  
    > [!NOTE]  
    >  Le nœud **Extensibilité** est disponible uniquement si vous installez le kit de développement Visual Studio.  Pour plus d'informations, consultez la section des composants requis plus haut dans cette rubrique.  
  
4.  En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework.  
  
5.  Sélectionnez le modèle **projet VSIX** , nommez le projet **WebPartNode**, puis choisissez le bouton **OK** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **WebPartNode** à l'**Explorateur de solutions**.  
  
#### Pour créer le projet d'extension  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution, choisissez **Ajouter**, puis choisissez **Nouveau projet**.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, le nœud de la solution s'affiche dans l'**Explorateur de solutions** à condition d'avoir activé la case à cocher **Toujours afficher la solution** dans la [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Dans la boîte de dialogue **Nouveau projet** , développez le nœud **Visual C\#** ou le nœud **Visual Basic** , puis le nœud **Fenêtres** de choisir.  
  
3.  En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework.  
  
4.  Dans la liste des modèles de projet, choisissez **Bibliothèque de classes**, nommez le projet **WebPartNodeExtension**, puis choisissez le bouton **OK** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **WebPartNodeExtension** à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprimez le fichier de code Class1 du projet.  
  
#### Pour créer le projet de commandes SharePoint  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution, choisissez **Ajouter**, puis choisissez **Nouveau projet**.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, le nœud de la solution s'affiche dans l'**Explorateur de solutions** à condition d'avoir activé la case à cocher **Toujours afficher la solution** dans la [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Dans la boîte de dialogue  **Nouveau projet** , développez le nœud **Visual C\#** ou le nœud **Visual Basic** , puis sélectionnez le nœud **Fenêtres** .  
  
3.  En haut de la boîte de dialogue, choisissez **.NET Framework 3.5** dans la liste des versions du .NET Framework.  
  
4.  Dans la liste des modèles de projet, choisissez **Bibliothèque de classes**, nommez le projet **WebPartCommands**, puis choisissez le bouton **OK** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **WebPartCommands** à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprimez le fichier de code Class1 du projet.  
  
## Configuration des projets  
 Avant d'écrire le code pour créer l'extension, vous devez ajouter des fichiers de code et des références d'assembly, et configurez les paramètres du projet.  
  
#### Pour configurer le projet WebPartNodeExtension  
  
1.  Dans le projet WebPartNodeExtension, ajoutez quatre fichiers de code portant les noms suivants :  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Ouvrez le menu contextuel du projet **WebPartNodeExtension** , puis choisissez **Ajouter une référence**.  
  
3.  Dans la boîte de dialogue **gestionnaire de référence – WebPartNodeExtension** , sélectionnez l'onglet **framework** , puis activez la case à cocher pour chacun des assemblys suivants :  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Sélectionnez l'onglet **Extensions** , activez la case à cocher pour l'assembly Microsoft.VisualStudio.SharePoint, puis choisissez le bouton **OK** .  
  
5.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **WebPartNodeExtension** , puis choisissez **Propriétés**.  
  
     Le **Concepteur de projets** s'ouvre.  
  
6.  Choisissez **Application** tableau.  
  
7.  Dans la zone **Est la valeur par défaut l'espace de noms** \(C\#\) ou la zone **L'espace de noms racine** \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\), entrez **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### Pour configurer le projet WebPartCommands  
  
1.  Dans le projet WebPartCommands, ajoutez un fichier de code appelé WebPartCommands.  
  
2.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **WebPartCommands** , choisissez **Ajouter**, puis choisissez **élément existant**.  
  
3.  Dans la boîte de dialogue **Ajouter un élément existant** , accédez au dossier qui contient les fichiers de code pour le projet WebPartNodeExtension, et des fichiers puis choisissez de WebPartNodeInfo et WebPartCommandIds code.  
  
4.  Cliquez sur la flèche en regard de le bouton **Ajouter** , puis choisissez **Ajoutez en tant que lien** dans le menu qui s'affiche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute les fichiers de code au projet WebPartCommands en tant que liens.  Par conséquent, les fichiers de code se trouvent dans le projet WebPartNodeExtension, mais le code dans les fichiers sont également compilés dans le projet WebPartCommands.  
  
5.  Ouvrez le menu contextuel du projet **WebPartCommands** de nouveau, puis choisissez **Ajouter une référence**.  
  
6.  Dans la boîte de dialogue **gestionnaire de référence – WebPartCommands** , sélectionnez l'onglet **Extensions** , activez la case à cocher pour les assemblys suivants, puis choisissez le bouton **OK** :  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **WebPartCommands** de nouveau, puis choisissez **Propriétés**.  
  
     Le **Concepteur de projets** s'ouvre.  
  
8.  Choisissez **Application** tableau.  
  
9. Dans la zone **Est la valeur par défaut l'espace de noms** \(C\#\) ou la zone **L'espace de noms racine** \([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\), entrez **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## Création d'icônes pour les nouveaux nœuds  
 Créez deux icônes pour l'extension **Explorateur de serveurs** : une pour le nouveau nœud **Galerie de composants WebPart**, et une autre pour chaque nœud WebPart enfant sous le nœud **Galerie de composants WebPart**.  Vous apprendrez un peu plus loin à écrire du code afin d'associer ces icônes aux nœuds.  
  
#### Pour créer des icônes pour les nœuds  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **WebPartNodeExtension** , puis choisissez **Propriétés**.  
  
2.  Le **Concepteur de projets** s'ouvre.  
  
3.  Sélectionnez **l'onglet** de ressources, puis choisissez **le ce projet ne contient pas de fichier de ressources par défaut. Cliquez ici pour créer un** lien.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée un fichier de ressources et l'ouvre dans le concepteur.  
  
4.  En haut du concepteur, cliquez sur la flèche en regard de la commande de menu **ajoutez la ressource** , puis choisissez **ajoutez la nouvelle icône** dans le menu qui s'affiche.  
  
5.  Dans la boîte de dialogue **ajoutez la nouvelle ressource** , nommez la nouvelle icône **WebPartsNode**, puis choisissez le bouton **Ajouter** .  
  
     La nouvelle icône s'ouvre dans l'**Éditeur d'images**.  
  
6.  Modifiez la version 16x16 de l'icône afin qu'elle ait une conception que vous pouvez facilement identifier.  
  
7.  Ouvrez le menu contextuel pour la version 32x32 de l'icône, puis choisissez **supprimez le type d'image**.  
  
8.  Répétez les étapes 5 à 8 pour ajouter une deuxième icône aux ressources du projet, puis nommez cette icône **Composant WebPart**.  
  
9. Dans **Explorateur de solutions**, sous le dossier **ressources** pour le projet **WebPartNodeExtension** , ouvrez le menu contextuel pour **WebPartsNode.ico**.  
  
10. Dans la fenêtre **Propriétés** , cliquez sur la flèche en regard **Action de génération**, puis choisissez **ressource incorporée** dans le menu qui s'affiche.  
  
11. Répétez les deux dernières étapes pour **WebPart.ico**.  
  
## Ajout du nœud Galerie de composants WebPart à l'Explorateur de serveurs  
 Créez une classe ayant pour effet d'ajouter le nouveau nœud **Galerie de composants WebPart** à chaque nœud du site SharePoint.  Pour ajouter le nouvel nœud, la classe implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Implémentez cette interface chaque fois que vous souhaitez étendre le comportement d'un nœud existant dans **Explorateur de serveurs**, par exemple ajouter un nœud enfant à un nœud.  
  
#### Pour ajouter le nœud Galerie de composants WebPart à l'Explorateur de serveurs  
  
1.  Dans le projet WebPartNodeExtension, ouvrez le fichier de code SiteNodeExtension, puis collez le code suivant dans ce fichier.  
  
    > [!NOTE]  
    >  Après avoir ajouté ce code, le projet comportera des erreurs de compilation, mais ils partiront lorsque vous ajoutez le code dans les étapes ultérieures.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/sitenodeextension.vb#1)]  
  
## Définition d'un type de nœud représentant un composant WebPart  
 Créez une classe ayant pour effet de définir un nouveau type de nœud représentant un composant WebPart.  Visual Studio utilise ce nouveau type de nœud pour afficher des nœuds enfants sous le nœud **galerie de composants WebPart** .  Chaque nœud enfant représente un composant WebPart unique sur le site SharePoint.  
  
 Pour définir le nouveau type de nœud, la classe implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Mettez en œuvre cette interface chaque fois que vous comptez définir un type nouveau de nœud dans l'**Explorateur de serveurs**.  
  
#### Pour définir le type de nœud des composants WebPart  
  
1.  Dans le projet WebPartNodeExtension, ouvrez le fichier de code de WebPartNodeTypeProvder, puis collez le code suivant dans ce fichier.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodetypeprovider.vb#2)]  
  
## Définition de la classe de données WebPart  
 Définissez une classe contenant des données à propos d'un composant WebPart unique sur le site SharePoint.  À une étape ultérieure de cette procédure, vous allez créer une commande SharePoint personnalisée qui récupère des données sur chaque composant WebPart sur le site puis assigne les données aux instances de cette classe.  
  
#### Pour définir la classe de données WebPart  
  
1.  Dans le projet WebPartNodeExtension, ouvrez le fichier de code WebPartNodeInfo, puis collez le code suivant dans ce fichier.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartnodeinfo.cs#3)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartnodeinfo.vb#3)]  
  
## Définition des ID pour la commande SharePoint  
 Définissez plusieurs chaînes qui identifient les commandes SharePoint personnalisées.  Vous implémenterez ces commandes à une étape ultérieure de cette procédure.  
  
#### Pour définir les ID de commande  
  
1.  Dans le projet WebPartNodeExtension, ouvrez le fichier de code WebPartCommandIds, puis collez le code suivant dans ce fichier.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartnodeextension/webpartcommandids.vb#4)]  
  
## Création de commandes SharePoint personnalisées  
 Créez des commandes personnalisées faisant appel au modèle d'objet serveur SharePoint pour récupérer des données sur les composants webpart sur le site SharePoint.  Chaque commande est une méthode à laquelle s'applique <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>.  
  
#### Pour définir les commandes SharePoint  
  
1.  Dans le projet WebPartCommands, ouvrez le fichier de code WebPartCommands, puis collez le code suivant dans ce fichier.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/CS/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.spexplorer.webpartnodewithcommands/vb/webpartcommands/webpartcommands.vb#6)]  
  
## Point de contrôle  
 À ce stade de la procédure, l'intégralité du code pour le nœud **Galerie de composants WebPart** et les commandes SharePoint font désormais partie des projets.  Générez la solution pour vous assurer que la compilation des deux projets se déroule sans erreur.  
  
#### Pour générer la solution  
  
1.  Dans la barre de menus, sélectionnez **Générer**, **Générer la solution**.  
  
    > [!WARNING]  
    >  À ce stade, le projet WebPartNode peut avoir une erreur de build car le fichier manifeste VSIX n'a pas de valeur pour l'auteur.  Cette erreur partira lorsque vous ajoutez une valeur dans les étapes ultérieures.  
  
## Création d'un package VSIX pour déployer l'extension  
 Pour déployer l'extension, utilisez le projet VSIX inclus dans votre solution pour créer un package VSIX.  D'abord, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest du projet VSIX.  Ensuite, créez le package VSIX en générant la solution.  
  
#### Pour configurer le package VSIX  
  
1.  Dans **Explorateur de solutions**, sous le projet WebPartNode, ouvrez le fichier **source.extension.vsixmanifest** dans l'éditeur de manifeste.  
  
     Le fichier source.extension.vsixmanifest est la base du fichier extension.vsixmanifest que tous les packages VSIX ont besoin.  Pour plus d'informations sur ce fichier, consultez [Référence de schéma d'extensions VSIX](http://msdn.microsoft.com/fr-fr/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Dans la zone **nom de produit** , entrez **Nœud galerie de composants WebPart pour l'explorateur de serveurs**.  
  
3.  Dans la zone **Author** , entrez **Contoso**.  
  
4.  Dans **la zone** de description, entrez **ajoute un nœud personnalisé galerie de composants WebPart au nœud connexions SharePoint dans l'explorateur de serveurs. Cette extension a recours à une commande SharePoint personnalisée pour effectuer un appel dans le modèle d'objet serveur.**  
  
5.  Sélectionnez l'onglet **Composants** de l'éditeur, puis choisissez le bouton **Nouveau** .  
  
     La boîte de dialogue **ajoutez le nouveau ressource** s'affiche.  
  
6.  Dans la liste **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à l'élément `MefComponent` dans le fichier extension.vsixmanifest.  Cet élément spécifie le nom d'un assembly d'extension dans le package VSIX.  Pour plus d’informations, consultez [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/fr-fr/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Dans la liste **Source** , choisissez **un projet dans la solution actuelle**.  
  
8.  Dans la liste **Projet** , choisissez **WebPartNodeExtension** puis choisissez le bouton **OK** .  
  
9. Dans l'éditeur de manifeste, choisissez le bouton **Nouveau** de nouveau.  
  
     La boîte de dialogue **ajoutez le nouveau ressource** s'affiche.  
  
10. Dans la zone **Type** , entrez **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Cet élément désigne l'extension personnalisée à inclure à l'extension Visual Studio.  Pour plus d’informations, consultez [Élément de ressource \(schéma VSX\)](http://msdn.microsoft.com/fr-fr/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. Dans la liste **Source** , sélectionnez l'élément de liste **un projet dans la solution actuelle** .  
  
12. Dans la liste **Projet** , choisissez **WebPartCommands**, puis choisissez le bouton **OK** .  
  
13. Dans la barre de menus, sélectionnez **Générer**, **Générer la solution**, puis vérifiez que les compilations de solution sans erreur.  
  
14. Assurez \-vous que le dossier de sortie de la génération pour le projet WebPartNode contient maintenant le fichier WebPartNode.vsix.  
  
     Par défaut, le dossier de sortie de la génération est le dossier ..  \\bin\\Debug sous le dossier qui contient votre fichier projet.  
  
## Test de l'extension  
 Vous êtes maintenant prêt à tester le nouveau nœud **galerie de composants WebPart** dans **Explorateur de serveurs**.  Tout d'abord, commencez à déboguer l'extension dans une instance expérimentale de Visual Studio.  Ensuite, utilisez le nouveau nœud **WebPart** dans l'instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### Pour démarrer le débogage de l'extension  
  
1.  Redémarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] avec les informations d'identification d'administration, puis ouvrez la solution WebPartNode.  
  
2.  Dans le projet WebPartNodeExtension, ouvrez le fichier de code SiteNodeExtension, puis ajoutez un point d'arrêt sur la première ligne de code dans les méthodes d' `NodeChildrenRequested` et d' `CreateWebPartNodes` .  
  
3.  Choisissez la touche F5 pour démarrer le débogage.  
  
     Visual Studio installe l'extension sous %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Web Part Gallery Node Extension for Server Explorer\\1.0 and starts an experimental instance of Visual Studio.  Vous testerez l'élément de projet dans cette instance de Visual Studio.  
  
#### Pour tester l'extension  
  
1.  Dans l'instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dans la barre de menus, sélectionnez **Affichage**, **Explorateur de serveurs**.  
  
2.  Exécutez les étapes suivantes si le site SharePoint que vous souhaitez utiliser pour le test n'apparaît pas sous le nœud **Connexions SharePoint** dans **Explorateur de serveurs**:  
  
    1.  Dans **Explorateur de serveurs**, ouvrez le menu contextuel pour **Connexions SharePoint**, puis choisissez **Ajouter une connexion**.  
  
    2.  Dans la boîte de dialogue **Ajoutez la connexion SharePoint** , entrez l'URL du site SharePoint auquel vous souhaitez vous connecter, puis choisissez le bouton **OK** .  
  
         Pour spécifier le site SharePoint sur votre ordinateur de développement, entrez **http:\/\/localhost**.  
  
3.  Développez le nœud de connexion de site \(qui affiche l'URL de votre site\), puis développez le nœud enfant de site \(par exemple, **Team le site**\).  
  
4.  Vérifiez que le code dans l'autre instance d' [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] s'immobilise sur le point d'arrêt que vous avez défini précédemment dans la méthode d' `NodeChildrenRequested` , puis choisit sur F5 pour continuer à déboguer le projet.  
  
5.  Dans l'instance expérimentale de Visual Studio, vérifiez qu'un nœud nommé **galerie de composants WebPart** apparaît sous le nœud de niveau supérieur de site, puis développez le nœud **galerie de composants WebPart** .  
  
6.  Vérifiez que le code dans l'autre instance de Visual Studio s'arrête au point d'arrêt que vous avez défini précédemment dans la méthode d' `CreateWebPartNodes` , puis sélectionne la touche F5 pour continuer à déboguer le projet.  
  
7.  Dans l'instance expérimentale de Visual Studio, vérifiez que tous les composants webpart sur le site connecté s'affichent sous le nœud **galerie de composants WebPart** dans **Explorateur de serveurs**.  
  
8.  Dans **Explorateur de serveurs**, ouvrez le menu contextuel pour un des composants webpart, puis choisissez **Propriétés**.  
  
9. Dans l'instance d' [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que vous déboguez, vérifiez que les informations relatives au composant WebPart s'affichent dans la fenêtre **Propriétés** .  
  
## Désinstallation de l'extension de Visual Studio  
 Une fois le test de l'extension terminé, désinstallez l'extension de Visual Studio.  
  
#### Pour désinstaller l'extension  
  
1.  Dans l'instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dans la barre de menus, sélectionnez **Outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s'ouvre.  
  
2.  Dans la liste d'extensions, choisissez **Extension du nœud galerie de composants WebPart pour l'explorateur de serveurs**, puis choisissez le bouton **Désinstaller** .  
  
3.  Dans la boîte de dialogue qui s'affiche, cliquez sur le bouton **oui** pour confirmer que vous voulez désinstaller l'extension, puis choisissez le bouton **Redémarrez maintenant** pour terminer la désinstallation.  
  
4.  Fermez les deux instances de Visual Studio \(l'instance expérimentale et l'instance de Visual Studio dans laquelle la solution WebPartNode est ouverte\).  
  
## Voir aussi  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Image Editor for Icons](/visual-cpp/windows/image-editor-for-icons)   
 [Creating an Icon or Other Image &#40;Image Editor for Icons&#41;](/visual-cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  