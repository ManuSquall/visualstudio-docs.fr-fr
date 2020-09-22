---
title: Déploiement d’extensions pour les outils SharePoint dans Visual Studio | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0e7bcb4c03a274c958b097ab7869cb58120b0ee7
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740142"
---
# <a name="deploy-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Déployer des extensions pour les outils SharePoint dans Visual Studio

Pour déployer une extension d’outils SharePoint, créez un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) qui contient l’assembly d’extension et tous les autres fichiers que vous souhaitez distribuer avec l’extension. Un package VSIX est un fichier compressé qui suit la norme OPC (Open Packaging Conventions). Les packages VSIX ont l’extension *. vsix* .

Une fois que vous avez créé un package VSIX, d’autres utilisateurs peuvent exécuter le fichier. VSIX pour installer votre extension. Lorsqu’un utilisateur installe votre extension, tous les fichiers sont installés dans le dossier%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions Pour déployer l’extension, vous pouvez télécharger le package VSIX sur le site Web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , ou vous pouvez distribuer le package à vos clients par d’autres moyens, tels que l’hébergement du package sur un partage réseau ou un autre site Web.

Pour plus d’informations sur la création de packages VSIX et leur déploiement dans le [Visual Studio Marketplace](https://marketplace.visualstudio.com/), consultez la page [expédition d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Vous pouvez créer un package VSIX à l’aide du modèle de **projet VSIX** dans Visual Studio, ou vous pouvez créer un package VSIX manuellement.

## <a name="use-vsix-projects-to-create-vsix-packages"></a>Utiliser des projets VSIX pour créer des packages VSIX

Vous pouvez utiliser le modèle de **projet VSIX** fourni par le kit de développement logiciel (SDK) Visual Studio pour créer des packages VSIX pour les extensions d’outils SharePoint. L’utilisation d’un projet VSIX offre plusieurs avantages par rapport à la création manuelle d’un package VSIX :

- Visual Studio génère automatiquement le package VSIX lorsque vous générez le projet. Des tâches telles que l’ajout de fichiers de déploiement au package et la création du fichier [Content_Types]. xml pour le package sont effectuées pour vous.

- Vous pouvez configurer le projet VSIX pour inclure la sortie de génération de votre projet d’extension et d’autres fichiers, tels que les modèles de projet et les modèles d’élément, dans le package VSIX.

Pour plus d’informations sur l’utilisation d’un projet VSIX, consultez [modèle de projet VSIX](../extensibility/vsix-project-template.md).

### <a name="organize-your-projects"></a>Organiser vos projets

Par défaut, les projets VSIX génèrent uniquement des packages VSIX, et non des assemblys. Par conséquent, vous n’implémentez généralement pas d’extension d’outils SharePoint dans un projet VSIX. Vous travaillez généralement avec au moins deux projets :

- Projet VSIX.

- Un projet de bibliothèque de classes qui implémente votre extension.

Vous pouvez également utiliser des projets supplémentaires pour certains types d’extensions :

- Projet de bibliothèque de classes qui implémente toutes les commandes SharePoint utilisées par votre extension. Pour obtenir une procédure pas à pas qui illustre ce scénario, consultez [procédure pas à pas : étendre Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Un modèle d’élément ou un projet de modèle de projet qui crée un modèle d’élément ou un modèle de projet, si votre extension définit un nouveau type d’élément de projet SharePoint. Pour obtenir une procédure pas à pas qui illustre ce scénario, consultez [procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

- Projet de bibliothèque de classes qui implémente un Assistant personnalisé pour un modèle d’élément ou un modèle de projet, si votre extension comprend un modèle. Pour obtenir une procédure pas à pas qui illustre ce scénario, consultez [procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

Si vous incluez tous les projets dans la même solution Visual Studio, vous pouvez modifier le fichier source. extension. vsixmanifest dans le projet VSIX pour inclure la sortie de génération des projets de bibliothèque de classes.

### <a name="edit-the-vsix-manifest"></a>Modifier le manifeste VSIX

Vous devez modifier le fichier source. extension. vsixmanifest dans le projet VSIX pour inclure les entrées de tous les éléments que vous souhaitez inclure dans votre extension. Quand vous ouvrez le fichier source. extension. vsixmanifest à partir de son menu contextuel, le fichier s’affiche dans un concepteur qui fournit une interface utilisateur pour modifier le code XML dans le fichier. Pour plus d’informations, consultez [Concepteur de manifeste VSIX](../extensibility/vsix-manifest-designer.md).

Vous devez ajouter des entrées au fichier source. extension. vsixmanifest pour les éléments suivants :

- Assembly d’extension.

- Assembly qui implémente toutes les commandes SharePoint utilisées par votre extension.

- Tous les modèles de projet ou les modèles d’élément associés à votre extension.

- Assistant personnalisé pour un modèle associé à votre extension.

Les procédures suivantes décrivent comment ajouter des entrées au fichier. vsixmanifest pour chacun de ces éléments.

#### <a name="to-include-the-extension-assembly"></a>Pour inclure l’assembly d’extension

1. Dans le projet VSIX, ouvrez le menu contextuel du fichier source. extension. vsixmanifest, puis choisissez **ouvrir**.

     Le fichier s’ouvre dans le concepteur.

2. Sous l’onglet **ressources** de l’éditeur, choisissez le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’ouvre.

3. Dans la liste **type** , choisissez **Microsoft. VisualStudio. MEFComponent**.

4. Dans la liste **source** , effectuez l’une des opérations suivantes :

    - Si l’assembly d’extension est construit à partir d’un projet qui se trouve dans la même solution que le projet VSIX, choisissez **un projet dans la solution actuelle**. Dans la liste **projet** , choisissez le nom du projet.

    - Si l’assembly d’extension est inclus dans un fichier de votre projet, choisissez **fichier sur le système de fichiers**. Dans la liste **chemin d’accès** , entrez le chemin d’accès complet au fichier d’assembly d’extension, ou utilisez le bouton **Parcourir** pour rechercher et sélectionner le fichier d’assembly.

5. Choisissez le bouton **OK**.

#### <a name="to-include-a-sharepoint-command-assembly"></a>Pour inclure un assembly de commande SharePoint

1. Dans le projet VSIX, ouvrez le menu contextuel du fichier source. extension. vsixmanifest, puis choisissez le bouton **ouvrir** .

     Le fichier s’ouvre dans le concepteur.

2. Dans la section **ressources** de l’éditeur, choisissez le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’ouvre.

3. Dans la zone **type** , entrez **SharePoint. Commands. v4**.

4. Dans la liste **source** , effectuez l’une des opérations suivantes :

    - Si l’assembly de commande est généré à partir d’un projet qui se trouve dans la même solution que le projet VSIX, choisissez **un projet dans la solution actuelle**. Dans la liste **projet** , choisissez le nom du projet.

    - Si l’assembly de commande est inclus dans un fichier de votre projet, choisissez **fichier sur le système de fichiers**. Dans la liste **chemin d’accès** , entrez le chemin d’accès complet au fichier d’assembly d’extension, ou utilisez le bouton **Parcourir** pour rechercher et sélectionner le fichier d’assembly.

5. Choisissez le bouton **OK**.

#### <a name="to-include-a-template-that-you-create"></a>Pour inclure un modèle que vous créez

1. Dans le projet VSIX, ouvrez le menu contextuel du fichier source. extension. vsixmanifest, puis choisissez le bouton **ouvrir** .

     Le fichier s’ouvre dans le concepteur.

2. Dans la section **ressources** de l’éditeur, choisissez le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’ouvre.

3. Dans la liste **type** , choisissez **Microsoft. VisualStudio. ProjectTemplate** ou **Microsoft. VisualStudio. ItemTemplate**.

4. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

5. Dans la liste **projet** , choisissez le nom du projet, puis choisissez le bouton **OK** .

6. Dans **Explorateur de solutions**, ouvrez le menu contextuel de votre projet de modèle de projet ou d’élément, puis choisissez **décharger le projet**.

7. Ouvrez à nouveau le menu contextuel du nœud du projet, puis choisissez **modifier**_YourTemplateProjectName_**. csproj** ou **modifier**_YourTemplateProjectName_**. vbproj**.

8. Localisez l' `VSTemplate` élément suivant dans le fichier projet.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
    ```

9. Remplacez cet élément par le code XML suivant.

    ```xml
    <VSTemplate Include="YourTemplateName.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     L' `OutputSubPath` élément spécifie des dossiers supplémentaires dans le chemin d’accès sous lequel le modèle de projet est créé lorsque vous générez le projet. Les dossiers spécifiés ici garantissent que le modèle d’élément sera disponible uniquement lorsque les clients ouvriront la boîte de dialogue **Ajouter un nouveau projet** , développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

10. Enregistrez et fermez le fichier.

11. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet de modèle de projet ou d’élément, puis choisissez **recharger le projet**.

#### <a name="to-include-a-template-that-you-create-manually"></a>Pour inclure un modèle que vous créez manuellement

1. Dans le projet VSIX, ajoutez un nouveau dossier au projet pour contenir le modèle.

2. Sous ce nouveau dossier, créez les sous-dossiers suivants, puis ajoutez le fichier de modèle (. zip) au dossier des *ID de paramètres régionaux* .

     *YourTemplateFolder*

     **SharePoint**

     **SharePoint14**

     *ID des paramètres régionaux*

     *YourTemplateName*. zip

     Par exemple, si vous avez un modèle d’élément nommé ContosoCustomAction.zip qui prend en charge les paramètres régionaux anglais (États-Unis), le chemin d’accès complet peut être *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*.

3. Dans **Explorateur de solutions**, choisissez le fichier de modèle (*YourTemplateName*. zip).

4. Dans la fenêtre **Propriétés** , affectez à la propriété **action de génération** la valeur **contenu**.

5. Ouvrez le menu contextuel du fichier source. extension. vsixmanifest, puis choisissez **ouvrir**.

     Le fichier s’ouvre dans le concepteur.

6. Dans la section **ressources** de l’éditeur, choisissez le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’ouvre.

7. Dans la liste **type** , choisissez **Microsoft. VisualStudio. ItemTemplate** ou **Microsoft. VisualStudio. ProjectTemplate**.

8. Dans la liste **source** , choisissez **fichier sur FileSystem**.

9. Dans le champ **chemin d’accès** , entrez le chemin d’accès complet de l’assembly (par exemple, *ItemTemplates\SharePoint\SharePoint14\1033\ContosoCustomAction.zip*ou utilisez le bouton **Parcourir** pour rechercher et sélectionner l’assembly, puis choisissez le bouton **OK** .

#### <a name="to-include-a-wizard-for-a-project-template-or-item-template"></a>Pour inclure un Assistant pour un modèle de projet ou un modèle d’élément

1. Dans le projet VSIX, ouvrez le menu contextuel du fichier source. extension. vsixmanifest, puis choisissez **ouvrir**.

     Le fichier s’ouvre dans le concepteur.

2. Dans la section **ressources** de l’éditeur, choisissez le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’ouvre.

3. Dans la liste **type** , choisissez **Microsoft. VisualStudio. assembly**.

4. Dans la liste **source** , effectuez l’une des opérations suivantes :

    - Si l’assembly de l’Assistant est généré à partir d’un projet qui se trouve dans la même solution que le projet VSIX, choisissez **un projet dans la solution actuelle**. Dans la liste **projet** , choisissez le nom du projet.

    - Si l’assembly de l’Assistant est inclus dans un fichier de votre projet, choisissez **fichier sur le système de fichiers**. Dans le champ **chemin d’accès** , entrez le chemin d’accès complet au fichier d’assembly ou utilisez le bouton **Parcourir** pour rechercher et sélectionner l’assembly.

5. Choisissez le bouton **OK**.

### <a name="related-walkthroughs"></a>Procédures pas à pas connexes

Le tableau suivant répertorie les procédures pas à pas qui montrent comment utiliser un projet VSIX pour déployer différents types d’extensions d’outils SharePoint.

|Type d’extension|Procédures pas à pas connexes|
|--------------------|--------------------------|
|Extension qui comprend uniquement l’assembly d’extension|[Procédure pas à pas : étendre un type d’élément de projet SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Procédure pas à pas : créer une extension de projet SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Procédure pas à pas : appel du modèle d’objet client SharePoint dans une extension de Explorateur de serveurs](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|
|Une extension qui comprend des commandes SharePoint|[Procédure pas à pas : création d’une étape de déploiement personnalisée pour les projets SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Procédure pas à pas : étendre Explorateur de serveurs pour afficher des composants WebPart](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|
|Extension qui comprend un modèle Visual Studio|[Procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|
|Extension qui comprend un Assistant modèle|[Procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|

## <a name="create-vsix-packages-manually"></a>Créer des packages VSIX manuellement

Si vous souhaitez créer manuellement le package VSIX pour votre extension d’outils SharePoint, procédez comme suit :

1. Créez le fichier extension. vsixmanifest et le fichier [Content_Types]. xml dans un nouveau dossier. Pour plus d’informations, consultez [anatomie d’un package VSIX](../extensibility/anatomy-of-a-vsix-package.md).

2. Dans l’Explorateur Windows, cliquez avec le bouton droit sur le dossier qui contient les deux fichiers XML, cliquez sur Envoyer vers, puis sur dossier compressé (zippé). Renommez le fichier .zip que vous venez de créer nom_fichier.vsix, où nom_fichier correspond au nom du fichier redistribuable qui installe votre package.

3. Ajoutez votre assembly d’extension au package VSIX. Si votre extension comprend une commande SharePoint, ajoutez également l’assembly qui implémente la commande SharePoint au package VSIX.

4. Modifiez le fichier extension. vsixmanifest :

    - Ajoutez un `Microsoft.VisualStudio.MefComponent` élément sous l' `Assets` élément, puis définissez la valeur du nouvel élément sur le chemin d’accès relatif de l’assembly qui implémente votre extension dans le package VSIX. Pour plus d’informations, consultez [MefComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

    - Si votre extension comprend une commande SharePoint qui appelle le modèle objet serveur pour SharePoint, ajoutez un `Microsoft.VisualStudio.Assembly` élément sous l' `Assets` élément. Définissez la valeur du nouvel élément sur le chemin d’accès relatif de l’assembly qui implémente la commande SharePoint dans le package VSIX. Pour plus d’informations, consultez [élément Asset (schéma VSX)](/previous-versions/dd393737(v=vs.110)).

    - Si votre extension comprend un modèle de projet ou un modèle d’élément, ajoutez un `ProjectTemplate` `ItemTemplate` élément ou sous l' `Assets` élément. Définissez la valeur du nouvel élément sur le chemin d’accès relatif du dossier qui contient le modèle dans le package VSIX. Pour plus d’informations, consultez l' [élément ProjectTemplate (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393735\(v\=vs.100\)) et l' [élément ITEMTEMPLATE (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

    - Si votre extension comprend un Assistant personnalisé pour un modèle de projet ou un modèle d’élément, ajoutez un `Assembly` élément sous l' `Assets` élément. Définissez la valeur du nouvel élément sur le chemin d’accès relatif de l’assembly dans le package VSIX, puis affectez `AssemblyName` à l’attribut le nom complet de l’assembly (y compris la version, la culture et le jeton de clé publique). Pour plus d’informations, consultez [dependency, élément (schéma VSX)](/previous-versions/dd393682(v=vs.110)).

### <a name="example"></a>Exemple

L’exemple suivant montre le contenu d’un fichier extension. vsixmanifest pour une extension d’outils SharePoint. L’extension est implémentée dans un assembly nommé Contoso.ProjectExtension.dll. L’extension comprend un assembly de commande SharePoint nommé Contoso.ExtensionCommands.dll et un modèle d’élément sous un dossier nommé **éléments personnalisés** dans le package VSIX. Cet exemple suppose que les deux assemblys se trouvent dans le même dossier que le fichier extension. vsixmanifest dans le package VSIX.

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
- [Étendre le nœud Connexions SharePoint dans Explorateur de serveurs](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Appeler les modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Extensions de débogage pour les outils SharePoint dans Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)