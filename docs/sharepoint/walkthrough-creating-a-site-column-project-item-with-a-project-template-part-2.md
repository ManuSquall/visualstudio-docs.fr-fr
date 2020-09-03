---
title: Créer un élément de projet colonne de site avec un modèle de projet, partie 2
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c3b84d901a1fd94d72ff14ec5c481e04676c5cbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016397"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 2
  Une fois que vous avez défini un type personnalisé d’élément de projet SharePoint et que vous l’avez associé à un modèle de projet dans Visual Studio, vous pouvez également fournir un Assistant pour le modèle. Vous pouvez utiliser l’Assistant pour collecter des informations auprès des utilisateurs lorsqu’ils utilisent votre modèle pour créer un nouveau projet qui contient l’élément de projet. Les informations que vous recueillez peuvent être utilisées pour initialiser l’élément de projet.

 Dans cette procédure pas à pas, vous allez ajouter un assistant au modèle de projet colonne de site illustré dans [procédure pas à pas : création d’un élément de projet de colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Lorsqu’un utilisateur crée un projet de colonne de site, l’Assistant recueille des informations sur la colonne de site (par exemple, son type de base et son groupe) et ajoute ces informations au fichier *Elements.xml* dans le nouveau projet.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un Assistant pour un type d’élément de projet SharePoint personnalisé associé à un modèle de projet.

- Définition d’une interface utilisateur d’Assistant personnalisée qui ressemble aux Assistants intégrés pour les projets SharePoint dans Visual Studio.

- Création de deux *commandes SharePoint* utilisées pour appeler le site SharePoint local pendant l’exécution de l’Assistant. Les commandes SharePoint sont des méthodes qui peuvent être utilisées par les extensions Visual Studio pour appeler des API dans le modèle objet serveur SharePoint. Pour plus d’informations, consultez [appel des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- L’utilisation de paramètres remplaçables pour initialiser les fichiers projet SharePoint avec les données que vous collectez dans l’Assistant.

- Création d’un nouveau fichier. snk dans chaque nouvelle instance de projet de colonne de site. Ce fichier est utilisé pour signer la sortie du projet afin que l’assembly de solution SharePoint puisse être déployé sur le Global Assembly Cache.

- Débogage et test de l’Assistant.

> [!NOTE]
> Pour obtenir une série d’exemples de flux de travail, consultez [exemples de flux](/sharepoint/dev/general-development/sharepoint-workflow-samples)de travail SharePoint.

## <a name="prerequisites"></a>Prérequis
 Pour effectuer cette procédure pas à pas, vous devez d’abord créer la solution SiteColumnProjectItem en effectuant la [procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Pour effectuer cette procédure pas à pas, vous avez également besoin des composants suivants sur l’ordinateur de développement :

- Éditions prises en charge de Windows, SharePoint et Visual Studio.

- Le kit de développement logiciel (SDK) Visual Studio. Cette procédure pas à pas utilise le modèle de **projet VSIX** dans le kit de développement logiciel (SDK) pour créer un package VSIX afin de déployer l’élément de projet. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer la procédure pas à pas :

- Assistants pour les modèles de projet et d’élément dans Visual Studio. Pour plus d’informations, consultez [Comment : utiliser des assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md) et l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.

- Colonnes de site dans SharePoint. Pour plus d’informations, consultez [colonnes](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

## <a name="understand-the-wizard-components"></a>Présentation des composants de l’Assistant
 L’Assistant illustré dans cette procédure pas à pas contient plusieurs composants. Le tableau suivant décrit ces composants.

|Composant|Description|
|---------------|-----------------|
|Implémentation de l’Assistant|Il s’agit d’une classe, nommée `SiteColumnProjectWizard` , qui implémente l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface. Cette interface définit les méthodes que Visual Studio appelle lorsque l’Assistant démarre et se termine, et à certains moments de l’exécution de l’Assistant.|
|Interface utilisateur de l’Assistant|Il s’agit d’une fenêtre WPF, nommée `WizardWindow` . Cette fenêtre comprend deux contrôles utilisateur, nommés `Page1` et `Page2` . Ces contrôles utilisateur représentent les deux pages de l’Assistant.<br /><br /> Dans cette procédure pas à pas, la <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> méthode de l’implémentation de l’Assistant affiche l’interface utilisateur de l’Assistant.|
|Modèle de données de l’Assistant|Il s’agit d’une classe intermédiaire, nommée `SiteColumnWizardModel` , qui fournit une couche entre l’interface utilisateur de l’Assistant et l’implémentation de l’Assistant. Cet exemple utilise cette classe pour faciliter l’abstraction de l’implémentation de l’Assistant et de l’interface utilisateur de l’Assistant. Cette classe n’est pas un composant obligatoire de tous les assistants.<br /><br /> Dans cette procédure pas à pas, l’implémentation de l’Assistant passe un `SiteColumnWizardModel` objet à la fenêtre de l’Assistant lorsqu’il affiche l’interface utilisateur de l’Assistant. L’interface utilisateur de l’Assistant utilise les méthodes de cet objet pour enregistrer les valeurs des contrôles dans l’interface utilisateur et pour effectuer des tâches telles que la vérification de la validité de l’URL d’entrée du site. Une fois que l’utilisateur a terminé l’Assistant, l’implémentation de l’Assistant utilise l' `SiteColumnWizardModel` objet pour déterminer l’état final de l’interface utilisateur.|
|Gestionnaire de signature de projet|Il s’agit d’une classe d’assistance, nommée `ProjectSigningManager` , qui est utilisée par l’implémentation de l’Assistant pour créer un nouveau fichier Key. snk dans chaque nouvelle instance de projet.|
|commandes SharePoint|Il s’agit de méthodes utilisées par le modèle de données de l’Assistant pour appeler le site SharePoint local pendant que l’Assistant est en cours d’exécution. Étant donné que les commandes SharePoint doivent cibler le .NET Framework 3,5, ces commandes sont implémentées dans un assembly différent du reste du code de l’Assistant.|

## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez ajouter plusieurs projets à la solution SiteColumnProjectItem que vous avez créée dans [procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):

- Projet WPF. Vous allez implémenter l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface et définir l’interface utilisateur de l’Assistant dans ce projet.

- Projet de bibliothèque de classes qui définit les commandes SharePoint. Ce projet doit cibler the.NET Framework 3,5.

  Démarrez la procédure pas à pas en créant les projets.

#### <a name="to-create-the-wpf-project"></a>Pour créer le projet WPF

1. Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , ouvrez la solution SiteColumnProjectItem.

2. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution **SiteColumnProjectItem** , choisissez **Ajouter**, puis **nouveau projet**.

3. En haut de la boîte de dialogue **Ajouter un nouveau projet** , assurez-vous que **.NET Framework 4,5** est choisi dans la liste des versions du .NET Framework.

4. Développez le nœud **Visual C#** ou le nœud **Visual Basic** , puis choisissez le nœud **Windows** .

5. Dans la liste des modèles de projet, choisissez **bibliothèque de contrôles utilisateur WPF**, nommez le projet **ProjectTemplateWizard**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **ProjectTemplateWizard** à la solution et ouvre le fichier UserControl1. XAML par défaut.

6. Supprimez le fichier UserControl1. xaml du projet.

#### <a name="to-create-the-sharepoint-commands-project"></a>Pour créer le projet de commandes SharePoint

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution SiteColumnProjectItem, choisissez **Ajouter**, puis **nouveau projet**.

2. En haut de la boîte de dialogue **Ajouter un nouveau projet** , choisissez **.NET Framework 3,5** dans la liste des versions du .NET Framework.

3. Développez le nœud **Visual C#** ou le nœud  **Visual Basic** , puis choisissez le nœud **Windows** .

4. Choisissez le modèle de projet **bibliothèque de classes** , nommez le projet **SharePointCommands**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **SharePointCommands** à la solution et ouvre le fichier de code Class1 par défaut.

5. Supprimez le fichier de code Class1 du projet.

## <a name="configure-the-projects"></a>Configurer les projets
 Avant de créer l’Assistant, vous devez ajouter des fichiers de code et des références d’assembly aux projets.

#### <a name="to-configure-the-wizard-project"></a>Pour configurer le projet de l’Assistant

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **ProjectTemplateWizard** , puis choisissez **Propriétés**.

2. Dans le **Concepteur de projet**, choisissez l’onglet **application** pour un projet Visual C# ou l’onglet **compiler** pour un projet Visual Basic.

3. Assurez-vous que la version cible de .NET Framework est définie sur le .NET Framework 4,5, et non sur le profil client .NET Framework 4,5.

     Pour plus d’informations, consultez [Comment : cibler une version du .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

4. Ouvrez le menu contextuel du projet **ProjectTemplateWizard** , choisissez **Ajouter**, puis **nouvel élément**.

5. Choisissez l’élément **fenêtre (WPF)** , nommez l’élément **WizardWindow**, puis cliquez sur le bouton **Ajouter** .

6. Ajoutez deux éléments de **contrôle utilisateur (WPF)** au projet et nommez-les **Page1** et **page2**.

7. Ajoutez quatre fichiers de code au projet et donnez-leur les noms suivants :

    - SiteColumnProjectWizard

    - SiteColumnWizardModel

    - ProjectSigningManager

    - ID

8. Ouvrez le menu contextuel du nœud de projet **ProjectTemplateWizard** , puis choisissez **Ajouter une référence**.

9. Développez le nœud **assemblys** , choisissez le nœud **Extensions** , puis activez les cases à cocher en regard des assemblys suivants :

    - EnvDTE

    - Microsoft. VisualStudio. OLE. Interop

    - Microsoft. VisualStudio. SharePoint

    - Microsoft. VisualStudio. Shell. 11.0

    - Microsoft. VisualStudio. Shell. Interop. 10.0

    - Microsoft. VisualStudio. Shell. Interop. 11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

10. Choisissez le bouton **OK** pour ajouter les assemblys au projet.

11. Dans **Explorateur de solutions**, sous le dossier **références** du projet **ProjectTemplateWizard** , choisissez **EnvDTE**.

12. Dans la fenêtre **Propriétés** , remplacez la valeur de la propriété **incorporer les types Interop** par **false**.

13. Si vous développez un projet Visual Basic, importez l’espace de noms ProjectTemplateWizard dans votre projet à l’aide du **Concepteur de projet**.

     Pour plus d’informations, consultez [procédure : ajouter ou supprimer des espaces de noms Importés &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).

#### <a name="to-configure-the-sharepointcommands-project"></a>Pour configurer le projet SharePointcommands

1. Dans **Explorateur de solutions**, choisissez le nœud de projet **SharePointCommands** .

2. Dans la barre de menus, choisissez **projet**,  **Ajouter un élément existant**.

3. Dans la boîte de dialogue **Ajouter un élément existant** , accédez au dossier qui contient les fichiers de code du projet ProjectTemplateWizard, puis sélectionnez le fichier de code **ID** .

4. Cliquez sur la flèche en regard du bouton **Ajouter** , puis sélectionnez l’option **Ajouter en tant que lien** dans le menu qui s’affiche.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le fichier de code au projet **SharePointCommands** sous forme de lien. Le fichier de code se trouve dans le projet **ProjectTemplateWizard** , mais le code du fichier est également compilé dans le projet **SharePointCommands** .

5. Dans le projet **SharePointCommands** , ajoutez un autre fichier de code nommé commandes.

6. Choisissez le projet SharePointCommands, puis, dans la barre de menus, choisissez **projet**  >  **Ajouter une référence**.

7. Développez le nœud **assemblys** , choisissez le nœud **Extensions** , puis activez les cases à cocher en regard des assemblys suivants :

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

8. Choisissez le bouton **OK** pour ajouter les assemblys au projet.

## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Créer le modèle d’Assistant, le gestionnaire de signature et les ID de commande SharePoint
 Ajoutez du code au projet ProjectTemplateWizard pour implémenter les composants suivants dans l’exemple :

- ID de commande SharePoint. Ces chaînes identifient les commandes SharePoint que l’Assistant utilise. Plus loin dans cette procédure pas à pas, vous ajouterez du code au projet SharePointCommands pour implémenter les commandes.

- Modèle de données de l’Assistant.

- Gestionnaire de signature du projet.

  Pour plus d’informations sur ces composants, consultez [Présentation des composants de l’Assistant](#understand-the-wizard-components).

#### <a name="to-define-the-sharepoint-command-ids"></a>Pour définir les ID de commande SharePoint

1. Dans le projet ProjectTemplateWizard, ouvrez le fichier de code ID, puis remplacez l’intégralité du contenu de ce fichier par le code suivant.

     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]

#### <a name="to-create-the-wizard-model"></a>Pour créer le modèle d’Assistant

1. Ouvrez le fichier de code SiteColumnWizardModel et remplacez l’intégralité du contenu de ce fichier par le code suivant.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]

#### <a name="to-create-the-project-signing-manager"></a>Pour créer le gestionnaire de signature de projet

1. Ouvrez le fichier de code ProjectSigningManager, puis remplacez tout le contenu de ce fichier par le code suivant.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]

## <a name="create-the-wizard-ui"></a>Créer l’interface utilisateur de l’Assistant
 Ajoutez du code XAML pour définir l’interface utilisateur de la fenêtre de l’Assistant et les deux contrôles utilisateur qui fournissent l’interface utilisateur pour les pages de l’Assistant, et ajoutez du code pour définir le comportement de la fenêtre et des contrôles utilisateur. L’Assistant que vous créez ressemble à l’Assistant intégré pour les projets SharePoint dans Visual Studio.

> [!NOTE]
> Dans les étapes suivantes, votre projet comportera des erreurs de compilation après l’ajout du code XAML ou du code à votre projet. Ces erreurs disparaissent lorsque vous ajoutez du code dans les étapes ultérieures.

#### <a name="to-create-the-wizard-window-ui"></a>Pour créer l’interface utilisateur de la fenêtre de l’Assistant

1. Dans le projet ProjectTemplateWizard, ouvrez le menu contextuel du fichier WizardWindow. xaml, puis choisissez **ouvrir** pour ouvrir la fenêtre dans le concepteur.

2. Dans la vue XAML du concepteur, remplacez le code XAML actuel par le code XAML suivant. Le code XAML définit une interface utilisateur qui inclut un en-tête, un <xref:System.Windows.Controls.Grid> qui contient les pages de l’Assistant et des boutons de navigation en bas de la fenêtre.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]

    > [!NOTE]
    > La fenêtre créée dans ce XAML est dérivée de la <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe de base. Quand vous ajoutez une boîte de dialogue WPF personnalisée à Visual Studio, nous vous recommandons de dériver votre boîte de dialogue de cette classe pour que les styles soient cohérents avec les autres boîtes de dialogue de Visual Studio et d’éviter les problèmes de dialogue modaux qui pourraient se produire autrement. Pour plus d’informations, consultez [création et gestion de boîtes de dialogue modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Si vous développez un projet Visual Basic, supprimez l' `ProjectTemplateWizard` espace de noms du `WizardWindow` nom de classe dans l' `x:Class` attribut de l' `Window` élément. Cet élément se trouve dans la première ligne du code XAML. Lorsque vous avez terminé, la première ligne doit ressembler à l’exemple suivant.

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Ouvrez le fichier code-behind pour le fichier WizardWindow. Xaml.

5. Remplacez le contenu de ce fichier, à l’exception des `using` déclarations situées en haut du fichier, par le code suivant.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]

#### <a name="to-create-the-first-wizard-page-ui"></a>Pour créer l’interface utilisateur de la première page de l’Assistant

1. Dans le projet ProjectTemplateWizard, ouvrez le menu contextuel du fichier Page1. xaml, puis choisissez **ouvrir** pour ouvrir le contrôle utilisateur dans le concepteur.

2. Dans la vue XAML du concepteur, remplacez le code XAML actuel par le code XAML suivant. Le code XAML définit une interface utilisateur qui comprend une zone de texte dans laquelle les utilisateurs peuvent entrer l’URL des sites locaux qu’ils souhaitent utiliser pour le débogage. L’interface utilisateur comprend également des cases d’option permettant aux utilisateurs de spécifier si le projet est en mode bac à sable (sandbox).

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]

3. Si vous développez un projet Visual Basic, supprimez l' `ProjectTemplateWizard` espace de noms du `Page1` nom de classe dans l' `x:Class` attribut de l' `UserControl` élément. Il s’agit de la première ligne du code XAML. Lorsque vous avez terminé, la première ligne doit ressembler à ce qui suit.

    ```xml
    <UserControl x:Class="Page1"
    ```

4. Remplacez le contenu du fichier Page1. xaml, à l’exception des `using` déclarations situées en haut du fichier, par le code suivant.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]

#### <a name="to-create-the-second-wizard-page-ui"></a>Pour créer la deuxième interface utilisateur de la page d’Assistant

1. Dans le projet ProjectTemplateWizard, ouvrez le menu contextuel du fichier page2. xaml, puis choisissez **ouvrir**.

     Le contrôle utilisateur s'ouvre dans le concepteur.

2. Dans la vue XAML, remplacez le code XAML actuel par le code XAML suivant. Le code XAML définit une interface utilisateur qui comprend une liste déroulante permettant de choisir le type de base de la colonne de site, une zone de liste déroulante permettant de spécifier un groupe intégré ou personnalisé sous lequel afficher la colonne de site dans la Galerie, et une zone de texte pour spécifier le nom de la colonne de site.

     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]

3. Si vous développez un projet Visual Basic, supprimez l' `ProjectTemplateWizard` espace de noms du `Page2` nom de classe dans l' `x:Class` attribut de l' `UserControl` élément. Il s’agit de la première ligne du code XAML. Lorsque vous avez terminé, la première ligne doit ressembler à ce qui suit.

    ```xml
    <UserControl x:Class="Page2"
    ```

4. Remplacez le contenu du fichier code-behind pour le fichier page2. xaml, à l’exception des `using` déclarations situées en haut du fichier, par le code suivant.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]

## <a name="implement-the-wizard"></a>Implémenter l’Assistant
 Définissez les fonctionnalités principales de l’Assistant en implémentant l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface. Cette interface définit les méthodes que Visual Studio appelle lorsque l’Assistant démarre et se termine, et à certains moments de l’exécution de l’Assistant.

#### <a name="to-implement-the-wizard"></a>Pour implémenter l’Assistant

1. Dans le projet ProjectTemplateWizard, ouvrez le fichier de code SiteColumnProjectWizard.

2. Remplacez l’intégralité du contenu de ce fichier par le code suivant.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]

## <a name="create-the-sharepoint-commands"></a>Créer les commandes SharePoint
 Créez deux commandes personnalisées qui appellent le modèle d’objet serveur SharePoint. Une commande détermine si l’URL de site que l’utilisateur tape dans l’Assistant est valide. L’autre commande obtient tous les types de champs du site SharePoint spécifié afin que les utilisateurs puissent sélectionner celui à utiliser comme base pour la nouvelle colonne de site.

#### <a name="to-define-the-sharepoint-commands"></a>Pour définir les commandes SharePoint

1. Dans le projet **SharePointCommands** , ouvrez le fichier de code Commands.

2. Remplacez l’intégralité du contenu de ce fichier par le code suivant.

     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]

## <a name="checkpoint"></a>Point de contrôle
 À ce stade de la procédure pas à pas, tout le code de l’Assistant se trouve maintenant dans le projet. Générez le projet pour vous assurer qu’il se compile sans erreur.

#### <a name="to-build-your-project"></a>Pour générer votre projet

1. Dans la barre de menus, choisissez **générer**  >  **générer la solution**.

## <a name="removing-the-keysnk-file-from-the-project-template"></a>Suppression du fichier Key. snk du modèle de projet
 Dans [procédure pas à pas : création d’un élément de projet de colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), le modèle de projet que vous avez créé contient un fichier Key. snk qui est utilisé pour signer chaque instance de projet de colonne de site. Ce fichier Key. snk n’est plus nécessaire, car l’Assistant génère à présent un nouveau fichier Key. snk pour chaque projet. Supprimez le fichier Key. snk du modèle de projet et supprimez les références à ce fichier.

#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Pour supprimer le fichier Key. snk du modèle de projet

1. Dans **Explorateur de solutions**, sous le nœud **SiteColumnProjectTemplate** , ouvrez le menu contextuel du fichier **Key. snk** , puis choisissez **supprimer**.

2. Dans la boîte de dialogue de confirmation qui apparaît, cliquez sur le bouton **OK**.

3. Sous le nœud **SiteColumnProjectTemplate** , ouvrez le fichier SiteColumnProjectTemplate. vstemplate, puis supprimez l’élément suivant.

    ```xml
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>
    ```

4. Enregistrez et fermez le fichier.

5. Sous le nœud **SiteColumnProjectTemplate** , ouvrez le fichier ProjectTemplate. csproj ou ProjectTemplate. vbproj, puis supprimez l' `PropertyGroup` élément suivant.

    ```xml
    <PropertyGroup>
      <SignAssembly>true</SignAssembly>
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>
    </PropertyGroup>
    ```

6. Supprimez l' `None` élément suivant.

    ```xml
    <None Include="key.snk" />
    ```

7. Enregistrez et fermez le fichier.

## <a name="associating-the-wizard-with-the-project-template"></a>Association de l’Assistant avec le modèle de projet
 Maintenant que vous avez implémenté l’Assistant, vous devez associer l’Assistant au modèle de projet **colonne de site** . Pour ce faire, vous devez effectuer les trois procédures suivantes :

1. Signez l’assembly de l’Assistant avec un nom fort.

2. Obtient le jeton de clé publique pour l’assembly de l’Assistant.

3. Ajoutez une référence à l’assembly de l’Assistant dans le fichier. vstemplate du modèle de projet **colonne de site** .

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Pour signer l’assembly de l’Assistant avec un nom fort

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **ProjectTemplateWizard** , puis choisissez **Propriétés**.

2. Sous l'onglet **Signature**, activez la case à cocher **Signer l'assembly**.

3. Dans la liste **choisir un fichier de clé de nom fort** , choisissez **\<New...>** .

4. Dans la boîte de dialogue **créer une clé de nom fort** , entrez un nom pour le nouveau fichier de clé, désactivez la case à cocher **protéger le fichier de clé avec un mot de passe** , puis choisissez le bouton **OK** .

5. Ouvrez le menu contextuel du projet **ProjectTemplateWizard** , puis choisissez **générer** pour créer le fichier ProjectTemplateWizard.dll.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Pour obtenir le jeton de clé publique de l’assembly de l’Assistant

1. Dans le **menu Démarrer**, choisissez **tous les programmes**, **Microsoft Visual Studio**, choisissez **Visual Studio Tools**, puis **invite de commandes développeur**.

     Une fenêtre d’invite de commandes Visual Studio s’ouvre.

2. Exécutez la commande suivante, en remplaçant *PathToWizardAssembly* par le chemin d’accès complet de l’assembly ProjectTemplateWizard.dll généré pour le projet ProjectTemplateWizard sur votre ordinateur de développement :

    ```cmd
    sn.exe -T PathToWizardAssembly
    ```

     Le jeton de clé publique de l’assembly ProjectTemplateWizard.dll est écrit dans la fenêtre d’invite de commandes de Visual Studio.

3. Laissez la fenêtre d’invite de commandes de Visual Studio ouverte. Vous aurez besoin du jeton de clé publique au cours de la procédure suivante.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Pour ajouter une référence à l’assembly de l’Assistant dans le fichier. vstemplate

1. Dans **Explorateur de solutions**, développez le nœud de projet **SiteColumnProjectTemplate** et ouvrez le fichier SiteColumnProjectTemplate. vstemplate.

2. Près de la fin du fichier, ajoutez l' `WizardExtension` élément suivant entre les `</TemplateContent>` `</VSTemplate>` balises et. Remplacez la valeur de *votre jeton* de l' `PublicKeyToken` attribut par le jeton de clé publique que vous avez obtenu dans la procédure précédente.

    ```xml
    <WizardExtension>
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>
    </WizardExtension>
    ```

     Pour plus d’informations sur l' `WizardExtension` élément, consultez l' [élément WizardExtension &#40;les modèles Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Enregistrez et fermez le fichier.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Ajouter des paramètres remplaçables au fichier Elements.xml dans le modèle de projet
 Ajoutez plusieurs paramètres remplaçables au fichier *Elements.xml* dans le projet SiteColumnProjectTemplate. Ces paramètres sont initialisés dans la `RunStarted` méthode de la `SiteColumnProjectWizard` classe que vous avez définie précédemment. Quand un utilisateur crée un projet de colonne de site, Visual Studio remplace automatiquement ces paramètres dans le fichier *Elements.xml* dans le nouveau projet par les valeurs qu’ils ont spécifiées dans l’Assistant.

 Un paramètre remplaçable est un jeton qui commence et se termine par le caractère dollar ($). En plus de définir vos propres paramètres remplaçables, vous pouvez utiliser des paramètres prédéfinis qui sont définis et initialisés par le système de projet SharePoint. Pour plus d’informations, consultez [paramètres remplaçables](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Pour ajouter des paramètres remplaçables au fichier Elements.xml

1. Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier *Elements.xml* par le code XML suivant.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <Field ID="{$guid5$}"
             Name="$fieldname$"
             DisplayName="$fieldname$"
             Type="$selectedfieldtype$"
             Group="$selectedgrouptype$">
      </Field>
    </Elements>
    ```

     Le nouveau code XML modifie les valeurs des `Name` `DisplayName` attributs,, `Type` et `Group` en paramètres remplaçables personnalisés.

2. Enregistrez et fermez le fichier.

## <a name="add-the-wizard-to-the-vsix-package"></a>Ajouter l’Assistant au package VSIX
 Pour déployer l’Assistant avec le package VSIX qui contient le modèle de projet colonne de site, ajoutez des références au projet d’Assistant et au projet de commandes SharePoint dans le fichier source. extension. vsixmanifest du projet VSIX.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Pour ajouter l’Assistant au package VSIX

1. Dans **Explorateur de solutions**, dans le projet **SiteColumnProjectItem** , ouvrez le menu contextuel du fichier **source. extension. vsixmanifest** , puis choisissez **ouvrir**.

     Visual Studio ouvre le fichier dans l’éditeur de manifeste.

2. Sous l’onglet **ressources** de l’éditeur, choisissez le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’ouvre.

3. Dans la liste **type** , choisissez **Microsoft. VisualStudio. assembly**.

4. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

5. Dans la liste **projet** , choisissez **ProjectTemplateWizard**, puis cliquez sur le bouton **OK** .

6. Sous l’onglet **composants** de l’éditeur, cliquez à nouveau sur le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’ouvre.

7. Dans la liste **type** , entrez **SharePoint. Commands. v4**.

8. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

9. Dans la liste **projet** , choisissez le projet **SharePointCommands** , puis choisissez le bouton **OK** .

10. Dans la barre de menus, choisissez **générer**  >  **générer la solution**, puis vérifiez que la solution se génère sans erreur.

## <a name="test-the-wizard"></a>Tester l’Assistant
 Vous êtes maintenant prêt à tester l’Assistant. Tout d’abord, commencez à déboguer la solution SiteColumnProjectItem dans l’instance expérimentale de Visual Studio. Ensuite, testez l’Assistant pour le projet de colonne de site dans l’instance expérimentale de Visual Studio. Enfin, générez et exécutez le projet pour vérifier que la colonne de site fonctionne comme prévu.

#### <a name="to-start-debugging-the-solution"></a>Pour démarrer le débogage de la solution

1. Redémarrez Visual Studio avec les informations d’identification d’administration, puis ouvrez la solution SiteColumnProjectItem.

2. Dans le projet ProjectTemplateWizard, ouvrez le fichier de code SiteColumnProjectWizard, puis ajoutez un point d’arrêt à la première ligne de code dans la `RunStarted` méthode.

3. Dans la barre de menus, choisissez **Déboguer**les  >  **exceptions**.

4. Dans la boîte de dialogue **exceptions** , assurez-vous que les cases à cocher **levé** et **non géré** par l’utilisateur pour les **exceptions du Common Language Runtime** sont désactivées, puis choisissez le bouton **OK** .

5. Démarrez le débogage en choisissant la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**  >  **Démarrer le débogage**.

     Visual Studio installe l’extension sur%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Pour tester l’Assistant dans Visual Studio

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

2. Développez le nœud **Visual C#** ou le nœud **Visual Basic** (selon la langue prise en charge par votre modèle de projet), développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

3. Dans la liste des modèles de projet, choisissez **colonne de site**, nommez le projet **SiteColumnWizardTest**, puis choisissez le bouton **OK** .

4. Vérifiez que le code de l’autre instance de Visual Studio s’arrête sur le point d’arrêt que vous avez défini précédemment dans la `RunStarted` méthode.

5. Continuez à déboguer le projet en choisissant la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**  >  **Continuer**.

6. Dans l' **Assistant Personnalisation de SharePoint**, entrez l’URL du site que vous souhaitez utiliser pour le débogage, puis choisissez le bouton **suivant** .

7. Dans la deuxième page de l' **Assistant Personnalisation de SharePoint**, effectuez les sélections suivantes :

   - Dans la liste **type** , choisissez **booléen**.

   - Dans la liste **groupe** , choisissez **colonnes oui/non personnalisées**.

   - Dans la zone **nom** , entrez **ma colonne oui/non**, puis choisissez le bouton **Terminer** .

     Dans **Explorateur de solutions**, un nouveau projet s’affiche et contient un élément de projet nommé **champ1**, et Visual Studio ouvre le fichier *Elements.xml* du projet dans l’éditeur.

8. Vérifiez que *Elements.xml* contient les valeurs que vous avez spécifiées dans l’Assistant.

#### <a name="to-test-the-site-column-in-sharepoint"></a>Pour tester la colonne de site dans SharePoint

1. Dans l’instance expérimentale de Visual Studio, choisissez la touche **F5** .

     La colonne de site est empaquetée et déployée sur le site SharePoint que spécifie la propriété **URL du site** du projet. Le navigateur Web s’ouvre sur la page par défaut de ce site.

    > [!NOTE]
    > Si la boîte de dialogue **débogage de script désactivé** s’affiche, choisissez le bouton **Oui** pour continuer à déboguer le projet.

2. Dans le menu **actions du site** , choisissez Paramètres du **site**.

3. Sur la page Paramètres du site, sous **galeries**, choisissez le lien **colonnes de site** .

4. Dans la liste des colonnes de site, vérifiez qu’un groupe de **colonnes oui/non personnalisé** contient une colonne nommée **ma colonne oui/non**, puis fermez le navigateur Web.

## <a name="clean-up-the-development-computer"></a>Nettoyer l’ordinateur de développement
 Une fois que vous avez fini de tester l’élément de projet, supprimez le modèle de projet de l’instance expérimentale de Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Pour nettoyer l’ordinateur de développement

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **Outils**  >  **extensions et mises à jour**.

     La boîte de dialogue **Extensions et mises à jour** s’ouvre.

2. Dans la liste des extensions, choisissez **colonne de site**, puis cliquez sur le bouton **désinstaller** .

3. Dans la boîte de dialogue qui s’affiche, choisissez le bouton **Oui** pour confirmer que vous souhaitez désinstaller l’extension, puis cliquez sur le bouton **redémarrer maintenant** pour terminer la désinstallation.

4. Fermez l’instance expérimentale de Visual Studio et l’instance dans laquelle la solution CustomActionProjectItem est ouverte.

     Pour plus d’informations sur le déploiement des [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Extensions, consultez [expédition d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : création d’un élément de projet colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Définir des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Création de modèles d'élément et de modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Comment : utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)
