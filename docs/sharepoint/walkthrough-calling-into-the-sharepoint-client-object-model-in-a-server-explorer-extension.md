---
title: 'Explorateur de serveurs : Extension du nœud Connexions SharePoint'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bf3d39a8a06a59ed337c0d847bb92875f0f68558
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824164"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Procédure pas à pas : Appel dans le modèle d’objet client SharePoint dans une extension de l’Explorateur de serveurs
  Cette procédure pas à pas montre comment appeler le modèle d’objet client SharePoint à partir d’une extension pour le **connexions SharePoint** nœud **Explorateur de serveurs**. Pour plus d’informations sur l’utilisation du modèle d’objet client SharePoint, consultez [appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension étend la **connexions SharePoint** nœud de **Explorateur de serveurs** comme suit :

  - L’extension ajoute un **galerie de composants WebPart** nœud sous chaque nœud de site SharePoint dans **Explorateur de serveurs**. Ce nouveau nœud contient des nœuds enfants représentant chaque composant WebPart dans la galerie de composant WebPart sur le site.

  - L’extension définit un nouveau type de nœud qui représente une instance de composant WebPart. Ce nouveau type de nœud sert de base pour les nœuds enfants sous le nouveau **galerie de composants WebPart** nœud. Le nouveau type de nœud WebPart affiche des informations dans le **propriétés** fenêtre sur le composant WebPart que le nœud représente.

- Création d’un package d’Extension Visual Studio (VSIX) pour déployer l’extension.

- Débogage et test de l’extension.

> [!NOTE]
> L’extension que vous créez dans cette procédure pas à pas ressemble à l’extension que vous créez dans [procédure pas à pas : Étendre l’Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). Cette procédure pas à pas utilise le modèle d’objet serveur SharePoint, mais cette procédure pas à pas effectue les mêmes tâches à l’aide du modèle objet client.

## <a name="prerequisites"></a>Prérequis
 Vous avez besoin des composants suivants sur l’ordinateur de développement pour effectuer cette procédure pas à pas :

- Éditions prises en charge de Windows, SharePoint et Visual Studio.

- Le Kit de développement logiciel avec Visual Studio. Cette procédure pas à pas utilise le **projet VSIX** modèle dans le Kit de développement logiciel pour créer un package VSIX pour déployer l’extension. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

Connaissance des concepts suivants est utile, mais pas obligatoire, pour suivre la procédure pas à pas :

- À l’aide du modèle d’objet client SharePoint. Pour plus d’informations, consultez [modèle objet Client managé](http://go.microsoft.com/fwlink/?LinkId=177797).

- Composants WebPart dans SharePoint. Pour plus d’informations, consultez [Web Parts Overview](http://go.microsoft.com/fwlink/?LinkId=177803).

## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez créer deux projets :

- Un projet VSIX pour créer le package VSIX pour déployer le **Explorateur de serveurs** extension.

- Un projet de bibliothèque de classes qui implémente le **Explorateur de serveurs** extension.

  Démarrer la procédure pas à pas en créant les projets.

#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.

3. Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, puis choisissez **extensibilité**.

    > [!NOTE]
    > Le **extensibilité** nœud est disponible uniquement si vous installez le SDK Visual Studio. Pour plus d’informations, consultez la section conditions préalables plus haut dans cette rubrique.

4. En haut de la boîte de dialogue, choisissez **.NET Framework 4.5** dans la liste des versions du .NET Framework.

     Extensions de l’outil SharePoint nécessitent des fonctionnalités dans cette version du .NET Framework.

5. Choisissez le **projet VSIX** modèle.

6. Dans le **nom** , tapez **WebPartNode**, puis choisissez le **OK** bouton.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **WebPartNode** projet **l’Explorateur de solutions**.

#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension

1. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud de solution, choisissez **ajouter**, puis choisissez **nouveau projet**.

2. Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, puis choisissez **Windows**.

3. En haut de la boîte de dialogue, choisissez **.NET Framework 4.5** dans la liste des versions du .NET Framework.

4. Dans la liste des modèles de projet, choisissez **bibliothèque de classes**.

5. Dans le **nom** , entrez **WebPartNodeExtension**, puis choisissez le **OK** bouton.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **WebPartNodeExtension** projet à la solution et ouvre le fichier de code Class1 par défaut.

6. Supprimer le fichier de code Class1 du projet.

## <a name="configure-the-extension-project"></a>Configurer le projet d’extension
 Avant d’écrire du code pour créer l’extension, vous devez ajouter les fichiers de code et des références d’assembly à votre projet, et vous devez mettre à jour l’espace de noms par défaut.

#### <a name="to-configure-the-project"></a>Pour configurer le projet

1. Dans le **WebPartNodeExtension** de projet, ajoutez deux fichiers de code sont nommés SiteNodeExtension et WebPartNodeTypeProvider.

2. Ouvrez le menu contextuel du projet WebPartNodeExtension, puis choisissez **ajouter une référence**.

3. Dans le **Gestionnaire de références - WebPartNodeExtension** boîte de dialogue, sélectionnez le **Framework** nœud et sélectionnez les cases à cocher pour le System.ComponentModel.Composition et System.Windows.Forms assemblys.

4. Choisissez le **Extensions** nœud, sélectionnez la case à cocher pour chacun des assemblys suivants, puis choisissez le **OK** bouton :

    - Microsoft.SharePoint.Client

    - Microsoft.SharePoint.Client.Runtime

    - Microsoft.VisualStudio.SharePoint

5. Ouvrez le menu contextuel pour le **WebPartNodeExtension** de projet, puis choisissez **propriétés**.

     Le **Concepteur de projets** s’ouvre.

6. Choisissez l’onglet **Application**.

7. Dans le **par défaut d’espace de noms** boîte (c#) ou **espace de noms racine** (Visual Basic), entrez **ServerExplorer.SharePointConnections.WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Créer des icônes pour les nouveaux nœuds
 Créez deux icônes pour le **Explorateur de serveurs** extension : une icône pour le nouveau **galerie de composants WebPart** nœud et une autre icône pour chaque nœud de composant WebPart enfant sous le **galerie de composants WebPart** nœud. Plus loin dans cette procédure pas à pas, vous allez écrire du code qui associe ces icônes avec les nœuds.

#### <a name="to-create-icons-for-the-nodes"></a>Pour créer des icônes pour les nœuds

1. Dans le **Concepteur de projets** pour le projet WebPartNodeExtension, choisissez le **ressources** onglet.

2. Cliquez sur le lien **ce projet ne contient pas un fichier de ressources par défaut. Cliquez ici pour en créer un.**

     Visual Studio crée un fichier de ressources et l’ouvre dans le concepteur.

3. En haut du concepteur, cliquez sur la flèche sur la **ajouter une ressource** menu de commande, puis choisissez **ajouter une nouvelle icône**.

4. Entrez **WebPartsNode** pour l’icône nouveau nom, puis choisissez le **ajouter** bouton.

     La nouvelle icône s’ouvre dans le **Éditeur d’images**.

5. Modifier la version 16 x 16 de l’icône afin qu’il dispose d’une conception que vous pouvez identifier facilement.

6. Ouvrez le menu contextuel pour la version 32 x 32 de l’icône, puis choisissez **supprimer le Type d’Image**.

7. Répétez les étapes 3 à 7 pour ajouter une deuxième icône aux ressources du projet et nommez cette icône **WebPart**.

8. Dans **l’Explorateur de solutions**, dans le **ressources** dossier pour le **WebPartNodeExtension** de projet, choisissez *WebPartsNode.ico*.

9. Dans le **propriétés** fenêtre, ouvrez le **Action de génération** liste, puis choisissez **ressource incorporée**.

10. Répétez les deux dernières étapes pour *WebPart.ico*.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Ajouter le nœud Galerie de composants WebPart à l’Explorateur de serveurs
 Créez une classe qui ajoute le nouveau **galerie de composants WebPart** nœud pour chaque nœud de site SharePoint. Pour ajouter le nouveau nœud, la classe implémente le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interface. Implémentez cette interface chaque fois que vous souhaitez étendre le comportement d’un nœud existant dans **Explorateur de serveurs**, telles que l’ajout d’un nouveau nœud enfant à un nœud.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Pour ajouter le nœud Galerie de composants WebPart à l’Explorateur de serveurs

1. Collez le code suivant dans le **SiteNodeExtension** fichier de code pour le **WebPartNodeExtension** projet.

    > [!NOTE]
    > Après avoir ajouté ce code, le projet aura des erreurs de compilation. Ces erreurs disparaissent lorsque vous ajoutez du code dans les étapes ultérieures.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>Définir un type de nœud qui représente un composant WebPart
 Créez une classe qui définit un nouveau type de nœud qui représente un composant WebPart. Visual Studio utilise ce nouveau type de nœud pour afficher les nœuds enfants sous le **galerie de composants WebPart** nœud. Chacun de ces nœuds enfants représente un composant WebPart sur le site SharePoint.

 Pour définir le nouveau type de nœud, la classe implémente le <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interface. Implémentez cette interface chaque fois que vous souhaitez définir un nouveau type de nœud dans **Explorateur de serveurs**.

#### <a name="to-define-the-web-part-node-type"></a>Pour définir le type de nœud de composant web

1. Collez le code suivant dans le **WebPartNodeTypeProvider** fichier de code pour le **WebPartNodeExtension** projet.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]

## <a name="checkpoint"></a>Point de contrôle
 À ce stade de la procédure pas à pas, tout le code pour le **galerie de composants WebPart** nœud se trouve maintenant dans le projet. Générer le **WebPartNodeExtension** projet pour vous assurer qu’il est compilé sans erreur.

#### <a name="to-build-the-project"></a>Pour générer le projet

1. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **WebPartNodeExtension** de projet, puis choisissez **Build**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Créer un package VSIX pour déployer l’extension
 Pour déployer l’extension, utilisez le projet VSIX dans votre solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest qui est inclus dans le projet. Puis créer le package VSIX en générant la solution.

#### <a name="to-configure-the-vsix-package"></a>Pour configurer le package VSIX

1. Dans **l’Explorateur de solutions**, dans le **WebPartNode** projet, ouvrez **source.extension.vsixmanifest** fichier dans l’éditeur de manifeste.

     Le fichier source.extension.vsixmanifest est la base du fichier extension.vsixmanifest qui nécessitent de tous les packages VSIX. Pour plus d’informations sur ce fichier, consultez [VSIX Extension schéma 1.0 référence](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. Dans le **Product Name** , entrez **nœud Galerie de composants WebPart pour l’Explorateur de serveurs**.

3. Dans le **auteur** , entrez **Contoso**.

4. Dans le **Description** , entrez **ajoute un nœud de galerie de composants WebPart personnalisé au nœud Connexions SharePoint dans l’Explorateur de serveurs**.

5. Sur le **actifs** onglet de l’éditeur, choisissez le **New** bouton.

6. Dans le **ajouter un nouveau composant** boîte de dialogue le **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.

    > [!NOTE]
    > Cette valeur correspond à la `MefComponent` élément dans le fichier extension.vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MEFComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Dans le **Source** , choisissez **un projet dans la solution actuelle**.

8. Dans le **projet** , choisissez **WebPartNodeExtension**, puis choisissez le **OK** bouton.

9. Dans la barre de menus, choisissez **Build** > **générer la Solution**, puis assurez-vous que la solution est compilée sans erreurs.

10. Assurez-vous que le dossier de sortie pour le projet WebPartNode contienne maintenant le fichier WebPartNode.vsix.

     Par défaut, le dossier de sortie est le... dossier \bin\debug sous le dossier qui contient votre fichier projet.

## <a name="test-the-extension"></a>Tester l’extension
 Vous êtes maintenant prêt à tester la nouvelle **galerie de composants WebPart** nœud **Explorateur de serveurs**. Tout d’abord, commencez à déboguer le projet d’extension dans une instance expérimentale de Visual Studio. Puis utilisez la nouvelle **WebPart** nœud dans l’instance expérimentale de Visual Studio.

#### <a name="to-start-debugging-the-extension"></a>Pour démarrer le débogage de l’extension

1. Redémarrez Visual Studio en tant qu’administrateur, puis ouvrez le **WebPartNode** solution.

2. Dans le projet WebPartNodeExtension, ouvrez le **SiteNodeExtension** fichier de code et ajoutez un point d’arrêt pour les premières lignes de code dans le `NodeChildrenRequested` et `CreateWebPartNodes` méthodes.

3. Choisissez le **F5** touche pour démarrer le débogage.

     Visual Studio installe l’extension %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web Extension de nœud de galerie de composants WebPart pour Explorer\1.0 de serveur et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.

#### <a name="to-test-the-extension"></a>Pour tester l’extension

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **vue** > **Explorateur de serveurs**.

2. Vérifiez que le site SharePoint que vous souhaitez utiliser pour le test s’affiche sous le **connexions SharePoint** nœud **Explorateur de serveurs**. S’il n’est pas répertorié, procédez comme suit :

    1. Ouvrez le menu contextuel pour **connexions SharePoint**, puis choisissez **ajouter une connexion**.

    2. Dans le **ajouter une connexion SharePoint** boîte de dialogue, entrez l’URL pour le site SharePoint auquel vous souhaitez vous connecter, puis choisissez le **OK** bouton.

         Pour spécifier le site SharePoint sur votre ordinateur de développement, tapez **http://localhost** .

3. Développez le nœud de connexion de site (qui affiche l’URL de votre site), puis développez un nœud de site enfant (par exemple, **Site d’équipe**).

4. Vérifiez que le code dans l’autre instance de Visual Studio s’arrête au point d’arrêt que vous avez défini précédemment dans le `NodeChildrenRequested` (méthode), puis choisissez le **F5** touche pour continuer à déboguer le projet.

5. Dans l’instance expérimentale de Visual Studio, développez le **galerie de composants WebPart** nœud, ce qui s’affiche sous le nœud de site de niveau supérieur.

6. Vérifiez que le code dans l’autre instance de Visual Studio s’arrête au point d’arrêt que vous avez défini précédemment dans le `CreateWebPartNodes` (méthode), puis choisissez le **F5** touche pour continuer à déboguer le projet.

7. Dans l’instance expérimentale de Visual Studio, vérifiez que tous les composants WebPart sur le site connecté s’affichent sous le **galerie de composants WebPart** nœud **Explorateur de serveurs**.

8. Ouvrez le menu contextuel pour un composant WebPart, puis choisissez **propriétés**.

9. Dans le **propriétés** fenêtre, vérifiez que plus d’informations sur le composant WebPart s’affichent.

10. Dans **Explorateur de serveurs**, ouvrez le menu contextuel pour le même composant WebPart, puis choisissez **afficher un Message**.

     Dans la boîte de message qui s’affiche, choisissez le **OK** bouton.

## <a name="uninstall-the-extension-from-visual-studio"></a>Désinstallez l’extension de Visual Studio
 Une fois que vous avez terminé le test de l’extension, désinstallez-le à partir de Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Pour désinstaller l'extension

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **outils** > **Extensions et mises à jour**.

     La boîte de dialogue **Extensions et mises à jour** s’ouvre.

2. Dans la liste des extensions, choisissez **nœud Galerie de composants WebPart pour l’Explorateur de serveurs**, puis choisissez le **désinstallation** bouton.

3. Dans la boîte de dialogue qui s’affiche, choisissez le **Oui** bouton.

4. Choisissez le **redémarrer maintenant** bouton pour terminer la désinstallation.

     L’élément de projet est également désinstallé.

5. Fermez les deux instances de Visual Studio (l’instance expérimentale et l’instance de Visual Studio dans laquelle la solution WebPartNode est ouverte).

## <a name="see-also"></a>Voir aussi
- [Appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procédure pas à pas : Étendre l’Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Éditeur d’images pour les icônes](/cpp/windows/image-editor-for-icons)
- [Création d’une icône ou une autre Image &#40;Éditeur d’images pour les icônes&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
