---
title: Créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e5b19f99cf9688191a5b6ef8ba8d4f58f4c6633c
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90739939"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-1"></a>Procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 1
  Vous pouvez étendre le système de projet SharePoint dans Visual Studio en créant vos propres types d’éléments de projet. Dans cette procédure pas à pas, vous allez créer un élément de projet qui peut être ajouté à un projet SharePoint pour créer une action personnalisée sur un site SharePoint. L’action personnalisée ajoute un élément de menu au menu **actions de site** du site SharePoint.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’une extension Visual Studio qui définit un nouveau type d’élément de projet SharePoint pour une action personnalisée. Le nouveau type d’élément de projet implémente plusieurs fonctionnalités personnalisées :

  - Menu contextuel qui sert de point de départ pour les tâches supplémentaires liées à l’élément de projet, telles que l’affichage d’un concepteur pour l’action personnalisée dans Visual Studio.

  - Code qui s’exécute lorsqu’un développeur modifie certaines propriétés de l’élément de projet et le projet qui le contient.

  - Icône personnalisée qui apparaît en regard de l’élément de projet dans **Explorateur de solutions**.

- Création d’un modèle d’élément Visual Studio pour l’élément de projet.

- Génération d’un package d’extension Visual Studio (VSIX) pour déployer le modèle d’élément de projet et l’assembly d’extension.

- Débogage et test de l’élément de projet.

  Il s’agit d’une procédure pas à pas autonome. Après avoir effectué cette procédure pas à pas, vous pouvez améliorer l’élément de projet en ajoutant un assistant au modèle d’élément. Pour plus d’informations, consultez [procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

> [!NOTE]
> Vous pouvez télécharger un exemple à partir de [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) qui montre comment créer des activités personnalisées pour un flux de travail.

## <a name="prerequisites"></a>Prérequis
 Pour effectuer cette procédure pas à pas, vous avez besoin des composants suivants sur l’ordinateur de développement :

- Éditions prises en charge de Microsoft Windows, SharePoint et Visual Studio.

- L’[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]opérateur Cette procédure pas à pas utilise le modèle de **projet VSIX** dans le kit de développement logiciel (SDK) pour créer un package VSIX afin de déployer l’élément de projet. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer la procédure pas à pas :

- Actions personnalisées dans SharePoint. Pour plus d’informations, consultez [action personnalisée](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

- Modèles d’élément dans Visual Studio. Pour plus d’informations, consultez [Création de modèles de projet et d’élément](../ide/creating-project-and-item-templates.md).

## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez créer trois projets :

- Projet VSIX. Ce projet crée le package VSIX pour déployer l’élément de projet SharePoint.

- Projet de modèle d’élément. Ce projet crée un modèle d’élément qui peut être utilisé pour ajouter l’élément de projet SharePoint à un projet SharePoint.

- Projet de bibliothèque de classes. Ce projet implémente une extension Visual Studio qui définit le comportement de l’élément de projet SharePoint.

  Démarrez la procédure pas à pas en créant les projets.

#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

3. Dans la liste située en haut de la boîte de dialogue **nouveau projet** , assurez-vous que **.NET Framework 4,5** est sélectionné.

4. Dans la boîte de dialogue **nouveau projet** , développez les nœuds **Visual C#** ou **Visual Basic** , puis choisissez le nœud **extensibilité** .

    > [!NOTE]
    > Le nœud **extensibilité** est disponible uniquement si vous installez le kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez la section conditions préalables, plus haut dans cette rubrique.

5. Choisissez le modèle de **projet VSIX** .

6. Dans la zone **nom** , entrez **CustomActionProjectItem**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **CustomActionProjectItem** à **Explorateur de solutions**.

#### <a name="to-create-the-item-template-project"></a>Pour créer le projet de modèle d’élément

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud solution, choisissez **Ajouter**, puis **nouveau projet**.

2. Dans la liste située en haut de la boîte de dialogue **nouveau projet** , assurez-vous que **.NET Framework 4,5** est sélectionné.

3. Dans la boîte de dialogue **nouveau projet** , développez les nœuds **Visual C#** ou **Visual Basic** , puis choisissez le nœud **extensibilité** .

4. Dans la liste des modèles de projet, choisissez le modèle **élément C#** ou modèle d' **élément Visual Basic** .

5. Dans la zone **nom** , entrez **ItemTemplate**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **ItemTemplate** à la solution.

#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud solution, choisissez **Ajouter**, puis **nouveau projet**.

2. Dans la liste située en haut de la boîte de dialogue **nouveau projet** , assurez-vous que **.NET Framework 4,5** est sélectionné.

3. Dans la boîte de dialogue **nouveau projet** , développez les nœuds **Visual C#** ou **Visual Basic** , choisissez le nœud **Windows** , puis choisissez le modèle de projet **bibliothèque de classes** .

4. Dans la zone **nom** , entrez **ProjectItemDefinition**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **ProjectItemDefinition** à la solution et ouvre le fichier de code Class1 par défaut.

5. Supprimez le fichier de code Class1 du projet.

## <a name="configure-the-extension-project"></a>Configurer le projet d’extension
 Avant d’écrire du code pour définir le type d’élément de projet SharePoint, vous devez ajouter des fichiers de code et des références d’assembly au projet d’extension.

#### <a name="to-configure-the-project"></a>Pour configurer le projet

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **ProjectItemDefinition** , choisissez **Ajouter**, puis **nouvel élément**.

2. Dans la liste des éléments de projet, choisissez **fichier de code**.

3. Dans la zone **nom** , entrez l' **CustomAction** de nom avec l’extension de nom de fichier appropriée, puis cliquez sur le bouton **Ajouter** .

4. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **ProjectItemDefinition** , puis choisissez **Ajouter une référence**.

5. Dans la boîte de dialogue **Gestionnaire de références-ProjectItemDefinition** , choisissez le nœud **assemblys** , puis le nœud **Framework** .

6. Activez la case à cocher en regard de chacun des assemblys suivants :

    - System.ComponentModel.Composition

    - System.Windows.Forms

7. Choisissez le nœud **Extensions** , activez la case à cocher en regard de l’assembly Microsoft. VisualStudio. SharePoint, puis choisissez le bouton **OK** .

## <a name="define-the-new-sharepoint-project-item-type"></a>Définir le nouveau type d’élément de projet SharePoint
 Créez une classe qui implémente l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface pour définir le comportement du nouveau type d’élément de projet. Implémentez cette interface chaque fois que vous souhaitez définir un nouveau type d’élément de projet.

#### <a name="to-define-the-new-sharepoint-project-item-type"></a>Pour définir le nouveau type d’élément de projet SharePoint

1. Dans le projet ProjectItemDefinition, ouvrez le fichier de code CustomAction.

2. Remplacez le code de ce fichier par le code suivant.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/CSharp/customactionprojectitem/projectitemtypedefinition/customaction.cs#1)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#1](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/projectitemdefinition/customaction.vb#1)]

## <a name="create-an-icon-for-the-project-item-in-solution-explorer"></a>Créer une icône pour l’élément de projet dans Explorateur de solutions
 Lorsque vous créez un élément de projet SharePoint personnalisé, vous pouvez associer une image (une icône ou une image bitmap) à l’élément de projet. Cette image apparaît en regard de l’élément de projet dans **Explorateur de solutions**.

 Dans la procédure suivante, vous allez créer une icône pour l’élément de projet et incorporer l’icône dans l’assembly d’extension. Cette icône est référencée par l' <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute> de la `CustomActionProjectItemTypeProvider` classe que vous avez créée précédemment.

#### <a name="to-create-a-custom-icon-for-the-project-item"></a>Pour créer une icône personnalisée pour l’élément de projet

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **ProjectItemDefinition** , choisissez **Ajouter**, puis **nouvel élément...**.

2. Dans la liste des éléments de projet, choisissez l’élément **icône fichier** .

    > [!NOTE]
    > Dans Visual Basic projets, vous devez choisir le nœud **général** pour afficher l’élément **icône de fichier** .

3. Dans la zone **nom** , entrez **CustomAction_SolutionExplorer. ico**, puis cliquez sur le bouton **Ajouter** .

     La nouvelle icône s’ouvre dans l' **éditeur d’images**.

4. Modifiez la version 16x16 du fichier icône afin qu’il dispose d’une conception que vous pouvez reconnaître, puis enregistrez le fichier d’icône.

5. Dans **Explorateur de solutions**, choisissez **CustomAction_SolutionExplorer. ico**.

6. Dans la fenêtre **Propriétés** , cliquez sur la flèche en regard de la propriété **action de génération** .

7. Dans la liste qui s’affiche, choisissez **ressource incorporée**.

## <a name="checkpoint"></a>Point de contrôle
 À ce stade de la procédure pas à pas, tout le code de l’élément de projet se trouve maintenant dans le projet. Générez le projet pour vérifier qu’il est compilé sans erreur.

#### <a name="to-build-your-project"></a>Pour générer votre projet

1. Ouvrez le menu contextuel du projet **ProjectItemDefinition** , puis choisissez **générer**.

## <a name="create-a-visual-studio-item-template"></a>Créer un modèle d’élément Visual Studio
 Pour permettre à d’autres développeurs d’utiliser votre élément de projet, vous devez créer un modèle de projet ou un modèle d’élément. Les développeurs utilisent ces modèles dans Visual Studio pour créer une instance de votre élément de projet en créant un nouveau projet, ou en ajoutant un élément à un projet existant. Pour cette procédure pas à pas, utilisez le projet ItemTemplate pour configurer votre élément de projet.

#### <a name="to-create-the-item-template"></a>Pour créer le modèle d’élément

1. Supprimez le fichier de code Class1 du projet ItemTemplate.

2. Dans le projet ItemTemplate, ouvrez le fichier *ItemTemplate. vstemplate* .

3. Remplacez le contenu du fichier par le code XML suivant, puis enregistrez et fermez le fichier.

    > [!NOTE]
    > Le code XML suivant est destiné à un modèle d’élément Visual C#. Si vous créez un modèle d’élément Visual Basic, remplacez la valeur de l' `ProjectType` élément par `VisualBasic` .

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
      <TemplateData>
        <DefaultName>CustomAction</DefaultName>
        <Name>Custom Action</Name>
        <Description>SharePoint Custom Action by Contoso</Description>
        <ProjectType>CSharp</ProjectType>
        <SortOrder>1000</SortOrder>
        <Icon>ItemTemplate.ico</Icon>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
      <TemplateContent>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\Elements.xml">Elements.xml</ProjectItem>
        <ProjectItem ReplaceParameters="true" TargetFileName="$fileinputname$\SharePointProjectItem.spdata">CustomAction.spdata</ProjectItem>
      </TemplateContent>
    </VSTemplate>
    ```

     Ce fichier définit le contenu et le comportement du modèle d’élément. Pour plus d’informations sur le contenu de ce fichier, consultez [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

4. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **ItemTemplate** , choisissez **Ajouter**, puis **nouvel élément**.

5. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez le modèle **fichier texte** .

6. Dans la zone **nom** , entrez **CustomAction. resdonnées**, puis cliquez sur le bouton **Ajouter** .

7. Ajoutez le code XML suivant au fichier *CustomAction. resdata* , puis enregistrez et fermez le fichier.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <ProjectItem Type="Contoso.CustomAction" DefaultFile="Elements.xml"
     xmlns="http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel">
      <Files>
        <ProjectItemFile Source="Elements.xml" Target="$fileinputname$\" Type="ElementManifest" />
      </Files>
    </ProjectItem>
    ```

     Ce fichier contient des informations sur les fichiers qui sont contenus par l’élément de projet. L' `Type` attribut de l' `ProjectItem` élément doit être défini sur la même chaîne que celle qui est passée au <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> sur la définition de l’élément de projet (la `CustomActionProjectItemTypeProvider` classe que vous avez créée précédemment dans cette procédure pas à pas). Pour plus d’informations sur le contenu des fichiers *. resdonnées* , consultez [Référence du schéma d’élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md).

8. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **ItemTemplate** , choisissez **Ajouter**, puis **nouvel élément**.

9. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez le modèle de **fichier XML** .

10. Dans la zone **nom** , entrez **Elements.xml**, puis cliquez sur le bouton **Ajouter** .

11. Remplacez le contenu du fichier *Elements.xml* par le code XML suivant, puis enregistrez et fermez le fichier.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">
      <CustomAction Id="Replace this with a GUID or some other unique string"
                    GroupId="SiteActions"
                    Location="Microsoft.SharePoint.StandardMenu"
                    Sequence="1000"
                    Title="Replace this with your title"
                    Description="Replace this with your description" >
        <UrlAction Url="~site/Lists/Tasks/AllItems.aspx"/>
      </CustomAction>
    </Elements>
    ```

     Ce fichier définit une action personnalisée par défaut qui crée un élément de menu dans le menu **actions du site** SharePoint. Quand un utilisateur choisit l’élément de menu, l’URL spécifiée dans l' `UrlAction` élément s’ouvre dans le navigateur Web. Pour plus d’informations sur les éléments XML que vous pouvez utiliser pour définir une action personnalisée, consultez [définitions des actions personnalisées](/sharepoint/dev/schema/custom-action-definition-schema).

12. Si vous le souhaitez, ouvrez le fichier *ItemTemplate. ico* et modifiez-le afin qu’il dispose d’une conception que vous pouvez reconnaître. Cette icône s’affiche en regard de l’élément de projet dans la boîte de dialogue **Ajouter un nouvel élément** .

13. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **ItemTemplate** , puis choisissez **décharger le projet**.

14. Rouvrez le menu contextuel du projet **ItemTemplate** , puis choisissez **modifier ItemTemplate. csproj** ou **modifier ItemTemplate. vbproj**.

15. Localisez l' `VSTemplate` élément suivant dans le fichier projet.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
    ```

16. Remplacez cet `VSTemplate` élément par le code XML suivant, puis enregistrez et fermez le fichier.

    ```xml
    <VSTemplate Include="ItemTemplate.vstemplate">
      <OutputSubPath>SharePoint\SharePoint14</OutputSubPath>
    </VSTemplate>
    ```

     L' `OutputSubPath` élément spécifie des dossiers supplémentaires dans le chemin d’accès sous lequel le modèle d’élément est créé lorsque vous générez le projet. Les dossiers spécifiés ici garantissent que le modèle d’élément sera disponible uniquement lorsque les clients ouvriront la boîte de dialogue **Ajouter un nouvel élément** , développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

17. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **ItemTemplate** , puis choisissez **recharger le projet**.

## <a name="create-a-vsix-package-to-deploy-the-project-item"></a>Créer un package VSIX pour déployer l’élément de projet
 Pour déployer l’extension, utilisez le projet VSIX dans votre solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source. extension. vsixmanifest qui est inclus dans le projet VSIX. Ensuite, créez le package VSIX en générant la solution.

#### <a name="to-configure-and-create-the-vsix-package"></a>Pour configurer et créer le package VSIX

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du fichier **source. extension. vsixmanifest** dans le projet CustomActionProjectItem, puis choisissez **ouvrir**.

     Visual Studio ouvre le fichier dans l’éditeur de manifeste. Le fichier source. extension. vsixmanifest est la base du fichier extension. vsixmanifest requis par tous les packages VSIX. Pour plus d’informations sur ce fichier, consultez [Référence du schéma d’extension VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Dans la zone **nom du produit** , entrez élément de projet d' **action personnalisée**.

3. Dans la zone **auteur** , entrez **contoso**.

4. Dans la zone **Description** , entrez **un élément de projet SharePoint qui représente une action personnalisée**.

5. Sous l’onglet **ressources** , cliquez sur le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’affiche.

6. Dans la liste **type** , choisissez **Microsoft. VisualStudio. ItemTemplate**.

    > [!NOTE]
    > Cette valeur correspond à l' `ItemTemplate` élément dans le fichier extension. vsixmanifest. Cet élément identifie le sous-dossier du package VSIX qui contient le modèle d’élément de projet. Pour plus d’informations, consultez [élément ItemTemplate (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393681\(v\=vs.100\)).

7. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

8. Dans la liste **projet** , choisissez **ItemTemplate**, puis choisissez le bouton **OK** .

9. Dans l’onglet **ressources** , cliquez à nouveau sur le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’affiche.

10. Dans la liste **type** , choisissez **Microsoft. VisualStudio. MEFComponent**.

    > [!NOTE]
    > Cette valeur correspond à l' `MefComponent` élément dans le fichier extension. vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MefComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

11. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

12. Dans la liste **projet** , choisissez **ProjectItemDefinition**.

13. Choisissez le bouton **OK**.

14. Dans la barre de menus, choisissez **générer**  >  **générer la solution**, puis assurez-vous que le projet se compile sans erreur.

15. Assurez-vous que le dossier de sortie de la génération pour le projet CustomActionProjectItem contient le fichier CustomActionProjectItem. vsix.

     Par défaut, le dossier de sortie de la génération est le.. dossier \bin\Debug sous le dossier qui contient le projet CustomActionProjectItem.

## <a name="test-the-project-item"></a>Tester l’élément de projet
 Vous êtes maintenant prêt à tester l’élément de projet. Tout d’abord, commencez à déboguer la solution CustomActionProjectItem dans l’instance expérimentale de Visual Studio. Ensuite, testez l’élément de projet d' **action personnalisée** dans un projet SharePoint dans l’instance expérimentale de Visual Studio. Enfin, générez et exécutez le projet SharePoint pour vérifier que l’action personnalisée fonctionne comme prévu.

#### <a name="to-start-debugging-the-solution"></a>Pour démarrer le débogage de la solution

1. Redémarrez Visual Studio avec les informations d’identification d’administration, puis ouvrez la solution CustomActionProjectItem.

2. Ouvrez le fichier de code CustomAction, puis ajoutez un point d’arrêt à la première ligne de code dans la `InitializeType` méthode.

3. Appuyez sur la touche **F5** pour démarrer le débogage.

     Visual Studio installe l’extension dans le projet d’action%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\Custom Item\1.0 et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.

#### <a name="to-test-the-project-item-in-visual-studio"></a>Pour tester l’élément de projet dans Visual Studio

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

2. Développez **Visual C#** ou **Visual Basic** (selon la langue prise en charge par votre modèle d’élément), développez **SharePoint**, puis choisissez le nœud **2010** .

3. Dans la liste des modèles de projet, choisissez **projet SharePoint 2010**.

4. Dans la zone **nom** , entrez **CustomActionTest**, puis choisissez le bouton **OK** .

5. Dans l' **Assistant Personnalisation de SharePoint**, entrez l’URL du site que vous souhaitez utiliser pour le débogage, puis choisissez le bouton **Terminer** .

6. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet, choisissez **Ajouter**, puis **nouvel élément**.

7. Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez le nœud **2010** sous le nœud **SharePoint** .

     Vérifiez que l’élément d' **action personnalisé** s’affiche dans la liste des éléments de projet.

8. Choisissez l’élément d' **action personnalisée** , puis cliquez sur le bouton **Ajouter** .

     Visual Studio ajoute un élément nommé **CustomAction1** à votre projet et ouvre le fichier *Elements.xml* dans l’éditeur.

9. Vérifiez que le code de l’autre instance de Visual Studio s’arrête sur le point d’arrêt que vous avez défini précédemment dans la `InitializeType` méthode.

10. Appuyez sur la touche **F5** pour continuer à déboguer le projet.

11. Dans l’instance expérimentale de Visual Studio, dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud **CustomAction1** , puis choisissez **afficher le concepteur d’actions personnalisées**.

12. Vérifiez qu’une boîte de message s’affiche, puis choisissez le bouton **OK** .

     Vous pouvez utiliser ce menu contextuel pour fournir des options ou des commandes supplémentaires aux développeurs, telles que l’affichage d’un concepteur pour l’action personnalisée.

13. Dans la barre de menus, choisissez **Afficher**la  >  **sortie**.

     La fenêtre **sortie** s’ouvre.

14. Dans **Explorateur de solutions**, ouvrez le menu contextuel de l’élément **CustomAction1** , puis remplacez son nom par **MyCustomAction**.

     Dans la fenêtre **sortie** , un message de confirmation s’affiche. Ce message est écrit par le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemNameChanged> Gestionnaire d’événements que vous avez défini dans la `CustomActionProjectItemTypeProvider` classe. Vous pouvez gérer cet événement et d’autres événements d’élément de projet pour implémenter un comportement personnalisé lorsque le développeur modifie l’élément de projet.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Pour tester l’action personnalisée dans SharePoint

1. Dans l’instance expérimentale de Visual Studio, ouvrez le fichier *Elements.xml* qui est un enfant de l’élément de projet **MyCustomAction** .

2. Dans le fichier *Elements.xml* , apportez les modifications suivantes, puis enregistrez le fichier :

    - Dans l' `CustomAction` élément, définissez l' `Id` attribut sur un GUID ou une autre chaîne unique, comme le montre l’exemple suivant :

        ```xml
        Id="cd85f6a7-af2e-44ab-885a-0c795b52121a"
        ```

    - Dans l' `CustomAction` élément, définissez l' `Title` attribut comme dans l’exemple suivant :

        ```xml
        Title="SharePoint Developer Center"
        ```

    - Dans l' `CustomAction` élément, définissez l' `Description` attribut comme dans l’exemple suivant :

        ```xml
        Description="Opens the SharePoint Developer Center Web site."
        ```

    - Dans l' `UrlAction` élément, définissez l' `Url` attribut comme dans l’exemple suivant :

        ```xml
        Url="https://docs.microsoft.com/sharepoint/dev/"
        ```

3. Choisissez la touche **F5**.

     L’action personnalisée est empaquetée et déployée sur le site SharePoint spécifié dans la propriété **URL du site** du projet. Le navigateur Web s’ouvre sur la page par défaut de ce site.

    > [!NOTE]
    > Si la boîte de dialogue **débogage de script désactivé** s’affiche, choisissez le bouton **Oui** pour continuer à déboguer le projet.

4. Dans le menu **actions du site** , choisissez Centre de **développement SharePoint**, vérifiez que le navigateur ouvre le site Web, puis https://docs.microsoft.com/sharepoint/dev/ fermez le navigateur Web.

## <a name="clean-up-the-development-computer"></a>Nettoyer l’ordinateur de développement
 Une fois que vous avez fini de tester l’élément de projet, supprimez le modèle d’élément de projet de l’instance expérimentale de Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Pour nettoyer l’ordinateur de développement

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **Outils**  >  **extensions et mises à jour**.

     La boîte de dialogue **Extensions et mises à jour** s’ouvre.

2. Dans la liste des extensions, choisissez **élément de projet action personnalisée**, puis cliquez sur le bouton **désinstaller** .

3. Dans la boîte de dialogue qui s’affiche, choisissez le bouton **Oui** pour confirmer que vous souhaitez désinstaller l’extension.

4. Choisissez le bouton **redémarrer maintenant** pour terminer la désinstallation.

5. Fermez l’instance expérimentale de Visual Studio et l’instance dans laquelle la solution CustomActionProjectItem est ouverte.

## <a name="next-steps"></a>Étapes suivantes
 Après avoir effectué cette procédure pas à pas, vous pouvez ajouter un assistant au modèle d’élément. Quand un utilisateur ajoute un élément de projet d’action personnalisé à un projet SharePoint, l’Assistant recueille des informations sur l’action (par exemple, son emplacement et l’URL vers laquelle naviguer lorsque l’action est choisie) et ajoute ces informations au fichier *Elements.xml* dans le nouvel élément de projet. Pour plus d’informations, consultez [procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Définir des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Utiliser le service de projet SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Éditeur d’images pour les icônes](/cpp/windows/image-editor-for-icons)
- [Création d’une icône ou d’une autre image &#40;éditeur d’images pour les icônes&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)