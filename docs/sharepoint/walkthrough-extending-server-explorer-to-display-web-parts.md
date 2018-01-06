---
title: "Procédure pas à pas : Extension de l’Explorateur de serveurs pour afficher des WebParts | Documents Microsoft"
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
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
ms.assetid: 5b1f104a-0eaf-4929-9f1f-d7afcfc8b707
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8fea089340c0d51fb5b88bf20d5521defc5dcc71
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-extending-server-explorer-to-display-web-parts"></a>Procédure pas à pas : extension de l'Explorateur de serveurs pour afficher des WebParts
  Dans Visual Studio, vous pouvez utiliser la **connexions SharePoint** nœud de **l’Explorateur de serveurs** pour afficher les composants sur les sites SharePoint. Toutefois, **l’Explorateur de serveurs** n’affiche pas certains composants par défaut. Dans cette procédure pas à pas, vous allez étendre **l’Explorateur de serveurs** afin qu’il affiche la galerie de composants WebPart sur chacun connecté à un site SharePoint.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’une extension Visual Studio qui étend **l’Explorateur de serveurs** comme suit :  
  
    -   L’extension ajoute un **galerie de composants WebPart** nœud sous chaque nœud de site SharePoint dans **l’Explorateur de serveurs**. Ce nouveau nœud contient des nœuds enfants représentant chaque composant WebPart dans la galerie de composants WebPart sur le site.  
  
    -   L’extension définit un nouveau type de nœud qui représente une instance de composant WebPart. Ce nouveau type de nœud est la base pour les nœuds enfants sous le nouveau **galerie de composants WebPart** nœud. Le nouveau type de nœud WebPart affiche des informations dans le **propriétés** fenêtre sur le composant WebPart qu’il représente. Le type de nœud inclut également un élément de menu contextuel personnalisé que vous pouvez utiliser comme point de départ pour effectuer d’autres tâches liées au composant WebPart.  
  
-   Création des deux commandes SharePoint personnalisées qui le les appels assembly d’extension. Commandes SharePoint sont des méthodes qui peuvent être appelées par les assemblys d’extension à utiliser des API dans le modèle objet serveur pour SharePoint. Dans cette procédure pas à pas, vous créez des commandes permettant de récupérer les informations de composant WebPart à partir du site SharePoint local sur l’ordinateur de développement. Pour plus d’informations, consultez [appel des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Création d’un package d’Extension Visual Studio (VSIX) pour déployer l’extension.  
  
-   Débogage et test de l’extension.  
  
> [!NOTE]  
>  Pour une autre version de cette procédure pas à pas qui utilise le modèle objet client pour SharePoint au lieu de son modèle d’objet serveur, consultez [procédure pas à pas : appel dans le modèle d’objet Client SharePoint dans une Extension de l’Explorateur de serveurs](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Vous devez disposer des composants suivants sur l’ordinateur de développement pour terminer cette procédure pas à pas :  
  
-   Éditions prises en charge de Windows, SharePoint et Visual Studio. Pour plus d’informations, consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Le Kit de développement avec Visual Studio. Cette procédure pas à pas utilise le **projet VSIX** modèle dans le Kit de développement pour créer un package VSIX pour déployer l’élément de projet. Pour plus d’informations, consultez [extension des outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Connaissance des concepts suivants s’avère utile, mais n’est pas requis pour terminer la procédure pas à pas :  
  
-   À l’aide du modèle d’objet serveur pour SharePoint. Pour plus d’informations, consultez [à l’aide du modèle d’objet SharePoint Foundation côté serveur](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Composants WebPart dans les solutions SharePoint. Pour plus d’informations, consultez [vue d’ensemble des parties Web](http://go.microsoft.com/fwlink/?LinkId=177803).  
  
## <a name="creating-the-projects"></a>Création des projets  
 Pour effectuer cette procédure pas à pas, vous devez créer trois projets :  
  
-   Un projet VSIX pour créer le package VSIX pour déployer l’extension.  
  
-   Un projet de bibliothèque de classes qui implémente l’extension. Ce projet doit cibler le .NET Framework 4.5.  
  
-   Un projet de bibliothèque de classes qui définit les commandes SharePoint personnalisées. Ce projet doit cibler.NET Framework 3.5.  
  
 Démarrer la procédure pas à pas en créant les projets.  
  
#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, puis choisissez le **extensibilité** nœud.  
  
    > [!NOTE]  
    >  Le **extensibilité** nœud est disponible uniquement si vous installez le Kit de développement logiciel Visual Studio. Pour plus d’informations, consultez la section conditions préalables plus haut dans cette rubrique.  
  
4.  En haut de la boîte de dialogue, choisissez **.NET Framework 4.5** dans la liste des versions du .NET Framework.  
  
5.  Choisissez le **projet VSIX** modèle, nommez le projet **WebPartNode**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Ajoute le **WebPartNode** projet **l’Explorateur de solutions**.  
  
#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud de solution, choisissez **ajouter**, puis choisissez **nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** nœud ou **Visual Basic** nœud, puis cliquez **Windows** nœud.  
  
3.  En haut de la boîte de dialogue, choisissez **.NET Framework 4.5** dans la liste des versions du .NET Framework.  
  
4.  Dans la liste des modèles de projet, choisissez **bibliothèque de classes**, nommez le projet **WebPartNodeExtension**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Ajoute le **WebPartNodeExtension** projet à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprime le fichier de code Class1 du projet.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Pour créer le projet de commandes SharePoint  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud de solution, choisissez **ajouter**, puis choisissez **nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** nœud ou **Visual Basic** nœud, puis choisissez le **Windows** nœud.  
  
3.  En haut de la boîte de dialogue, choisissez **.NET Framework 3.5** dans la liste des versions du .NET Framework.  
  
4.  
  
5.  Dans la liste des modèles de projet, choisissez **bibliothèque de classes**, nommez le projet **WebPartCommands**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Ajoute le **WebPartCommands** projet à la solution et ouvre le fichier de code Class1 par défaut.  
  
6.  Supprime le fichier de code Class1 du projet.  
  
## <a name="configuring-the-projects"></a>Configuration des projets  
 Avant d’écrire de code pour créer l’extension, vous devez ajouter des fichiers de code et des références d’assembly et configurer les paramètres du projet.  
  
#### <a name="to-configure-the-webpartnodeextension-project"></a>Pour configurer le projet WebPartNodeExtension  
  
1.  Dans le projet WebPartNodeExtension, ajoutez quatre fichiers de code qui portent les noms suivants :  
  
    -   SiteNodeExtension  
  
    -   WebPartNodeTypeProvider  
  
    -   WebPartNodeInfo  
  
    -   WebPartCommandIds  
  
2.  Ouvrez le menu contextuel pour le **WebPartNodeExtension** de projet, puis choisissez **ajouter une référence**.  
  
3.  Dans le **Gestionnaire de références - WebPartNodeExtension** boîte de dialogue, choisissez le **Framework** onglet et sélectionnez la case à cocher pour chacun des assemblys suivants :  
  
    -   System.ComponentModel.Composition  
  
    -   System.Windows.Forms  
  
4.  Choisissez le **Extensions** onglet, activez la case à cocher pour l’assembly Microsoft.VisualStudio.SharePoint, puis choisissez le **OK** bouton.  
  
5.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **WebPartNodeExtension** nœud de projet, puis choisissez **propriétés**.  
  
     Le **Concepteur de projets** s’ouvre.  
  
6.  Choisissez l’onglet **Application**.  
  
7.  Dans le **par défaut d’espace de noms** boîte (c#) ou **espace de noms racine** boîte ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), entrez **ServerExplorer.SharePointConnections.WebPartNode**.  
  
#### <a name="to-configure-the-webpartcommands-project"></a>Pour configurer le projet WebPartCommands  
  
1.  Dans le projet WebPartCommands, ajoutez un fichier de code appelé WebPartCommands.  
  
2.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **WebPartCommands** nœud de projet, choisissez **ajouter**, puis choisissez **unélémentexistant**.  
  
3.  Dans le **ajouter un élément existant** boîte de dialogue, accédez au dossier qui contient les fichiers de code pour le projet WebPartNodeExtension, puis choisissez les fichiers de code WebPartNodeInfo et WebPartCommandIds.  
  
4.  Cliquez sur la flèche à côté du **ajouter** bouton, puis choisissez **ajouter en tant que lien** dans le menu qui s’affiche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Ajoute les fichiers de code au projet WebPartCommands sous forme de liens. Par conséquent, les fichiers de code sont trouvent dans le projet WebPartNodeExtension, mais le code dans les fichiers sont également compilés dans le projet WebPartCommands.  
  
5.  Ouvrez le menu contextuel pour le **WebPartCommands** le projet à nouveau, puis choisissez **ajouter une référence**.  
  
6.  Dans le **Gestionnaire de références - WebPartCommands** boîte de dialogue, choisissez le **Extensions** onglet, activez la case à cocher pour chacun des assemblys suivants, puis choisissez le **OK** bouton :  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
7.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **WebPartCommands** à nouveau de projet, puis choisissez **propriétés**.  
  
     Le **Concepteur de projets** s’ouvre.  
  
8.  Choisissez l’onglet **Application**.  
  
9. Dans le **par défaut d’espace de noms** boîte (c#) ou **espace de noms racine** boîte ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), entrez **ServerExplorer.SharePointConnections.WebPartNode**.  
  
## <a name="creating-icons-for-the-new-nodes"></a>Création d’icônes pour les nouveaux nœuds  
 Créez deux icônes pour le **l’Explorateur de serveurs** extension : une icône pour le nouveau **galerie de composants WebPart** nœud et une autre pour chaque nœud de composant WebPart enfant sous le **galerie de composants WebPart** nœud. Plus loin dans cette procédure pas à pas, vous allez écrire le code qui associe ces icônes avec les nœuds.  
  
#### <a name="to-create-icons-for-the-nodes"></a>Pour créer des icônes pour les nœuds  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **WebPartNodeExtension** de projet, puis choisissez **propriétés**.  
  
2.  Le **Concepteur de projets** s’ouvre.  
  
3.  Choisissez le **ressources** onglet, puis choisissez le **ce projet ne contient pas un fichier de ressources par défaut. Cliquez ici pour en créer un** lien.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Crée un fichier de ressources et l’ouvre dans le concepteur.  
  
4.  En haut du concepteur, cliquez sur la flèche à côté du **ajouter une ressource** menu de commande, puis choisissez **ajouter une nouvelle icône** dans le menu qui s’affiche.  
  
5.  Dans le **ajouter une nouvelle ressource** boîte de dialogue, nom de la nouvelle icône **WebPartsNode**, puis choisissez le **ajouter** bouton.  
  
     La nouvelle icône s’ouvre dans le **Éditeur d’images**.  
  
6.  Modifier la version de l’icône de 16 x 16 afin qu’il ait une conception que vous pouvez facilement identifier.  
  
7.  Ouvrez le menu contextuel pour la version de l’icône 32 x 32, puis choisissez **supprimer le Type d’Image**.  
  
8.  Répétez les étapes 5 à 8 pour ajouter une deuxième icône aux ressources du projet et nommez cette icône **WebPart**.  
  
9. Dans **l’Explorateur de solutions**, sous le **ressources** dossier pour le **WebPartNodeExtension** de projet, ouvrez le menu contextuel pour **WebPartsNode.ico**.  
  
10. Dans le **propriétés** fenêtre, cliquez sur la flèche à côté **Action de génération**, puis choisissez **ressource incorporée** dans le menu qui s’affiche.  
  
11. Répétez les deux dernières étapes pour **WebPart.ico**.  
  
## <a name="adding-the-web-part-gallery-node-to-server-explorer"></a>Ajouter le nœud de la galerie de composants WebPart à l’Explorateur de serveurs  
 Créez une classe qui ajoute le nouveau **galerie de composants WebPart** nœud pour chaque nœud du site SharePoint. Pour ajouter le nouveau nœud, la classe implémente le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interface. Implémentez cette interface chaque fois que vous souhaitez étendre le comportement d’un nœud existant dans **l’Explorateur de serveurs**, telles que l’ajout d’un nœud enfant à un nœud.  
  
#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Pour ajouter le nœud de la galerie de composants WebPart à l’Explorateur de serveurs  
  
1.  Dans le projet WebPartNodeExtension, ouvrez le fichier de code SiteNodeExtension, puis collez le code suivant dans celui-ci.  
  
    > [!NOTE]  
    >  Une fois que vous ajoutez ce code, le projet aura des erreurs de compilation, mais ils allez disparaître lorsque vous ajoutez code dans les étapes ultérieures.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]  
  
## <a name="defining-a-node-type-that-represents-a-web-part"></a>Définition d’un Type de nœud qui représente un composant WebPart  
 Créez une classe qui définit un nouveau type de nœud qui représente un composant WebPart. Visual Studio utilise ce nouveau type de nœud pour afficher les nœuds enfants sous le **galerie de composants WebPart** nœud. Chaque nœud enfant représente un composant WebPart sur le site SharePoint.  
  
 Pour définir le nouveau type de nœud, la classe implémente le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interface. Implémentez cette interface chaque fois que vous souhaitez définir un nouveau type de nœud dans **l’Explorateur de serveurs**.  
  
#### <a name="to-define-the-web-part-node-type"></a>Pour définir le type de nœud de composant WebPart  
  
1.  Dans le projet WebPartNodeExtension, ouvrez le fichier de code WebPartNodeTypeProvider, puis collez le code suivant dans celui-ci.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]  
  
## <a name="defining-the-web-part-data-class"></a>Définition de la classe de données WebPart  
 Définissez une classe qui contient des données sur un composant WebPart sur le site SharePoint. Plus loin dans cette procédure pas à pas, vous allez créer une commande SharePoint personnalisée qui extrait des données relatives à chaque composant WebPart sur le site et puis affecte les données aux instances de cette classe.  
  
#### <a name="to-define-the-web-part-data-class"></a>Pour définir la classe de données de composant WebPart  
  
1.  Dans le projet WebPartNodeExtension, ouvrez le fichier de code WebPartNodeInfo, puis collez le code suivant dans celui-ci.  
  
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]  
  
## <a name="defining-the-ids-for-the-sharepoint-command"></a>Définition des ID pour la commande SharePoint  
 Définir plusieurs chaînes qui identifient les commandes SharePoint personnalisées. Vous allez implémenter ces commandes plus loin dans cette procédure pas à pas.  
  
#### <a name="to-define-the-command-ids"></a>Pour définir les ID de commande  
  
1.  Dans le projet WebPartNodeExtension, ouvrez le fichier de code WebPartCommandIds, puis collez le code suivant dans celui-ci.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]  
  
## <a name="creating-the-custom-sharepoint-commands"></a>Création de commandes SharePoint personnalisées  
 Créer des commandes personnalisées qui appellent le modèle d’objet serveur pour SharePoint pour récupérer des données sur les composants WebPart sur le site SharePoint. Chaque commande est une méthode qui a le <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> appliqué.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Pour définir les commandes SharePoint  
  
1.  Dans le projet WebPartCommands, ouvrez le fichier de code WebPartCommands, puis collez le code suivant dans celui-ci.  
  
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]  
  
## <a name="checkpoint"></a>Point de contrôle  
 À ce stade de la procédure pas à pas, tout le code pour le **galerie de composants WebPart** nœud et les commandes SharePoint sont désormais dans les projets. Générez la solution pour vous assurer que les deux projets compilé sans erreur.  
  
#### <a name="to-build-the-solution"></a>Pour générer la solution  
  
1.  Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
    > [!WARNING]  
    >  À ce stade, le projet WebPartNode peut-être une erreur de build, car le fichier manifest VSIX n’a pas une valeur pour l’auteur. Cette erreur disparaîtra lorsque vous ajoutez une valeur dans les étapes ultérieures.  
  
## <a name="creating-a-vsix-package-to-deploy-the-extension"></a>Création d’un Package VSIX pour déployer l’Extension  
 Pour déployer l’extension, utilisez le projet VSIX dans votre solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest dans le projet VSIX. Ensuite, créez le package VSIX en générant la solution.  
  
#### <a name="to-configure-the-vsix-package"></a>Pour configurer le package VSIX  
  
1.  Dans **l’Explorateur de solutions**, sous le projet WebPartNode, ouvrez le **source.extension.vsixmanifest** fichier dans l’éditeur de manifeste.  
  
     Le fichier source.extension.vsixmanifest est la base du fichier extension.vsixmanifest qui nécessitent de tous les packages VSIX. Pour plus d’informations sur ce fichier, consultez [une Extension de schéma 1.0 référence VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Dans le **Product Name** , entrez **nœud Galerie de composants WebPart pour l’Explorateur de serveurs**.  
  
3.  Dans le **auteur** , entrez **Contoso**.  
  
4.  Dans le **Description** , entrez **ajoute un nœud personnalisé de la galerie de composants WebPart au nœud Connexions SharePoint dans l’Explorateur de serveurs. Cette extension utilise une commande SharePoint personnalisée pour appeler le modèle d’objet serveur.**  
  
5.  Choisissez le **actifs** onglet de l’éditeur, puis choisissez le **nouveau** bouton.  
  
     Le **ajouter un nouveau composant** boîte de dialogue s’affiche.  
  
6.  Dans le **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à la `MefComponent` élément dans le fichier extension.vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MEFComponent, élément (schéma VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Dans le **Source** , choisissez **un projet dans la solution actuelle**.  
  
8.  Dans le **projet** , choisissez **WebPartNodeExtension** , puis choisissez le **OK** bouton.  
  
9. Dans l’éditeur de manifeste, choisissez le **nouveau** bouton Nouveau.  
  
     Le **ajouter un nouveau composant** boîte de dialogue s’affiche.  
  
10. Dans le **Type** , entrez **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Cet élément spécifie une extension personnalisée que vous souhaitez inclure dans l’extension de Visual Studio. Pour plus d’informations, consultez [Asset, élément (schéma VSX)](http://msdn.microsoft.com/en-us/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. Dans le **Source** , choisissez le **un projet dans la solution actuelle** élément de liste.  
  
12. Dans le **projet** , choisissez **WebPartCommands**, puis choisissez le **OK** bouton.  
  
13. Dans la barre de menus, choisissez **générer**, **générer la Solution**, puis assurez-vous que la solution est compilée sans erreur.  
  
14. Assurez-vous que le dossier de sortie de génération pour le projet WebPartNode contienne désormais le fichier WebPartNode.vsix.  
  
     Par défaut, le dossier de sortie est le... dossier \bin\debug sous le dossier qui contient votre fichier projet.  
  
## <a name="testing-the-extension"></a>Test de l’Extension  
 Vous êtes maintenant prêt à tester la nouvelle **galerie de composants WebPart** nœud **l’Explorateur de serveurs**. Tout d’abord, démarrez le débogage de l’extension dans une instance expérimentale de Visual Studio. Ensuite, utilisez la nouvelle **WebPart** nœud dans l’instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-start-debugging-the-extension"></a>Pour démarrer le débogage de l’extension  
  
1.  Redémarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] avec les informations d’identification administratives, puis ouvrez la solution WebPartNode.  
  
2.  Dans le projet WebPartNodeExtension, ouvrez le fichier de code SiteNodeExtension et puis ajoutez un point d’arrêt à la première ligne de code dans le `NodeChildrenRequested` et `CreateWebPartNodes` méthodes.  
  
3.  Appuyez sur la touche F5 pour démarrer le débogage.  
  
     Visual Studio installe l’extension %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Extension du nœud Galerie partie pour le serveur Explorer\1.0 et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Pour tester l’extension  
  
1.  Dans l’instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dans la barre de menus, choisissez **vue**, **l’Explorateur de serveurs**.  
  
2.  Les étapes suivantes si le site SharePoint que vous souhaitez utiliser pour le test n’apparaît pas sous le **connexions SharePoint** nœud **l’Explorateur de serveurs**:  
  
    1.  Dans **l’Explorateur de serveurs**, ouvrez le menu contextuel pour **connexions SharePoint**, puis choisissez **ajouter une connexion**.  
  
    2.  Dans le **ajouter une connexion SharePoint** boîte de dialogue, entrez l’URL du site SharePoint auquel vous souhaitez vous connecter, puis choisissez le **OK** bouton.  
  
         Pour spécifier le site SharePoint sur votre ordinateur de développement, entrez **http://localhost**.  
  
3.  Développez le nœud de connexion de site (qui affiche l’URL de votre site), puis développez un nœud de site enfant (par exemple, **Site d’équipe**).  
  
4.  Vérifiez que le code dans l’autre instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] s’arrête sur le point d’arrêt défini précédemment dans le `NodeChildrenRequested` (méthode) et appuyez sur F5 pour continuer à déboguer le projet.  
  
5.  Dans l’instance expérimentale de Visual Studio, vérifiez qu’un nouveau nœud nommé **galerie de composants WebPart** apparaît sous le nœud de site de niveau supérieur, puis cliquez sur le **galerie de composants WebPart** nœud.  
  
6.  Vérifiez que le code dans l’autre instance de Visual Studio s’arrête au point d’arrêt défini précédemment dans le `CreateWebPartNodes` (méthode), puis choisissez la touche F5 pour continuer à déboguer le projet.  
  
7.  Dans l’instance expérimentale de Visual Studio, vérifiez que tous les composants WebPart sur le site connecté s’affichent sous la **galerie de composants WebPart** nœud **l’Explorateur de serveurs**.  
  
8.  Dans **l’Explorateur de serveurs**, ouvrez le menu contextuel pour un des composants WebPart, puis choisissez **propriétés**.  
  
9. Dans l’instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que vous déboguez, vérifiez que les détails de la partie Web apparaissent dans le **propriétés** fenêtre.  
  
## <a name="uninstalling-the-extension-from-visual-studio"></a>Désinstallation de l’Extension à partir de Visual Studio  
 Une fois que vous avez terminé le test de l’extension, désinstallez l’extension de Visual Studio.  
  
#### <a name="to-uninstall-the-extension"></a>Pour désinstaller l'extension  
  
1.  Dans l’instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], dans la barre de menus, choisissez **outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s’ouvre.  
  
2.  Dans la liste des extensions, choisissez **Extension du nœud Galerie de composants WebPart pour l’Explorateur de serveurs**, puis choisissez le **désinstallation** bouton.  
  
3.  Dans la boîte de dialogue qui s’affiche, choisissez le **Oui** pour confirmer que vous voulez désinstaller l’extension, puis choisissez le **redémarrer maintenant** bouton pour terminer la désinstallation.  
  
4.  Fermez les deux instances de Visual Studio (l’instance expérimentale et l’instance de Visual Studio dans laquelle la solution WebPartNode est ouverte).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension du nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Procédure pas à pas : Appel dans le modèle d’objet Client SharePoint dans une Extension de l’Explorateur de serveurs](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)   
 [Éditeur d’images pour les icônes](/cpp/windows/image-editor-for-icons)   
 [Création d’une icône ou autre Image &#40; Éditeur d’images pour les icônes &#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)  
  
  