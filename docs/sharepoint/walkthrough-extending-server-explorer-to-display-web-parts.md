---
title: 'Procédure pas à pas : extension de Explorateur de serveurs pour afficher composants WebPart | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e5221d1cce065a352051ca700cf0fc5ef4ae843
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015630"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>Procédure pas à pas : étendre Explorateur de serveurs pour afficher des composants WebPart
  Dans Visual Studio, vous pouvez utiliser le nœud **Connexions SharePoint** de **Explorateur de serveurs** pour afficher les composants sur les sites SharePoint. Toutefois, **Explorateur de serveurs** n’affiche pas certains composants par défaut. Dans cette procédure pas à pas, vous allez étendre **Explorateur de serveurs** afin qu’il affiche la Galerie de composants WebPart sur chaque site SharePoint connecté.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’une extension Visual Studio qui étend **Explorateur de serveurs** des manières suivantes :

  - L’extension ajoute un nœud de **Galerie de composants WebPart** sous chaque nœud de site SharePoint dans **Explorateur de serveurs**. Ce nouveau nœud contient des nœuds enfants qui représentent chaque composant WebPart dans la Galerie de composants WebPart sur le site.

  - L’extension définit un nouveau type de nœud qui représente une instance de composant WebPart. Ce nouveau type de nœud est la base des nœuds enfants sous le nouveau nœud **Galerie de composants WebPart** . Le nouveau type de nœud WebPart affiche des informations dans la fenêtre **Propriétés** sur le composant WebPart qu’il représente. Le type de nœud comprend également un élément de menu contextuel personnalisé que vous pouvez utiliser comme point de départ pour effectuer d’autres tâches relatives au composant WebPart.

- Créez deux commandes SharePoint personnalisées appelées par l’assembly d’extension. Les commandes SharePoint sont des méthodes qui peuvent être appelées par des assemblys d’extension pour utiliser des API dans le modèle d’objet serveur pour SharePoint. Dans cette procédure pas à pas, vous allez créer des commandes qui récupèrent des informations WebPart à partir du site SharePoint local sur l’ordinateur de développement. Pour plus d’informations, consultez [appel des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Génération d’un package d’extension Visual Studio (VSIX) pour déployer l’extension.

- Débogage et test de l’extension.

> [!NOTE]
> Pour obtenir une autre version de cette procédure pas à pas qui utilise le modèle d’objet client pour SharePoint au lieu de son modèle d’objet serveur, consultez [procédure pas à pas : appeler le modèle d’objet client SharePoint dans une extension de Explorateur de serveurs](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="prerequisites"></a>Prérequis
 Pour effectuer cette procédure pas à pas, vous avez besoin des composants suivants sur l’ordinateur de développement :

- Éditions prises en charge de Windows, SharePoint et Visual Studio.

- Le kit de développement logiciel (SDK) Visual Studio. Cette procédure pas à pas utilise le modèle de **projet VSIX** dans le kit de développement logiciel (SDK) pour créer un package VSIX afin de déployer l’élément de projet. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer la procédure pas à pas :

- Utilisation du modèle d’objet serveur pour SharePoint. Pour plus d’informations, consultez [utilisation du modèle objet côté serveur SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- Composants WebPart dans les solutions SharePoint. Pour plus d’informations, consultez [composants WebPart vue d’ensemble](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez créer trois projets :

- Projet VSIX pour créer le package VSIX pour déployer l’extension.

- Projet de bibliothèque de classes qui implémente l’extension. Ce projet doit cibler le .NET Framework 4,5.

- Projet de bibliothèque de classes qui définit les commandes SharePoint personnalisées. Ce projet doit cibler the.NET Framework 3,5.

  Démarrez la procédure pas à pas en créant les projets.

#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

3. Dans la boîte de dialogue  **nouveau projet** , développez les nœuds **Visual C#** ou **Visual Basic** , puis choisissez le nœud **extensibilité** .

    > [!NOTE]
    > Le nœud **extensibilité** est disponible uniquement si vous installez le kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez la section conditions préalables, plus haut dans cette rubrique.

4. En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework.

5. Choisissez le modèle de **projet VSIX** , nommez le projet **WebPartNode**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **WebPartNode** à **Explorateur de solutions**.

#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud solution, choisissez **Ajouter**, puis **nouveau projet**.

2. Dans la boîte de dialogue **nouveau projet** , développez le nœud **Visual C#** ou **Visual Basic** nœud, puis le nœud choisir **Windows** .

3. En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework.

4. Dans la liste des modèles de projet, choisissez **bibliothèque de classes**, nommez le projet **WebPartNodeExtension**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **WebPartNodeExtension** à la solution et ouvre le fichier de code Class1 par défaut.

5. Supprimez le fichier de code Class1 du projet.

#### <a name="to-create-the-sharepoint-commands-project"></a>Pour créer le projet de commandes SharePoint

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud solution, choisissez **Ajouter**, puis **nouveau projet**.

2. Dans la boîte de dialogue  **nouveau projet** , développez le nœud **Visual C#** ou **Visual Basic** nœud, puis choisissez le nœud **Windows** .

3. En haut de la boîte de dialogue, choisissez **.NET Framework 3,5** dans la liste des versions du .NET Framework.

4. Dans la liste des modèles de projet, choisissez **bibliothèque de classes**, nommez le projet **WebPartCommands**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **WebPartCommands** à la solution et ouvre le fichier de code Class1 par défaut.

5. Supprimez le fichier de code Class1 du projet.

## <a name="configure-the-projects"></a>Configurer les projets
 Avant d’écrire du code pour créer l’extension, vous devez ajouter des fichiers de code et des références d’assembly, et configurer les paramètres du projet.

#### <a name="to-configure-the-webpartnodeextension-project"></a>Pour configurer le projet WebPartNodeExtension

1. Dans le projet WebPartNodeExtension, ajoutez quatre fichiers de code portant les noms suivants :

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. Ouvrez le menu contextuel du projet **WebPartNodeExtension** , puis choisissez **Ajouter une référence**.

3. Dans la boîte de dialogue **Gestionnaire de références-WebPartNodeExtension** , choisissez l’onglet **Framework** , puis activez la case à cocher pour chacun des assemblys suivants :

    - System.ComponentModel.Composition

    - System.Windows.Forms

4. Choisissez l’onglet **Extensions** , activez la case à cocher de l’assembly Microsoft. VisualStudio. SharePoint, puis choisissez le bouton **OK** .

5. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **WebPartNodeExtension** , puis choisissez **Propriétés**.

     Le **Concepteur de projets** s’ouvre.

6. Choisissez l’onglet **Application**.

7. Dans la zone **espace de noms par défaut** (C#) ou **espace de noms racine** ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ), entrez **ServerExplorer. SharePointConnections. WebPartNode**.

#### <a name="to-configure-the-webpartcommands-project"></a>Pour configurer le projet WebPartCommands

1. Dans le projet WebPartCommands, ajoutez un fichier de code nommé WebPartCommands.

2. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **WebPartCommands** , choisissez **Ajouter**, puis **élément existant**.

3. Dans la boîte de dialogue **Ajouter un élément existant** , accédez au dossier qui contient les fichiers de code du projet WebPartNodeExtension, puis choisissez les fichiers de code WebPartNodeInfo et WebPartCommandIds.

4. Cliquez sur la flèche en regard du bouton **Ajouter** , puis choisissez **Ajouter en tant que lien** dans le menu qui s’affiche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute les fichiers de code au projet WebPartCommands sous forme de liens. Par conséquent, les fichiers de code se trouvent dans le projet WebPartNodeExtension, mais le code des fichiers est également compilé dans le projet WebPartCommands.

5. Rouvrez le menu contextuel du projet **WebPartCommands** , puis choisissez **Ajouter une référence**.

6. Dans la boîte de dialogue **Gestionnaire de références-WebPartCommands** , choisissez l’onglet **Extensions** , activez la case à cocher pour chacun des assemblys suivants, puis choisissez le bouton **OK** :

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

7. Dans **Explorateur de solutions**, ouvrez à nouveau le menu contextuel du projet **WebPartCommands** , puis choisissez **Propriétés**.

     Le **Concepteur de projets** s’ouvre.

8. Choisissez l’onglet **Application**.

9. Dans la zone **espace de noms par défaut** (C#) ou **espace de noms racine** ( [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ), entrez **ServerExplorer. SharePointConnections. WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Créer des icônes pour les nouveaux nœuds
 Créez deux icônes pour l’extension de **Explorateur de serveurs** : une icône pour le nouveau nœud de la **Galerie de composants WebPart** , et une autre icône pour chaque nœud de composant WebPart enfant sous le nœud **Galerie de composants WebPart** . Plus loin dans cette procédure pas à pas, vous allez écrire du code qui associe ces icônes aux nœuds.

#### <a name="to-create-icons-for-the-nodes"></a>Pour créer des icônes pour les nœuds

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **WebPartNodeExtension** , puis choisissez **Propriétés**.

2. Le **Concepteur de projets** s’ouvre.

3. Choisissez l’onglet **ressources** , puis choisissez le **fichier ce projet ne contient pas de fichier de ressources par défaut. Cliquez ici pour créer un** lien.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée un fichier de ressources et l’ouvre dans le concepteur.

4. En haut du concepteur, cliquez sur la flèche en regard de la commande de menu **Ajouter une ressource** , puis choisissez **Ajouter une nouvelle icône** dans le menu qui s’affiche.

5. Dans la boîte de dialogue **Ajouter une nouvelle ressource** , nommez la nouvelle icône **WebPartsNode**, puis cliquez sur le bouton **Ajouter** .

     La nouvelle icône s’ouvre dans l' **éditeur d’images**.

6. Modifiez la version 16x16 de l’icône afin qu’elle dispose d’une conception que vous pouvez facilement reconnaître.

7. Ouvrez le menu contextuel de la version 32x32 de l’icône, puis choisissez **supprimer le type d’image**.

8. Répétez les étapes 5 à 8 pour ajouter une deuxième icône aux ressources du projet, puis nommez cette icône **WebPart**.

9. Dans **Explorateur de solutions**, sous le dossier **ressources** du projet **WebPartNodeExtension** , ouvrez le menu contextuel de **WebPartsNode. ico**.

10. Dans la fenêtre **Propriétés** , cliquez sur la flèche en regard de **action de génération**, puis sélectionnez **ressource incorporée** dans le menu qui s’affiche.

11. Répétez les deux dernières étapes pour **WebPart. ico**.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Ajoutez le nœud Galerie de composants WebPart à Explorateur de serveurs
 Créez une classe qui ajoute le nouveau nœud de la **Galerie de composants WebPart** à chaque nœud de site SharePoint. Pour ajouter le nouveau nœud, la classe implémente l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interface. Implémentez cette interface chaque fois que vous souhaitez étendre le comportement d’un nœud existant dans **Explorateur de serveurs**, tel que l’ajout d’un nœud enfant à un nœud.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Pour ajouter le nœud Galerie de composants WebPart à Explorateur de serveurs

1. Dans le projet WebPartNodeExtension, ouvrez le fichier de code SiteNodeExtension, puis collez-y le code suivant.

    > [!NOTE]
    > Une fois que vous avez ajouté ce code, le projet rencontre des erreurs de compilation, mais il disparaît lorsque vous ajoutez du code dans les étapes ultérieures.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Définir un type de nœud qui représente un composant WebPart
 Créez une classe qui définit un nouveau type de nœud qui représente un composant WebPart. Visual Studio utilise ce nouveau type de nœud pour afficher les nœuds enfants sous le nœud **Galerie de composants WebPart** . Chaque nœud enfant représente un composant WebPart unique sur le site SharePoint.

 Pour définir le nouveau type de nœud, la classe implémente l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interface. Implémentez cette interface chaque fois que vous souhaitez définir un nouveau type de nœud dans **Explorateur de serveurs**.

#### <a name="to-define-the-web-part-node-type"></a>Pour définir le type de nœud WebPart

1. Dans le projet WebPartNodeExtension, ouvrez le fichier de code WebPartNodeTypeProvder, puis collez-y le code suivant.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>Définir la classe de données WebPart
 Définissez une classe qui contient des données relatives à un composant WebPart unique sur le site SharePoint. Plus loin dans cette procédure pas à pas, vous allez créer une commande SharePoint personnalisée qui récupère les données relatives à chaque composant WebPart sur le site, puis assigne les données aux instances de cette classe.

#### <a name="to-define-the-web-part-data-class"></a>Pour définir la classe de données WebPart

1. Dans le projet WebPartNodeExtension, ouvrez le fichier de code WebPartNodeInfo, puis collez-y le code suivant.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>Définir les ID des commandes SharePoint
 Définissez plusieurs chaînes qui identifient les commandes SharePoint personnalisées. Vous allez implémenter ces commandes plus loin dans cette procédure pas à pas.

#### <a name="to-define-the-command-ids"></a>Pour définir les ID de commande

1. Dans le projet WebPartNodeExtension, ouvrez le fichier de code WebPartCommandIds, puis collez-y le code suivant.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>Créer les commandes SharePoint personnalisées
 Créez des commandes personnalisées qui appellent le modèle objet serveur pour SharePoint pour récupérer des données sur le composants WebPart sur le site SharePoint. Chaque commande est une méthode à laquelle est <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> appliqué.

#### <a name="to-define-the-sharepoint-commands"></a>Pour définir les commandes SharePoint

1. Dans le projet WebPartCommands, ouvrez le fichier de code WebPartCommands, puis collez le code suivant dans celui-ci.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>Point de contrôle
 À ce stade de la procédure pas à pas, tout le code pour le nœud de la **Galerie de composants WebPart** et les commandes SharePoint se trouvent maintenant dans les projets. Générez la solution pour vous assurer que les deux projets se compilent sans erreur.

#### <a name="to-build-the-solution"></a>Pour générer la solution

1. Dans la barre de menus, choisissez **générer**  >  **générer la solution**.

    > [!WARNING]
    > À ce stade, le projet WebPartNode peut avoir une erreur de génération, car le fichier manifeste VSIX n’a pas de valeur pour Author. Cette erreur disparaît lorsque vous ajoutez une valeur dans les étapes ultérieures.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Créer un package VSIX pour déployer l’extension
 Pour déployer l’extension, utilisez le projet VSIX dans votre solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source. extension. vsixmanifest dans le projet VSIX. Ensuite, créez le package VSIX en générant la solution.

#### <a name="to-configure-the-vsix-package"></a>Pour configurer le package VSIX

1. Dans **Explorateur de solutions**, sous le projet WebPartNode, ouvrez le fichier **source. extension. vsixmanifest** dans l’éditeur de manifeste.

     Le fichier source. extension. vsixmanifest est la base du fichier extension. vsixmanifest requis par tous les packages VSIX. Pour plus d’informations sur ce fichier, consultez [Référence du schéma d’extension VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. Dans la zone **nom du produit** , entrez **nœud de la Galerie de composants webpart pour Explorateur de serveurs**.

3. Dans la zone **auteur** , entrez **contoso**.

4. Dans la zone **Description** , entrez **ajoute un nœud de Galerie de composants WebPart personnalisé au nœud connexions SharePoint dans Explorateur de serveurs. Cette extension utilise une commande SharePoint personnalisée pour appeler le modèle d’objet serveur.**

5. Choisissez l’onglet **ressources** de l’éditeur, puis choisissez le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’affiche.

6. Dans la liste **type** , choisissez **Microsoft. VisualStudio. MEFComponent**.

    > [!NOTE]
    > Cette valeur correspond à l' `MefComponent` élément dans le fichier extension. vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MefComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Dans la liste  **source** , choisissez **un projet dans la solution actuelle**.

8. Dans la liste **projet** , choisissez **WebPartNodeExtension** , puis cliquez sur le bouton **OK** .

9. Dans l’éditeur de manifeste, cliquez à nouveau sur le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’affiche.

10. Dans la zone **type** , entrez **SharePoint. Commands. v4**.

    > [!NOTE]
    > Cet élément spécifie une extension personnalisée que vous souhaitez inclure dans l’extension Visual Studio. Pour plus d’informations, consultez [élément Asset (schéma VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

11. Dans la liste **source** , choisissez l’élément de liste **un projet dans la solution actuelle** .

12. Dans la liste **projet** , choisissez **WebPartCommands**, puis choisissez le bouton **OK** .

13. Dans la barre de menus, choisissez **générer**  >  **générer la solution**, puis assurez-vous que la solution est compilée sans erreur.

14. Assurez-vous que le dossier de sortie de la génération pour le projet WebPartNode contient maintenant le fichier WebPartNode. vsix.

     Par défaut, le dossier de sortie de la génération est le.. dossier \bin\Debug sous le dossier qui contient votre fichier projet.

## <a name="test-the-extension"></a>Tester l’extension
 Vous êtes maintenant prêt à tester le nouveau nœud de la **Galerie de composants WebPart** dans **Explorateur de serveurs**. Tout d’abord, commencez à déboguer l’extension dans une instance expérimentale de Visual Studio. Ensuite, utilisez le nouveau nœud **composants WebPart** dans l’instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-start-debugging-the-extension"></a>Pour démarrer le débogage de l’extension

1. Redémarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] avec les informations d’identification d’administration, puis ouvrez la solution WebPartNode.

2. Dans le projet WebPartNodeExtension, ouvrez le fichier de code SiteNodeExtension, puis ajoutez un point d’arrêt à la première ligne de code dans les `NodeChildrenRequested` `CreateWebPartNodes` méthodes et.

3. Appuyez sur la touche **F5** pour démarrer le débogage.

     Visual Studio installe l’extension de l’extension de nœud de la Galerie de composants%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web pour le serveur Explorer\1.0 et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.

#### <a name="to-test-the-extension"></a>Pour tester l’extension

1. Dans l’instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , dans la barre de menus, choisissez **Afficher**  >  **Explorateur de serveurs**.

2. Si le site SharePoint que vous souhaitez utiliser pour le test n’apparaît pas sous le nœud **Connexions SharePoint** dans **Explorateur de serveurs**, procédez comme suit :

    1. Dans **Explorateur de serveurs**, ouvrez le menu contextuel des **Connexions SharePoint**, puis choisissez **Ajouter une connexion**.

    2. Dans la boîte de dialogue **Ajouter une connexion SharePoint** , entrez l’URL du site SharePoint auquel vous souhaitez vous connecter, puis choisissez le bouton **OK** .

         Pour spécifier le site SharePoint sur votre ordinateur de développement, entrez **http://localhost** .

3. Développez le nœud connexion au site (qui affiche l’URL de votre site), puis développez un nœud de site enfant (par exemple, **site d’équipe**).

4. Vérifiez que le code de l’autre instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] s’arrête sur le point d’arrêt que vous avez défini précédemment dans la méthode, puis appuyez sur `NodeChildrenRequested` **F5** pour continuer à déboguer le projet.

5. Dans l’instance expérimentale de Visual Studio, vérifiez qu’un nouveau nœud nommé **Galerie de composants WebPart** apparaît sous le nœud de site de niveau supérieur, puis développez le nœud **Galerie de composants WebPart** .

6. Vérifiez que le code de l’autre instance de Visual Studio s’arrête sur le point d’arrêt que vous avez défini précédemment dans la méthode, puis appuyez sur `CreateWebPartNodes` la touche **F5** pour continuer à déboguer le projet.

7. Dans l’instance expérimentale de Visual Studio, vérifiez que tous les composants WebPart sur le site connecté s’affichent sous le nœud **Galerie de composants WebPart** dans **Explorateur de serveurs**.

8. Dans **Explorateur de serveurs**, ouvrez le menu contextuel de l’un des composants WebPart, puis choisissez **Propriétés**.

9. Dans l’instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] que vous déboguez, vérifiez que les détails sur le composant WebPart s’affichent dans la fenêtre **Propriétés** .

## <a name="uninstall-the-extension-from-visual-studio"></a>Désinstaller l’extension de Visual Studio
 Une fois que vous avez fini de tester l’extension, désinstallez l’extension de Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Pour désinstaller l'extension

1. Dans l’instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , dans la barre de menus, choisissez **Outils**  >  **extensions et mises à jour**.

     La boîte de dialogue **Extensions et mises à jour** s’ouvre.

2. Dans la liste des extensions, choisissez **extension de nœud de la Galerie de composants WebPart pour Explorateur de serveurs**, puis choisissez le bouton **désinstaller** .

3. Dans la boîte de dialogue qui s’affiche, choisissez le bouton **Oui** pour confirmer que vous souhaitez désinstaller l’extension, puis cliquez sur le bouton **redémarrer maintenant** pour terminer la désinstallation.

4. Fermez les deux instances de Visual Studio (l’instance expérimentale et l’instance de Visual Studio dans laquelle la solution WebPartNode est ouverte).

## <a name="see-also"></a>Voir aussi
- [Étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procédure pas à pas : appel du modèle d’objet client SharePoint dans une extension de Explorateur de serveurs](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [Éditeur d’images pour les icônes](/cpp/windows/image-editor-for-icons)
- [Création d’une icône ou d’une autre image &#40;éditeur d’images pour les icônes&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
