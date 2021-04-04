---
title: 'Explorateur de serveurs : extension du nœud Connexions SharePoint'
titleSuffix: ''
description: Dans cette procédure pas à pas, consultez Comment appeler le modèle d’objet client SharePoint à partir d’une extension pour le nœud Connexions SharePoint dans Explorateur de serveurs.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dee53642e042c8d4db88bdba7c093f327527798d
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217019"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>Procédure pas à pas : appel du modèle d’objet client SharePoint dans une extension de Explorateur de serveurs
  Cette procédure pas à pas montre comment appeler le modèle d’objet client SharePoint à partir d’une extension pour le nœud **Connexions SharePoint** dans **Explorateur de serveurs**. Pour plus d’informations sur l’utilisation du modèle d’objet client SharePoint, consultez [appel des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’une [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension qui étend le nœud **Connexions SharePoint** de **Explorateur de serveurs** des manières suivantes :

  - L’extension ajoute un nœud de **Galerie de composants WebPart** sous chaque nœud de site SharePoint dans **Explorateur de serveurs**. Ce nouveau nœud contient des nœuds enfants qui représentent chaque composant WebPart dans la Galerie de composants WebPart sur le site.

  - L’extension définit un nouveau type de nœud qui représente une instance de composant WebPart. Ce nouveau type de nœud est la base des nœuds enfants sous le nouveau nœud **Galerie de composants WebPart** . Le nouveau type de nœud WebPart affiche des informations dans la fenêtre **Propriétés** concernant le composant WebPart que le nœud représente.

- Génération d’un package d’extension Visual Studio (VSIX) pour déployer l’extension.

- Débogage et test de l’extension.

> [!NOTE]
> L’extension que vous créez dans cette procédure pas à pas ressemble à l’extension que vous créez dans [procédure pas à pas : étendre Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md). Cette procédure pas à pas utilise le modèle d’objet serveur SharePoint, mais cette procédure pas à pas effectue les mêmes tâches à l’aide du modèle d’objet client.

## <a name="prerequisites"></a>Prérequis
 Pour effectuer cette procédure pas à pas, vous avez besoin des composants suivants sur l’ordinateur de développement :

- Éditions prises en charge de Windows, SharePoint et Visual Studio.

- Le kit de développement logiciel (SDK) Visual Studio. Cette procédure pas à pas utilise le modèle de **projet VSIX** dans le kit de développement logiciel (SDK) pour créer un package VSIX afin de déployer l’extension. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

La connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer la procédure pas à pas :

- Utilisation du modèle d’objet client SharePoint. Pour plus d’informations, consultez [modèle objet client géré](/previous-versions/office/developer/sharepoint-2010/ee537247(v=office.14)).

- Composants WebPart dans SharePoint. Pour plus d’informations, consultez [WebParts vue d’ensemble](/previous-versions/office/ms432401(v=office.14)).

## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez créer deux projets :

- Projet VSIX pour créer le package VSIX pour déployer l’extension de **Explorateur de serveurs** .

- Projet de bibliothèque de classes qui implémente l’extension **Explorateur de serveurs** .

  Démarrez la procédure pas à pas en créant les projets.

#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

3. Dans la boîte de dialogue **nouveau projet** , développez les nœuds **Visual C#** ou **Visual Basic** , puis choisissez **extensibilité**.

    > [!NOTE]
    > Le nœud **extensibilité** est disponible uniquement si vous installez le kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez la section conditions préalables, plus haut dans cette rubrique.

4. En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework.

     Les extensions des outils SharePoint nécessitent des fonctionnalités dans cette version du .NET Framework.

5. Choisissez le modèle de **projet VSIX** .

6. Dans la zone **nom** , tapez **WebPartNode**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **WebPartNode** à **Explorateur de solutions**.

#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud solution, choisissez **Ajouter**, puis **nouveau projet**.

2. Dans la boîte de dialogue  **nouveau projet** , développez les nœuds **Visual C#** ou **Visual Basic** , puis choisissez **Windows**.

3. En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework.

4. Dans la liste des modèles de projet, choisissez **bibliothèque de classes**.

5. Dans la zone **nom** , entrez **WebPartNodeExtension**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **WebPartNodeExtension** à la solution et ouvre le fichier de code Class1 par défaut.

6. Supprimez le fichier de code Class1 du projet.

## <a name="configure-the-extension-project"></a>Configurer le projet d’extension
 Avant d’écrire du code pour créer l’extension, vous devez ajouter des fichiers de code et des références d’assembly à votre projet, et vous devez mettre à jour l’espace de noms par défaut.

#### <a name="to-configure-the-project"></a>Pour configurer le projet

1. Dans le projet **WebPartNodeExtension** , ajoutez deux fichiers de code nommés SiteNodeExtension et WebPartNodeTypeProvider.

2. Ouvrez le menu contextuel du projet WebPartNodeExtension, puis choisissez **Ajouter une référence**.

3. Dans la boîte de dialogue **Gestionnaire de références-WebPartNodeExtension** , choisissez le nœud **Framework** , puis activez les cases à cocher pour les assemblys System. ComponentModel. composition et System. Windows. Forms.

4. Choisissez le nœud **Extensions** , activez la case à cocher pour chacun des assemblys suivants, puis choisissez le bouton **OK** :

    - Microsoft. SharePoint. client

    - Microsoft. SharePoint. client. Runtime

    - Microsoft. VisualStudio. SharePoint

5. Ouvrez le menu contextuel du projet **WebPartNodeExtension** , puis choisissez **Propriétés**.

     Le **Concepteur de projets** s’ouvre.

6. Choisissez l’onglet **Application**.

7. Dans la zone **espace de noms par défaut** (C#) ou **espace de noms racine** (Visual Basic), entrez **ServerExplorer. SharePointConnections. WebPartNode**.

## <a name="create-icons-for-the-new-nodes"></a>Créer des icônes pour les nouveaux nœuds
 Créez deux icônes pour l’extension de **Explorateur de serveurs** : une icône pour le nouveau nœud de la **Galerie de composants WebPart** et une autre icône pour chaque nœud de composant WebPart enfant sous le nœud **Galerie de composants WebPart** . Plus loin dans cette procédure pas à pas, vous écrirez du code qui associe ces icônes aux nœuds.

#### <a name="to-create-icons-for-the-nodes"></a>Pour créer des icônes pour les nœuds

1. Dans le **Concepteur de projet** pour le projet WebPartNodeExtension, choisissez l’onglet **ressources** .

2. Choisissez le lien **ce projet ne contient pas de fichier de ressources par défaut. Cliquez ici pour en créer un.**

     Visual Studio crée un fichier de ressources et l’ouvre dans le concepteur.

3. En haut du concepteur, cliquez sur la flèche de la commande de menu **Ajouter une ressource** , puis choisissez **Ajouter une nouvelle icône**.

4. Entrez **WebPartsNode** pour le nom de la nouvelle icône, puis cliquez sur le bouton **Ajouter** .

     La nouvelle icône s’ouvre dans l' **éditeur d’images**.

5. Modifiez la version 16x16 de l’icône afin qu’elle dispose d’une conception que vous pouvez facilement reconnaître.

6. Ouvrez le menu contextuel de la version 32x32 de l’icône, puis choisissez **supprimer le type d’image**.

7. Répétez les étapes 3 à 7 pour ajouter une deuxième icône aux ressources du projet, puis nommez cette icône **WebPart**.

8. Dans **Explorateur de solutions**, dans le dossier **ressources** du projet **WebPartNodeExtension** , choisissez *WebPartsNode. ico*.

9. Dans la fenêtre **Propriétés** , ouvrez la liste **action de génération** , puis sélectionnez **ressource incorporée**.

10. Répétez les deux dernières étapes pour *WebPart. ico*.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>Ajoutez le nœud Galerie de composants WebPart à Explorateur de serveurs
 Créez une classe qui ajoute le nouveau nœud de la **Galerie de composants WebPart** à chaque nœud de site SharePoint. Pour ajouter le nouveau nœud, la classe implémente l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interface. Implémentez cette interface chaque fois que vous souhaitez étendre le comportement d’un nœud existant dans **Explorateur de serveurs**, tel que l’ajout d’un nouveau nœud enfant à un nœud.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>Pour ajouter le nœud Galerie de composants WebPart à Explorateur de serveurs

1. Collez le code suivant dans le fichier de code **SiteNodeExtension** pour le projet **WebPartNodeExtension** .

    > [!NOTE]
    > Après avoir ajouté ce code, le projet comportera des erreurs de compilation. Ces erreurs disparaissent lorsque vous ajoutez du code dans les étapes ultérieures.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb" id="Snippet1":::

## <a name="define-a-node-type-that-represents-a-web-part"></a>Définir un type de nœud qui représente un composant WebPart
 Créez une classe qui définit un nouveau type de nœud qui représente un composant WebPart. Visual Studio utilise ce nouveau type de nœud pour afficher les nœuds enfants sous le nœud **Galerie de composants WebPart** . Chacun de ces nœuds enfants représente un composant WebPart unique sur le site SharePoint.

 Pour définir le nouveau type de nœud, la classe implémente l' <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interface. Implémentez cette interface chaque fois que vous souhaitez définir un nouveau type de nœud dans **Explorateur de serveurs**.

#### <a name="to-define-the-web-part-node-type"></a>Pour définir le type de nœud WebPart

1. Collez le code suivant dans le fichier de code **WebPartNodeTypeProvider** pour le projet **WebPartNodeExtension** .

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb" id="Snippet2":::

## <a name="checkpoint"></a>Point de contrôle
 À ce stade de la procédure pas à pas, tout le code du nœud de la **Galerie de composants WebPart** se trouve maintenant dans le projet. Générez le projet **WebPartNodeExtension** pour vous assurer qu’il se compile sans erreur.

#### <a name="to-build-the-project"></a>Pour générer le projet

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **WebPartNodeExtension** , puis choisissez **générer**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Créer un package VSIX pour déployer l’extension
 Pour déployer l’extension, utilisez le projet VSIX dans votre solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source. extension. vsixmanifest qui est inclus dans le projet. Créez ensuite le package VSIX en générant la solution.

#### <a name="to-configure-the-vsix-package"></a>Pour configurer le package VSIX

1. Dans **Explorateur de solutions**, dans le projet **WebPartNode** , ouvrez le fichier **source. extension. vsixmanifest** dans l’éditeur de manifeste.

     Le fichier source. extension. vsixmanifest est la base du fichier extension. vsixmanifest requis par tous les packages VSIX. Pour plus d’informations sur ce fichier, consultez [Référence du schéma d’extension VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Dans la zone **nom du produit** , entrez **nœud de la Galerie de composants webpart pour Explorateur de serveurs**.

3. Dans la zone **auteur** , entrez **contoso**.

4. Dans la zone **Description** , entrez **ajoute un nœud de Galerie de composants WebPart personnalisé au nœud connexions SharePoint dans Explorateur de serveurs**.

5. Sous l’onglet **ressources** de l’éditeur, choisissez le bouton **nouveau** .

6. Dans la boîte de dialogue **Ajouter un nouvel élément** multimédia, dans la liste **type** , choisissez **Microsoft. VisualStudio. MEFComponent**.

    > [!NOTE]
    > Cette valeur correspond à l' `MefComponent` élément dans le fichier extension. vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MefComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

8. Dans la liste **projet** , choisissez **WebPartNodeExtension**, puis choisissez le bouton **OK** .

9. Dans la barre de menus, choisissez **générer**  >  **générer la solution**, puis assurez-vous que la solution est compilée sans erreur.

10. Assurez-vous que le dossier de sortie de la génération pour le projet WebPartNode contient maintenant le fichier WebPartNode. vsix.

     Par défaut, le dossier de sortie de la génération est le.. dossier \bin\Debug sous le dossier qui contient votre fichier projet.

## <a name="test-the-extension"></a>Tester l’extension
 Vous êtes maintenant prêt à tester le nouveau nœud de la **Galerie de composants WebPart** dans **Explorateur de serveurs**. Tout d’abord, commencez par déboguer le projet d’extension dans une instance expérimentale de Visual Studio. Utilisez ensuite le nouveau nœud **WebParts** dans l’instance expérimentale de Visual Studio.

#### <a name="to-start-debugging-the-extension"></a>Pour démarrer le débogage de l’extension

1. Redémarrez Visual Studio avec les informations d’identification d’administration, puis ouvrez la solution **WebPartNode** .

2. Dans le projet WebPartNodeExtension, ouvrez le fichier de code **SiteNodeExtension** , puis ajoutez un point d’arrêt aux premières lignes de code dans `NodeChildrenRequested` les `CreateWebPartNodes` méthodes et.

3. Appuyez sur la touche **F5** pour démarrer le débogage.

     Visual Studio installe l’extension de l’extension de nœud de la Galerie de composants%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web pour le serveur Explorer\1.0 et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.

#### <a name="to-test-the-extension"></a>Pour tester l’extension

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **Afficher**  >  **Explorateur de serveurs**.

2. Vérifiez que le site SharePoint que vous souhaitez utiliser pour le test s’affiche sous le nœud **Connexions SharePoint** dans **Explorateur de serveurs**. Si elle ne figure pas dans la liste, procédez comme suit :

    1. Ouvrez le menu contextuel des **Connexions SharePoint**, puis choisissez **Ajouter une connexion**.

    2. Dans la boîte de dialogue **Ajouter une connexion SharePoint** , entrez l’URL du site SharePoint auquel vous souhaitez vous connecter, puis choisissez le bouton **OK** .

         Pour spécifier le site SharePoint sur votre ordinateur de développement, tapez **http://localhost** .

3. Développez le nœud connexion au site (qui affiche l’URL de votre site), puis développez un nœud de site enfant (par exemple, **site d’équipe**).

4. Vérifiez que le code de l’autre instance de Visual Studio s’arrête sur le point d’arrêt que vous avez défini précédemment dans la méthode, puis appuyez sur `NodeChildrenRequested` la touche **F5** pour continuer à déboguer le projet.

5. Dans l’instance expérimentale de Visual Studio, développez le nœud **Galerie de composants WebPart** , qui apparaît sous le nœud de site de niveau supérieur.

6. Vérifiez que le code de l’autre instance de Visual Studio s’arrête sur le point d’arrêt que vous avez défini précédemment dans la méthode, puis appuyez sur `CreateWebPartNodes` la touche **F5** pour continuer à déboguer le projet.

7. Dans l’instance expérimentale de Visual Studio, vérifiez que tous les WebParts sur le site connecté s’affichent sous le nœud **Galerie de composants WebPart** dans **Explorateur de serveurs**.

8. Ouvrez le menu contextuel d’un composant WebPart, puis choisissez **Propriétés**.

9. Dans la fenêtre **Propriétés** , vérifiez que les détails sur le composant WebPart s’affichent.

10. Dans **Explorateur de serveurs**, ouvrez le menu contextuel du même composant WebPart, puis choisissez **afficher le message**.

     Dans la boîte de message qui s’affiche, choisissez le bouton **OK** .

## <a name="uninstall-the-extension-from-visual-studio"></a>Désinstaller l’extension de Visual Studio
 Une fois que vous avez fini de tester l’extension, désinstallez-la à partir de Visual Studio.

#### <a name="to-uninstall-the-extension"></a>Pour désinstaller l'extension

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **Outils**  >  **extensions et mises à jour**.

     La boîte de dialogue **Extensions et mises à jour** s’ouvre.

2. Dans la liste des extensions, choisissez le **nœud Galerie de composants WebPart pour Explorateur de serveurs**, puis choisissez le bouton **désinstaller** .

3. Dans la boîte de dialogue qui s’affiche, choisissez le bouton **Oui** .

4. Choisissez le bouton **redémarrer maintenant** pour terminer la désinstallation.

     L’élément de projet est également désinstallé.

5. Fermez les deux instances de Visual Studio (l’instance expérimentale et l’instance de Visual Studio dans laquelle la solution WebPartNode est ouverte).

## <a name="see-also"></a>Voir aussi
- [Appeler les modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Procédure pas à pas : étendre Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Éditeur d’images pour les icônes](/cpp/windows/image-editor-for-icons)
- [Création d’une icône ou d’une autre image &#40;éditeur d’images pour les icônes&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)