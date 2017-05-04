---
title: "Deploying Extensions for the SharePoint Tools in Visual Studio | Microsoft Docs"
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
  - "SharePoint development in Visual Studio, deploying extensions"
ms.assetid: 69927d95-acdf-4fd8-ac43-28e9a7fa8a38
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Deploying Extensions for the SharePoint Tools in Visual Studio
  Pour déployer une extension d'outils SharePoint, créez un package d'extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(VSIX\) qui contient l'assembly d'extension et tous les autres fichiers que vous voulez distribuer avec l'extension.  Un package VSIX est un fichier compressé conforme à la norme OPC \(Open Packaging Conventions\).  Les packages VSIX ont l'extension .vsix.  
  
 Une fois que vous avez créé un package VSIX, d'autres utilisateurs peuvent exécuter le fichier .vsix pour installer votre extension.  Lorsqu'un utilisateur installe votre extension, tous les fichiers sont placés dans le dossier %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions.  Pour déployer l'extension, vous pouvez télécharger le package VSIX sur le site Web de la [Galerie Visual Studio \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=123847) ou distribuer le package à vos clients par d'autres moyens, tels que l'hébergement du package sur un partage réseau ou un autre site Web.  
  
 Pour plus d'informations sur la création de packages VSIX et leur déploiement sur le site Web de la [Galerie Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847), consultez [Envoi des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Vous pouvez créer un package VSIX au moyen du modèle **Projet VSIX** dans Visual Studio ou bien manuellement.  
  
## Utilisation de projets VSIX pour la création de packages VSIX  
 Vous pouvez utiliser le modèle **projet VSIX** fourni par le kit de développement Visual Studio pour créer des packages VSIX pour les extensions d'outils SharePoint.  L'utilisation d'un projet VSIX offre plusieurs avantages par rapport à la création manuelle d'un package VSIX :  
  
-   Visual Studio génère automatiquement le package VSIX lors de la génération du projet.  Les tâches telles que l'ajout des fichiers de déploiement au package et la création du fichier \[Content\_Types\].xml pour le package sont effectuées automatiquement.  
  
-   Vous pouvez configurer le projet VSIX pour inclure la sortie de génération de votre projet d'extension et d'autres fichiers, tels que les modèles de projet et d'élément, dans le package VSIX.  
  
 Pour plus d'informations sur l'utilisation d'un projet VSIX, consultez [Modèle de projet VSIX](../extensibility/vsix-project-template.md).  
  
### Organisation de vos projets  
 Par défaut, les projets VSIX génèrent uniquement des packages VSIX, pas d'assemblys.  Par conséquent, en général vous n'implémentez pas d'extension d'outils SharePoint dans un projet VSIX.  Généralement, vous utilisez au moins deux projets :  
  
-   Un projet VSIX.  
  
-   Un projet de bibliothèque de classes qui implémente votre extension.  
  
 Vous pouvez également utiliser des projets supplémentaires pour certains types d'extensions :  
  
-   Un projet de bibliothèque de classes qui implémente des commandes SharePoint utilisées par votre extension.  Pour connaître la procédure pas à pas qui illustre ce scénario, consultez [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Un projet de modèle d'élément ou de projet qui crée un modèle d'élément ou un modèle de projet, si votre extension définit un nouveau type d'élément de projet SharePoint.  Pour connaître la procédure pas à pas qui illustre ce scénario, consultez [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
-   Un projet de bibliothèque de classes qui implémente un Assistant personnalisé d'un modèle d'élément ou d'un modèle de projet, si votre extension comprend un modèle.  Pour connaître la procédure pas à pas qui illustre ce scénario, consultez [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).  
  
 Si vous incluez tous les projets dans la même solution Visual Studio, vous pouvez modifier le fichier source.extension.vsixmanifest dans le projet VSIX pour inclure la sortie de génération des projets de bibliothèque de classes.  
  
### Modification du manifeste VSIX  
 Vous devez modifier le fichier source.extension.vsixmanifest dans le projet VSIX pour inclure des entrées pour tous les éléments à inclure dans votre extension.  Lorsque vous ouvrez le fichier source.extension.vsixmanifest dans le menu contextuel, le fichier apparaît dans un concepteur qui fournit une interface utilisateur pour modifier le code XML dans le fichier.  Pour plus d’informations, consultez [Concepteur de manifeste VSIX](../extensibility/media/vsix-manifest-designer.png).  
  
 Vous devez ajouter des entrées dans le fichier source.extension.vsixmanifest pour les éléments suivants :  
  
-   L'assembly d'extension.  
  
-   L'assembly qui implémente des commandes SharePoint utilisées par votre extension.  
  
-   Tous les modèles de projet ou d'élément associés à votre extension.  
  
-   Un Assistant personnalisé pour un modèle associé à votre extension.  
  
 Les procédures suivantes décrivent la procédure d'ajout des entrées dans le fichier .vsixmanifest pour chacun de ces éléments.  
  
##### Pour inclure l'assembly d'extension  
  
1.  Dans le projet VSIX, ouvrez le menu contextuel du fichier source.extension.vsixmanifest, puis choisissez **Ouvrir**.  
  
     Le fichier s'ouvre dans le concepteur  
  
2.  Sous l'onglet **Composants** de l'éditeur, choisissez le bouton **Nouveau** .  
  
     La boîte de dialogue **ajoutez le nouveau ressource** s'ouvre.  
  
3.  Dans la liste **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.  
  
4.  Dans la liste **Source** , effectuez l'une des étapes suivantes :  
  
    -   Si l'assembly d'extension est généré à partir d'un projet figurant dans la même solution que le projet VSIX, choisissez **un projet dans la solution actuelle**.  Dans la liste **Projet** , sélectionnez le nom du projet.  
  
    -   Si l'assembly d'extension est inclus en tant que fichier dans votre projet, choisissez **Tapez du système de fichiers**.  Dans la liste **Chemin d'accès** , entrez le chemin d'accès complet au fichier d'assembly d'extension, ou utilisez le bouton **Parcourir** pour rechercher et sélectionner le fichier d'assembly.  
  
5.  Cliquez sur le bouton **OK**.  
  
##### Pour inclure un assembly de commande SharePoint  
  
1.  Dans le projet VSIX, ouvrez le menu contextuel du fichier source.extension.vsixmanifest, puis choisissez le bouton **Ouvrir** .  
  
     Le fichier s'ouvre dans le concepteur.  
  
2.  Dans la section **Composants** de l'éditeur, choisissez le bouton **Nouveau** .  
  
     La boîte de dialogue **ajoutez le nouveau ressource** s'ouvre.  
  
3.  Dans la zone **Type** , entrez **SharePoint.Commands.v4**.  
  
4.  Dans la liste **Source** , effectuez l'une des étapes suivantes :  
  
    -   Si l'assembly de commande est généré à partir d'un projet figurant dans la même solution que le projet VSIX, choisissez **un projet dans la solution actuelle**.  Dans la liste **Projet** , sélectionnez le nom du projet.  
  
    -   Si l'assembly de commande est inclus en tant que fichier dans votre projet, choisissez **Tapez du système de fichiers**.  Dans la liste **Chemin d'accès** , entrez le chemin d'accès complet au fichier d'assembly d'extension, ou utilisez le bouton **Parcourir** pour rechercher et sélectionner le fichier d'assembly.  
  
5.  Cliquez sur le bouton **OK**.  
  
##### Pour inclure un modèle que vous créez  
  
1.  Dans le projet VSIX, ouvrez le menu contextuel du fichier source.extension.vsixmanifest, puis choisissez le bouton **Ouvrir** .  
  
     Le fichier s'ouvre dans le concepteur.  
  
2.  Dans la section **Composants** de l'éditeur, choisissez le bouton **Nouveau** .  
  
     La boîte de dialogue **ajoutez le nouveau ressource** s'ouvre.  
  
3.  Dans la liste **Type** , choisissez **Microsoft.VisualStudio.ProjectTemplate** ou **Microsoft.VisualStudio.ItemTemplate**.  
  
4.  Dans la liste **Source** , choisissez **un projet dans la solution actuelle**.  
  
5.  Dans la liste **Projet** , sélectionnez le nom du projet, puis choisissez le bouton **OK** .  
  
6.  Dans **Explorateur de solutions**, ouvrez le menu contextuel pour votre projet de modèle de projet ou d'élément, puis choisissez **Décharger le projet**.  
  
7.  Ouvrez le menu contextuel du nœud de projet une nouvelle fois, puis choisissez **Modifier***YourTemplateProjectName***.csproj** ou **Modifier***YourTemplateProjectName***.vbproj**.  
  
8.  Localisez l'élément `VSTemplate` suivant dans le fichier projet.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
    ```  
  
9. Remplacez cet élément par le code XML suivant.  
  
    ```  
    <VSTemplate Include="YourTemplateName.vstemplate">  
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>  
    </VSTemplate>  
    ```  
  
     L'élément `OutputSubPath` spécifie des dossiers supplémentaires dans le chemin d'accès où le modèle de projet est créé lorsque vous générez le projet.  Les dossiers spécifiés ici garantissent que le modèle d'élément sera disponible uniquement lorsque les clients ouvrez la boîte de dialogue **Ajouter un nouveau projet** , développez le nœud **SharePoint** , puis sélectionnez le nœud **2010** .  
  
10. Enregistrez et fermez le fichier.  
  
11. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet de modèle de projet ou d'élément, puis choisissez **Recharger le projet**.  
  
##### Pour inclure un modèle que vous créez manuellement  
  
1.  Ajoutez au projet VSIX un nouveau dossier devant contenir le modèle.  
  
2.  Sous ce nouveau dossier, créez les sous\-dossiers suivants, puis ajoutez le fichier modèle \(.zip\) au dossier *ID de paramètres régionaux*.  
  
     *VotreDossierModèle*  
  
     **SharePoint**  
  
     **SharePoint14**  
  
     *ID de paramètres régionaux*  
  
     *YourTemplateName*.zip  
  
     Par exemple, si vous disposez d'un modèle d'élément nommé ContosoCustomAction.zip qui prend en charge les paramètres régionaux Anglais \(États\-Unis\), le chemin d'accès complet peut correspondre à ItemTemplates\\SharePoint\\SharePoint14\\1033\\ContosoCustomAction.zip.  
  
3.  Dans **Explorateur de solutions**, sélectionnez le fichier modèle \(.zip\).*YourTemplateName*  
  
4.  Dans la fenêtre **Propriétés**, affectez à la propriété **Action de génération** la valeur **Contenu**.  
  
5.  Ouvrez le menu contextuel du fichier source.extension.vsixmanifest, puis choisissez **Ouvrir**.  
  
     Le fichier s'ouvre dans le concepteur.  
  
6.  Dans la section **Composants** de l'éditeur, choisissez le bouton **Nouveau** .  
  
     La boîte de dialogue **ajoutez le nouveau ressource** s'ouvre.  
  
7.  Dans la liste **Type** , choisissez **Microsoft.VisualStudio.ItemTemplate** ou **Microsoft.VisualStudio.ProjectTemplate**.  
  
8.  Dans la liste **Source** , choisissez **fichier sur le système de fichiers**.  
  
9. Dans le champ **Chemin d'accès** , entrez le chemin d'accès complet à l'assembly \(par exemple, **ItemTemplates \\SharePoint\\SharePoint14\\1033\\ContosoCustomAction .zip**, ou utilisez le bouton **Parcourir** pour rechercher et sélectionner l'assembly, puis choisissez le bouton **OK** .  
  
##### Pour inclure un Assistant pour un modèle de projet ou un modèle d'élément  
  
1.  Dans le projet VSIX, ouvrez le menu contextuel du fichier source.extension.vsixmanifest, puis choisissez **Ouvrir**.  
  
     Le fichier s'ouvre dans le concepteur.  
  
2.  Dans la section **Composants** de l'éditeur, choisissez le bouton **Nouveau** .  
  
     La boîte de dialogue **ajoutez le nouveau ressource** s'ouvre.  
  
3.  Dans la liste **Type** , choisissez **Microsoft.VisualStudio.Assembly**.  
  
4.  Dans la liste **Source** , effectuez l'une des étapes suivantes :  
  
    -   Si l'assembly d'assistant est généré à partir d'un projet figurant dans la même solution que le projet VSIX, choisissez **un projet dans la solution actuelle**.  Dans la liste **Projet** , sélectionnez le nom du projet.  
  
    -   Si l'assembly de l'assistant est inclus en tant que fichier dans votre projet, choisissez **Tapez du système de fichiers**.  Dans le champ **Chemin d'accès** , entrez le chemin d'accès complet au fichier d'assembly, ou utilisez le bouton **Parcourir** pour rechercher et sélectionner l'assembly.  
  
5.  Cliquez sur le bouton **OK**.  
  
### Procédures pas à pas connexes  
 Le tableau suivant répertorie les procédures pas à pas qui illustrent le mode d'utilisation d'un projet VSIX pour déployer différents types d'extensions d'outils SharePoint.  
  
|Type d'extension|Procédures pas à pas connexes|  
|----------------------|-----------------------------------|  
|Une extension qui inclut uniquement l'assembly d'extension|[Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)<br /><br /> [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)<br /><br /> [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)|  
|Une extension qui inclut des commandes SharePoint|[Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)<br /><br /> [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)<br /><br /> [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
|Une extension qui inclut un modèle Visual Studio|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)<br /><br /> [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, première partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)|  
|Une extension qui inclut un Assistant de modèle|[Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)<br /><br /> [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, deuxième partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)|  
  
## Création manuelle de packages VSIX  
 Si vous voulez créer manuellement le package VSIX pour votre extension d'outils SharePoint, exécutez les opérations suivantes :  
  
1.  Créez les fichiers extension.vsixmanifest et \[Content\_Types\].xml, ainsi que le fichier de package VSIX \(fichier .vsix\).  Pour plus d'informations, consultez [Anatomie d'un Package VSIX](../extensibility/anatomy-of-a-vsix-package.md) et [Procédure : création manuelle d’un package d’extension &#40;déploiement VSIX&#41;](../Topic/How%20to:%20Manually%20Package%20an%20Extension%20(VSIX%20Deployment).md).  
  
2.  Ajoutez votre assembly d'extension au package VSIX.  Si votre extension inclut une commande SharePoint, ajoutez également l'assembly qui implémente la commande SharePoint dans le package VSIX.  
  
3.  Modifiez le fichier extension.vsixmanifest :  
  
    -   Ajoutez un élément d' `Microsoft.VisualStudio.MefComponent` sous l'élément d' `Assets` , puis affectez la valeur du nouvel élément au chemin d'accès relatif de l'assembly qui implémente votre extension dans le package VSIX.  Pour plus d’informations, consultez [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/fr-fr/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
    -   Si votre extension inclut une commande SharePoint qui fait appel au modèle d'objet serveur pour SharePoint, ajoutez un élément d' `Microsoft.VisualStudio.Assembly` sous l'élément d' `Assets` .  Définissez la valeur du nouvel élément au chemin d'accès relatif de l'assembly qui implémente la commande SharePoint dans le package VSIX.  Pour plus d’informations, consultez [Élément de ressource \(schéma VSX\)](http://msdn.microsoft.com/fr-fr/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
    -   Si votre extension inclut un modèle de projet ou un modèle d'élément, ajoutez un élément d' `ProjectTemplate` ou d' `ItemTemplate` sous l'élément d' `Assets` .  Définissez la valeur du nouvel élément au chemin d'accès relatif du dossier qui contient le modèle dans le package VSIX.  Pour plus d'informations, consultez [NIB: ProjectTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/fr-fr/87add64c-9dcd-495f-8815-209dab182cb1) et [NIB: ItemTemplate Element \(VSX Schema\)](http://msdn.microsoft.com/fr-fr/1d489e54-c1c5-4f96-a510-6c2640867ff0).  
  
    -   Si votre extension inclut un Assistant personnalisé pour un modèle de projet ou un modèle d'élément, ajoutez un élément d' `Assembly` sous l'élément d' `Assets` .  Définissez la valeur du nouvel élément au chemin d'accès relatif de l'assembly dans le package VSIX, puis affectez à l'attribut d' `AssemblyName` le nom d'assembly qualifié complet \(notamment la version, culture, et jeton de clé publique\).  Pour plus d’informations, consultez [Élément de dépendance \(schéma VSX\)](http://msdn.microsoft.com/fr-fr/1f63f60a-98ad-48ec-8e44-4eba383d3e37).  
  
### Exemple  
 L'exemple suivant illustre le contenu d'un fichier extension.vsixmanifest d'une extension d'outils SharePoint.  L'extension est implémentée dans un assembly nommé Contoso.ProjectExtension.dll.  L'extension inclut un assembly de commande SharePoint nommé Contoso.ExtensionCommands.dll et un modèle d'élément sous un dossier nommé **ItemTemplates** dans le package VSIX.  Cet exemple suppose que les deux assemblys se trouvent dans le même dossier que le fichier extension.vsixmanifest du package VSIX.  
  
```  
<PackageManifest Version=”2.0.0” xmlns=”http://schemas.microsoft.com/developer/vsx-schema/2011”>  
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
  
## Voir aussi  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  