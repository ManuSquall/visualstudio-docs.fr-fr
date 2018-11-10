---
title: Déploiement d’Extensions pour les outils SharePoint dans Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3bf20f945c40dd963820b1bf3f4032a2dd517ca
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295967"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Déployer des extensions pour les outils SharePoint dans Visual Studio

Pour déployer une extension des outils SharePoint, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) qui contient l’assembly d’extension et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Un package VSIX est un fichier compressé qui respecte la norme Open Packaging Conventions (OPC). Les packages VSIX ont le *.vsix* extension.

Après avoir créé un package VSIX, les autres utilisateurs peuvent exécuter le fichier .vsix pour installer votre extension. Lorsqu’un utilisateur installe votre extension, tous les fichiers sont installés dans le dossier %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions. Pour déployer l’extension, vous pouvez télécharger le package VSIX pour le [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) site Web, ou vous distribuer le package à vos clients par d’autres moyens, tels que le package sur un partage réseau ou un autre site Web d’hébergement.

Pour plus d’informations sur la création de packages VSIX et de les déployer à le [galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847), consultez [de livraison des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Vous pouvez créer un package VSIX à l’aide de la **projet VSIX** modèle dans Visual Studio, ou vous pouvez créer un package VSIX manuellement.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Utiliser des projets VSIX pour créer des packages VSIX

Vous pouvez utiliser la **projet VSIX** modèle fourni par le SDK de Visual Studio pour créer des packages VSIX pour les extensions d’outils SharePoint. À l’aide d’un projet VSIX offre plusieurs avantages sur la création manuelle d’un package VSIX :

-   Visual Studio génère automatiquement le package VSIX lorsque vous générez le projet. Tâches telles que l’ajout des fichiers de déploiement pour le package et en créant le fichier [Content_Types] .xml pour le package sont effectuées automatiquement.

-   Vous pouvez configurer le projet VSIX pour inclure la sortie de génération de votre projet d’extension et d’autres fichiers, tels que les modèles de projet et modèles d’élément, dans le package VSIX.

Pour plus d’informations sur l’utilisation d’un projet VSIX, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Organiser vos projets

Par défaut, les projets VSIX génèrent uniquement des packages VSIX, pas d’assemblys. Par conséquent, vous en général, n’implémentez pas une extension des outils SharePoint dans un projet VSIX. En règle générale, vous travaillez avec au moins deux projets :

-   Un projet VSIX.

-   Un projet de bibliothèque de classes qui implémente votre extension.

Vous pouvez également travailler avec des projets supplémentaires pour certains types d’extensions :

-   Un projet de bibliothèque de classes qui implémente des commandes SharePoint qui sont utilisés par votre extension. Pour une procédure pas à pas qui illustre ce scénario, consultez [procédure pas à pas : étendre des Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

-   Un projet de modèle d’élément ou un modèle de projet qui crée un modèle d’élément ou d’un modèle de projet, si votre extension définit un nouveau type d’élément de projet SharePoint. Pour une procédure pas à pas qui illustre ce scénario, consultez [procédure pas à pas : créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

-   Un projet de bibliothèque de classes qui implémente un Assistant personnalisé pour un modèle d’élément ou d’un modèle de projet, si votre extension inclut un modèle. Pour une procédure pas à pas qui illustre ce scénario, consultez [procédure pas à pas : créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Si vous incluez tous les projets dans la même solution Visual Studio, vous pouvez modifier le fichier source.extension.vsixmanifest dans le projet VSIX pour inclure la sortie de génération de projets de bibliothèque de classes.

### <a name="edit-the-vsix-manifest"></a>Modifier le manifeste VSIX

Vous devez modifier le fichier source.extension.vsixmanifest dans le projet VSIX pour inclure des entrées pour tous les éléments que vous souhaitez inclure dans votre extension. Lorsque vous ouvrez le fichier source.extension.vsixmanifest dans son menu contextuel, le fichier apparaît dans un concepteur qui fournit une interface utilisateur pour modifier le XML dans le fichier. Pour plus d’informations, consultez [Concepteur de manifeste VSIX](../extensibility/vsix-manifest-designer.md).

Vous devez ajouter des entrées dans le fichier source.extension.vsixmanifest pour les éléments suivants :

-   L’assembly d’extension.

-   L’assembly qui implémente des commandes SharePoint qui sont utilisés par votre extension.

-   Modèles de projet ni les modèles d’élément qui sont associés à votre extension.

-   Un Assistant personnalisé pour un modèle qui est associé à votre extension.

Les procédures suivantes décrivent comment ajouter des entrées dans le fichier .vsixmanifest pour chacun de ces éléments.

#### <a name="to-include-the-extension-assembly"></a>Pour inclure l’assembly d’extension

1.  Dans le projet VSIX, ouvrez le menu contextuel pour le fichier source.extension.vsixmanifest, puis choisissez **ouvrir**.

     Le fichier s’ouvre dans le Concepteur

2.  Sur le **actifs** onglet de l’éditeur, choisissez le **New** bouton.

     Le **ajouter un nouveau composant** boîte de dialogue s’ouvre.

3.  Dans le **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.

4.  Dans le **Source** liste, effectuez l’une des étapes suivantes :

    -   Si l’assembly d’extension est créée à partir d’un projet qui se trouve dans la même solution que le projet VSIX, choisissez **un projet dans la solution actuelle**. Dans le **projet** , sélectionnez le nom du projet.

    -   Si l’assembly d’extension est inclus en tant que fichier dans votre projet, choisissez **fichier sur le système de fichiers**. Dans le **chemin d’accès** liste, entrez le chemin d’accès complet au fichier d’assembly extension ou utilisez le **Parcourir** bouton pour rechercher et choisir le fichier d’assembly.

5.  Sélectionnez le bouton **OK** .

#### <a name="to-include-a-sharepoint-command-assembly"></a>Pour inclure un assembly de commande SharePoint

1.  Dans le projet VSIX, ouvrez le menu contextuel pour le fichier source.extension.vsixmanifest, puis choisissez le **ouvrir** bouton.

     Le fichier s’ouvre dans le concepteur.

2.  Dans le **actifs** section de l’éditeur, choisissez le **New** bouton.

     Le **ajouter un nouveau composant** boîte de dialogue s’ouvre.

3.  Dans le **Type** , entrez **SharePoint.Commands.v4**.

4.  Dans le **Source** liste, effectuez l’une des étapes suivantes :

    -   Si l’assembly de commande est créée à partir d’un projet qui se trouve dans la même solution que le projet VSIX, choisissez **un projet dans la solution actuelle**. Dans le **projet** , sélectionnez le nom du projet.

    -   Si l’assembly de commande est inclus en tant que fichier dans votre projet, choisissez **fichier sur le système de fichiers**. Dans le **chemin d’accès** liste, entrez le chemin d’accès complet au fichier d’assembly extension ou utilisez le **Parcourir** bouton pour rechercher et choisir le fichier d’assembly.

5.  Sélectionnez le bouton **OK** .

#### <a name="to-include-a-template-that-you-create"></a>Pour inclure un modèle que vous créez

1.  Dans le projet VSIX, ouvrez le menu contextuel pour le fichier source.extension.vsixmanifest, puis choisissez le **ouvrir** bouton.

     Le fichier s’ouvre dans le concepteur.

2.  Dans le **actifs** section de l’éditeur, choisissez le **New** bouton.

     Le **ajouter un nouveau composant** boîte de dialogue s’ouvre.

3.  Dans le **Type** , choisissez **Microsoft.VisualStudio.ProjectTemplate** ou **Microsoft.VisualStudio.ItemTemplate**.

4.  Dans le **Source** , choisissez **un projet dans la solution actuelle**.

5.  Dans le **projet** liste, choisissez le nom du projet, puis le **OK** bouton.

6.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour votre projet de modèle de projet ou modèle d’élément, puis choisissez **décharger le projet**.

7.  Rouvrez le menu contextuel du nœud de projet, puis choisissez **modifier**_VotreNomProjetModèle_**.csproj** ou **modifier**  _VotreNomProjetModèle_**.vbproj**.

8.  Recherchez les éléments suivants `VSTemplate` élément dans le fichier projet.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Remplacez cet élément par le code XML suivant.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     Le `OutputSubPath` élément spécifie des dossiers supplémentaires dans le chemin d’accès sous lequel le modèle de projet est créé lorsque vous générez le projet. Les dossiers spécifiés ici garantissent que le modèle d’élément sera disponible uniquement lorsque les clients Ouvrir le **ajouter un nouveau projet** boîte de dialogue, développez le **SharePoint** nœud, puis choisissez le **2010**  nœud.

10. Enregistrez et fermez le fichier.

11. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le projet de modèle de projet ou modèle d’élément, puis choisissez **recharger le projet**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Pour inclure un modèle que vous créez manuellement

1.  Dans le projet VSIX, ajoutez un nouveau dossier au projet pour contenir le modèle.

2.  Sous ce nouveau dossier, créez les sous-dossiers suivants, puis ajoutez le fichier modèle (.zip) à la *ID de paramètres régionaux* dossier.

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *ID de paramètres régionaux*

     *YourTemplateName*.zip

     Par exemple, si vous avez un modèle d’élément nommé ContosoCustomAction.zip qui prend en charge les paramètres régionaux anglais (États-Unis), le chemin d’accès complet peut être *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3.  Dans **l’Explorateur de solutions**, choisissez le fichier de modèle (*YourTemplateName*.zip).

4.  Dans le **propriétés** fenêtre, définissez la **Action de génération** propriété **contenu**.

5.  Ouvrez le menu contextuel pour le fichier source.extension.vsixmanifest, puis choisissez **Open**.

     Le fichier s’ouvre dans le concepteur.

6.  Dans le **actifs** section de l’éditeur, choisissez le **New** bouton.

     Le **ajouter un nouveau composant** boîte de dialogue s’ouvre.

7.  Dans le **Type** , choisissez **Microsoft.VisualStudio.ItemTemplate** ou **Microsoft.VisualStudio.ProjectTemplate**.

8.  Dans le **Source** , choisissez **fichier sur le système de fichiers**.

9. Dans le **chemin d’accès** , entrez le chemin d’accès complet à l’assembly (par exemple, *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*, ou utiliser le **Parcourir**bouton pour rechercher et sélectionner l’assembly, puis choisissez le **OK** bouton.

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Pour inclure un Assistant pour un modèle de projet ou un modèle d’élément

1.  Dans le projet VSIX, ouvrez le menu contextuel pour le fichier source.extension.vsixmanifest, puis choisissez **ouvrir**.

     Le fichier s’ouvre dans le concepteur.

2.  Dans le **actifs** section de l’éditeur, choisissez le **New** bouton.

     Le **ajouter un nouveau composant** boîte de dialogue s’ouvre.

3.  Dans le **Type** , choisissez **Microsoft.VisualStudio.Assembly**.

4.  Dans le **Source** liste, effectuez l’une des étapes suivantes :

    -   Si l’assembly de l’Assistant est créée à partir d’un projet qui se trouve dans la même solution que le projet VSIX, choisissez **un projet dans la solution actuelle**. Dans le **projet** , sélectionnez le nom du projet.

    -   Si l’assembly de l’Assistant est inclus en tant que fichier dans votre projet, choisissez **fichier sur le système de fichiers**. Dans le **chemin d’accès** champ, entrez le chemin d’accès complet au fichier d’assembly ou utilisez le **Parcourir** bouton pour rechercher et sélectionner l’assembly.

5.  Sélectionnez le bouton **OK** .

### <a name="related-walkthroughs"></a>Procédures pas à pas connexes

Le tableau suivant répertorie les procédures pas à pas qui montrent comment utiliser un projet VSIX pour déployer différents types d’extensions d’outils SharePoint.

|Type d’extension|Procédures pas à pas connexes|
|--------------------|--------------------------|
|Une extension qui inclut uniquement l’assembly d’extension|[Procédure pas à pas : Étendre un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Procédure pas à pas : Créer une extension de projet SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Procédure pas à pas : Appel dans le modèle d’objet client SharePoint dans une extension de l’Explorateur de serveurs](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Une extension qui inclut des commandes SharePoint|[Procédure pas à pas : Créer une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Procédure pas à pas : Étendre l’Explorateur de serveurs pour afficher des WebParts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Une extension qui inclut un modèle Visual Studio|[Procédure pas à pas : Créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Procédure pas à pas : Créer un élément de projet de colonne de Site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Une extension qui inclut un Assistant de modèle|[Procédure pas à pas : Créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Procédure pas à pas : Créer un élément de projet de colonne de Site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Créer manuellement des packages VSIX

Si vous souhaitez créer manuellement le package VSIX pour votre extension d’outils SharePoint, procédez comme suit :

1.  Créer le fichier extension.vsixmanifest et le fichier [Content_Types] .xml dans un nouveau dossier. Pour plus d’informations, consultez [Anatomie d’un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2.  Dans l’Explorateur Windows, cliquez sur le dossier qui contient les deux fichiers XML, cliquez sur Envoyer vers, puis cliquez sur dossier compressé (zippé). Renommez le fichier .zip à Filename.vsix, où nom_fichier représente le nom du fichier redistribuable qui installe votre package.

3.  Ajoutez votre assembly d’extension au package VSIX. Si votre extension inclut une commande SharePoint, également ajouter l’assembly qui implémente la commande SharePoint pour le package VSIX.

4.  Modifiez le fichier extension.vsixmanifest :

    -   Ajouter un `Microsoft.VisualStudio.MefComponent` élément sous le `Assets` élément et définissez la valeur du nouvel élément pour le chemin d’accès relatif de l’assembly qui implémente votre extension dans le package VSIX. Pour plus d’informations, consultez [MEFComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    -   Si votre extension inclut une commande SharePoint qui appelle le modèle d’objet serveur pour SharePoint, ajoutez un `Microsoft.VisualStudio.Assembly` élément sous le `Assets` élément. Définissez la valeur du nouvel élément sur le chemin d’accès relatif de l’assembly qui implémente la commande SharePoint dans le package VSIX. Pour plus d’informations, consultez [Asset, élément (schéma VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

    -   Si votre extension inclut un modèle de projet ou un modèle d’élément, ajoutez un `ProjectTemplate` ou `ItemTemplate` élément sous le `Assets` élément. Définissez la valeur du nouvel élément sur le chemin d’accès relatif du dossier qui contient le modèle dans le package VSIX. Pour plus d’informations, consultez [ProjectTemplate, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) et [ItemTemplate, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    -   Si votre extension inclut un Assistant personnalisé pour un modèle de projet ou un modèle d’élément, ajoutez un `Assembly` élément sous le `Assets` élément. Définissez la valeur du nouvel élément sur le chemin d’accès relatif de l’assembly dans le package VSIX et définissez le `AssemblyName` attribut nom d’assembly complet (y compris la version, culture et jeton de clé publique). Pour plus d’informations, consultez [dépendance, élément (schéma VSX)](https://msdn.microsoft.com/1f63f60a-98ad-48ec-8e44-4eba383d3e37).

### <a name="example"></a>Exemple

L’exemple suivant montre le contenu d’un fichier extension.vsixmanifest d’une extension des outils SharePoint. L’extension est implémentée dans un assembly nommé Contoso.ProjectExtension.dll. L’extension inclut un assembly de commande SharePoint nommé Contoso.ExtensionCommands.dll et un modèle d’élément dans un dossier nommé **ItemTemplates** dans le package VSIX. Cet exemple suppose que les deux assemblys sont dans le même dossier que le fichier extension.vsixmanifest dans le package VSIX.

```xml
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <Identity Id="CustomActionProjectItem.Microsoft.b99efe4d-cef3-4afd-b9af-034ca0c52743" Version="1.0" Language="en-US" Publisher="Microsoft" />
    <DisplayName>CustomActionProjectItem</DisplayName>
    <Description>Empty VSIX Project.</Description>
  </Metadata>
  <Installation>
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="11.0" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" Version="4.5" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.ItemTemplate" Path="ItemTemplates" />
    <Asset Type="Microsoft.VisualStudio.MefComponent" Path="ProjectItemDefinition.dll" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Voir aussi

- [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Étendre le nœud Connexions SharePoint dans l’Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Déboguer des extensions pour les outils SharePoint dans Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
