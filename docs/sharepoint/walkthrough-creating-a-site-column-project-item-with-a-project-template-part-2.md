---
title: 'Procédure pas à pas : Création d’un élément de projet de colonne de Site avec un modèle de projet, partie 2 | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], creating template wizards
- SharePoint project items, creating template wizards
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d4512dc15d394cdf2442d8bfcf440ccb31623a29
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942073"
---
# <a name="walkthrough-create-a-site-column-project-item-with-a-project-template-part-2"></a>Procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 2
  Une fois que vous définissez un type d’élément de projet SharePoint personnalisé et l’associez à un modèle de projet dans Visual Studio, vous souhaiterez également fournir un Assistant pour le modèle. Vous pouvez utiliser l’Assistant pour collecter des informations auprès des utilisateurs lorsqu’ils utilisent votre modèle pour créer un projet qui contient l’élément de projet. Les informations que vous recueillez peuvent être utilisées pour initialiser l’élément de projet.  
  
 Dans cette procédure pas à pas, vous allez ajouter un Assistant pour le modèle de projet colonne de Site qui est illustré dans [procédure pas à pas : création d’un élément de projet colonne de Site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md). Lorsqu’un utilisateur crée un projet colonne de Site, l’Assistant recueille des informations sur la colonne de site (par exemple, son type de base et le groupe) et ajoute ces informations pour le *Elements.xml* fichier dans le nouveau projet.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un Assistant pour un type d’élément de projet SharePoint personnalisé associé à un modèle de projet.  
  
-   Définition d’un Assistant personnalisé l’interface utilisateur semblable aux Assistants intégrés pour les projets SharePoint dans Visual Studio.  
  
-   Création de deux *commandes SharePoint* qui sont utilisés pour appeler le site SharePoint local pendant l’exécution de l’Assistant. Les commandes SharePoint sont des méthodes qui peuvent être utilisées par les extensions de Visual Studio pour appeler des API dans le modèle d’objet serveur SharePoint. Pour plus d’informations, consultez [appel des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   À l’aide des paramètres remplaçables pour initialiser les fichiers de projet SharePoint avec les données que vous collectez dans l’Assistant.  
  
-   Création d’un fichier .snk dans chaque nouvelle instance de projet colonne de Site. Ce fichier est utilisé pour signer le projet afin que l’assembly de solution SharePoint peut être déployé dans le global assembly cache de sortie.  
  
-   Débogage et test de l’Assistant.  
  
> [!NOTE]  
> Pour une série d’exemples de workflows, consultez [exemples de flux de travail SharePoint](https://docs.microsoft.com/sharepoint/dev/general-development/sharepoint-workflow-samples).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure pas à pas, vous devez d’abord créer la solution SiteColumnProjectItem en effectuant [procédure pas à pas : création d’un élément de projet colonne de Site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Vous devez également les composants suivants sur l’ordinateur de développement pour effectuer cette procédure pas à pas :  
  
- Éditions prises en charge de Windows, SharePoint et Visual Studio.
  
- Le Kit de développement logiciel avec Visual Studio. Cette procédure pas à pas utilise le **projet VSIX** modèle dans le Kit de développement logiciel pour créer un package VSIX pour déployer l’élément de projet. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Connaissance des concepts suivants est utile, mais pas obligatoire, pour suivre la procédure pas à pas :  
  
- Assistants pour les modèles de projet et d’élément dans Visual Studio. Pour plus d’informations, consultez [Comment : utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md) et <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.  
  
- Colonnes de site dans SharePoint. Pour plus d’informations, consultez [colonnes](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
## <a name="understand-the-wizard-components"></a>Comprendre les composants de l’Assistant
 L’Assistant qui est illustré dans cette procédure pas à pas contient plusieurs composants. Le tableau suivant décrit ces composants.  
  
|Composant|Description|  
|---------------|-----------------|  
|Implémentation de l’Assistant|Il s’agit d’une classe nommée `SiteColumnProjectWizard`, qui implémente le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface. Cette interface définit les méthodes appelées par Visual Studio lorsque l’Assistant démarre et se termine et à certains moments lors de l’Assistant s’exécute.|  
|Interface de l’Assistant|Il s’agit d’une fenêtre WPF, nommée `WizardWindow`. Cette fenêtre inclut deux contrôles utilisateur, nommés `Page1` et `Page2`. Ces contrôles utilisateur représentent les deux pages de l’Assistant.<br /><br /> Dans cette procédure pas à pas, le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> méthode de l’implémentation de l’Assistant affiche l’interface utilisateur de l’Assistant.|  
|Modèle de données d’Assistant|Il s’agit d’une classe intermédiaire nommée `SiteColumnWizardModel`, qui fournit une couche entre l’interface utilisateur de l’Assistant et l’implémentation de l’Assistant. Cet exemple utilise cette classe pour vous aider à abstraire l’implémentation de l’Assistant et l’interface utilisateur de l’Assistant à partir d’autres ; Cette classe n’est pas un composant obligatoire de tous les Assistants.<br /><br /> Dans cette procédure pas à pas, l’implémentation de l’Assistant passe un `SiteColumnWizardModel` objet à la fenêtre de l’Assistant lorsqu’il affiche l’interface utilisateur de l’Assistant. L’interface utilisateur de l’Assistant utilise des méthodes de cet objet pour enregistrer les valeurs des contrôles dans l’interface utilisateur et pour effectuer des tâches telles que la vérification que l’URL du site d’entrée est valide. Une fois que l’utilisateur termine l’Assistant, l’implémentation de l’Assistant utilise le `SiteColumnWizardModel` objet afin de déterminer l’état final de l’interface utilisateur.|  
|Gestionnaire de signature de projet|Il s’agit d’une classe d’assistance nommée `ProjectSigningManager`, qui est utilisé par l’implémentation de l’Assistant pour créer un nouveau fichier key.snk dans chaque nouvelle instance de projet.|  
|commandes SharePoint|Il s’agit de méthodes qui sont utilisées par le modèle de données d’Assistant à appeler dans le site SharePoint local pendant l’exécution de l’Assistant. Étant donné que les commandes SharePoint doivent cibler le .NET Framework 3.5, ces commandes sont implémentées dans un assembly différent du reste de l’Assistant de code.|  
  
## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez ajouter plusieurs projets à la solution SiteColumnProjectItem que vous avez créé dans [procédure pas à pas : créer un élément de projet de colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md):  
  
- Un projet WPF. Vous allez implémenter le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> d’interface et de définir l’interface utilisateur de l’Assistant dans ce projet.  
  
- Un projet de bibliothèque de classes qui définit les commandes SharePoint. Ce projet doit cibler.NET Framework 3.5.  
  
  Démarrer la procédure pas à pas en créant les projets.  
  
#### <a name="to-create-the-wpf-project"></a>Pour créer le projet WPF
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez la solution SiteColumnProjectItem.  
  
2.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SiteColumnProjectItem** nœud de la solution, choisissez **ajouter**, puis choisissez **denouveauprojet**.  
  
3.  En haut de la **ajouter un nouveau projet** boîte de dialogue zone, assurez-vous que l’option **.NET Framework 4.5** est choisi dans la liste des versions du .NET Framework.  
  
4.  Développez le **Visual C#** nœud ou le **Visual Basic** nœud, puis choisissez le **Windows** nœud.  
  
5.  Dans la liste des modèles de projet, choisissez **bibliothèque de contrôles utilisateur WPF**, nommez le projet **ProjectTemplateWizard**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **ProjectTemplateWizard** projet à la solution et ouvre le fichier UserControl1.xaml par défaut.  
  
6.  Supprimer le fichier UserControl1.xaml du projet.  
  
#### <a name="to-create-the-sharepoint-commands-project"></a>Pour créer le projet de commandes SharePoint  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud de solution SiteColumnProjectItem, choisissez **ajouter**, puis choisissez **nouveau projet**.  
  
2.  En haut de la **ajouter un nouveau projet** boîte de dialogue, sélectionnez **.NET Framework 3.5** dans la liste des versions du .NET Framework.  
  
3.  Développez le **Visual C#** nœud ou le **Visual Basic** nœud, puis choisissez le **Windows** nœud.  
  
4.  Choisissez le **bibliothèque de classes** modèle de projet, nommez le projet **SharePointCommands**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **SharePointCommands** projet à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprimer le fichier de code Class1 du projet.  
  
## <a name="configure-the-projects"></a>Configurer les projets
 Avant de créer l’Assistant, vous devez ajouter certains fichiers de code et les références d’assembly pour les projets.  
  
#### <a name="to-configure-the-wizard-project"></a>Pour configurer le projet d’Assistant  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ProjectTemplateWizard** nœud de projet, puis choisissez **propriétés**.  
  
2.  Dans le **Concepteur de projets**, choisissez le **Application** onglet pour un projet Visual c# ou le **compiler** onglet pour un projet Visual Basic.  
  
3.  Assurez-vous que le framework cible est défini sur le .NET Framework 4.5, pas le .NET Framework 4.5 Client Profile.  
  
     Pour plus d’informations, consultez [Guide pratique pour cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
4.  Ouvrez le menu contextuel pour le **ProjectTemplateWizard** de projet, choisissez **ajouter**, puis choisissez **un nouvel élément**.  
  
5.  Choisissez le **fenêtre (WPF)** item, nommez l’élément **WizardWindow**, puis choisissez le **ajouter** bouton.  
  
6.  Ajoutez deux **contrôle utilisateur (WPF)** éléments au projet, puis nommez-les **Page1** et **Page2**.  
  
7.  Ajoutez quatre fichiers de code au projet et leur donner les noms suivants :  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   ID de commande  
  
8.  Ouvrez le menu contextuel pour le **ProjectTemplateWizard** nœud de projet, puis choisissez **ajouter une référence**.  
  
9. Développez le **assemblys** nœud, choisissez le **Extensions** nœud et sélectionnez les cases à cocher en regard des assemblys suivants :  
  
    -   EnvDTE  
  
    -   Assemblys Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. Choisissez le **OK** pour ajouter les assemblys au projet.  
  
11. Dans **l’Explorateur de solutions**, sous le **références** dossier pour le **ProjectTemplateWizard** de projet, choisissez **EnvDTE**.  
  
12. Dans le **propriétés** fenêtre, modifiez la valeur de la **incorporer les Types Interop** propriété **False**.  
  
13. Si vous développez un projet Visual Basic, importez l’espace de noms ProjectTemplateWizard dans votre projet à l’aide de la **Concepteur de projet**.  
  
     Pour plus d’informations, consultez [Comment : ajouter ou supprimer des espaces de noms importés &#40;Visual Basic&#41;](../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Pour configurer le projet SharePointcommands
  
1.  Dans **l’Explorateur de solutions**, choisissez le **SharePointCommands** nœud du projet.  
  
2.  Dans la barre de menus, choisissez **projet**, **ajouter un élément existant**.  
  
3.  Dans le **ajouter un élément existant** boîte de dialogue, accédez au dossier qui contient les fichiers de code pour le projet ProjectTemplateWizard, puis choisissez le **ID de commande** fichier de code.  
  
4.  Cliquez sur la flèche à côté du **ajouter** bouton, puis choisissez le **ajouter en tant que lien** option dans le menu qui s’affiche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le fichier de code pour le **SharePointCommands** projet sous forme de lien. Le fichier de code se trouve dans le **ProjectTemplateWizard** projet, mais le code dans le fichier est également compilé dans le **SharePointCommands** projet.  
  
5.  Dans le **SharePointCommands** de projet, ajoutez un autre fichier de code qui est nommé de commandes.  
  
6.  Choisissez le projet SharePointCommands, puis, dans la barre de menus, **projet** > **ajouter une référence**.  
  
7.  Développez le **assemblys** nœud, choisissez le **Extensions** nœud et sélectionnez les cases à cocher en regard des assemblys suivants :  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  Choisissez le **OK** pour ajouter les assemblys au projet.  
  
## <a name="create-the-wizard-model-signing-manager-and-sharepoint-command-ids"></a>Créer le modèle d’Assistant, un gestionnaire de signature et un ID de commande SharePoint
 Ajoutez le code au projet ProjectTemplateWizard pour implémenter les composants suivants dans l’exemple :  
  
- Les ID de commande SharePoint. Ces chaînes identifient les commandes SharePoint qui utilise l’Assistant. Plus loin dans cette procédure pas à pas, vous ajouterez du code au projet SharePointCommands pour implémenter les commandes.  
  
- Le modèle de données d’Assistant.  
  
- Le Gestionnaire de signature du projet.  
  
  Pour plus d’informations sur ces composants, consultez [présentation des composants de l’Assistant](#wizardcomponents).  
  
#### <a name="to-define-the-sharepoint-command-ids"></a>Pour définir les ID de commande SharePoint
  
1.  Dans le projet ProjectTemplateWizard, ouvrez le fichier de code d’ID de commande, puis remplacez tout le contenu de ce fichier par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/commandids.vb#5)]  
  
#### <a name="to-create-the-wizard-model"></a>Pour créer le modèle d’Assistant  
  
1.  Ouvrez le fichier de code SiteColumnWizardModel et remplacez tout le contenu de ce fichier par le code suivant.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]  
  
#### <a name="to-create-the-project-signing-manager"></a>Pour créer le Gestionnaire de signature du projet  
  
1.  Ouvrez le fichier de code ProjectSigningManager et remplacez tout le contenu de ce fichier par le code suivant.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.vb#8)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/projectsigningmanager.cs#8)]  
  
## <a name="create-the-wizard-ui"></a>Créer l’interface utilisateur de l’Assistant
 Ajoutez le XAML pour définir l’interface utilisateur de la fenêtre de l’Assistant et les deux contrôles utilisateur qui fournissent l’interface utilisateur pour les pages d’Assistant et ajouter du code pour définir le comportement des fenêtre et contrôles utilisateur. L’Assistant que vous créez est similaire à l’Assistant intégré pour les projets SharePoint dans Visual Studio.  
  
> [!NOTE]  
>  Dans les étapes suivantes, votre projet aura des erreurs de compilation après avoir ajouté le code ou XAML à votre projet. Ces erreurs disparaissent lorsque vous ajoutez du code dans les étapes ultérieures.  
  
#### <a name="to-create-the-wizard-window-ui"></a>Pour créer la fenêtre de l’Assistant d’interface utilisateur
  
1.  Dans le projet ProjectTemplateWizard, ouvrez le menu contextuel pour le fichier WizardWindow.xaml, puis choisissez **ouvrir** pour ouvrir la fenêtre dans le concepteur.  
  
2.  Dans la vue XAML du concepteur, remplacez le XAML actuel par le XAML suivant. Le XAML définit une interface utilisateur qui comprend un titre, un <xref:System.Windows.Controls.Grid> qui contient les pages d’Assistant et boutons de navigation en bas de la fenêtre.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  La fenêtre qui est créée dans ce XAML est dérivée de la <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe de base. Lorsque vous ajoutez une boîte de dialogue WPF personnalisée à Visual Studio, nous vous recommandons de dériver votre boîte de dialogue à partir de cette classe pour que la cohérence du style avec d’autres boîtes de dialogue Visual Studio et éviter les problèmes de la boîte de dialogue modale qui pourraient se produire. Pour plus d’informations, consultez [création et la gestion des boîtes de dialogue modales](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Si vous développez un projet Visual Basic, supprimez le `ProjectTemplateWizard` espace de noms à partir de la `WizardWindow` nom de classe dans le `x:Class` attribut de la `Window` élément. Cet élément est dans la première ligne de le XAML. Lorsque vous avez terminé, la première ligne doit ressembler à l’exemple suivant.  
  
    ```xml  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Ouvrez le fichier code-behind pour le fichier WizardWindow.xaml.  
  
5.  Remplacez le contenu de ce fichier, à l’exception de la `using` déclarations en haut du fichier, avec le code suivant.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.vb#4)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/wizardwindow.xaml.cs#4)]  
  
#### <a name="to-create-the-first-wizard-page-ui"></a>Pour créer la première page de l’Assistant
  
1.  Dans le projet ProjectTemplateWizard, ouvrez le menu contextuel pour le fichier Page1.xaml, puis choisissez **ouvrir** pour ouvrir le contrôle utilisateur dans le concepteur.  
  
2.  Dans la vue XAML du concepteur, remplacez le XAML actuel par le XAML suivant. Le XAML définit une interface utilisateur qui comprend une zone de texte où les utilisateurs peuvent entrer l’URL des sites locaux qu’ils souhaitent utiliser pour le débogage. L’interface utilisateur inclut également des cases d’option avec laquelle les utilisateurs peuvent spécifier si le projet est sandbox.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page1.xaml#11)]  
  
3.  Si vous développez un projet Visual Basic, supprimez le `ProjectTemplateWizard` espace de noms à partir de la `Page1` nom de classe dans le `x:Class` attribut de la `UserControl` élément. Il s’agit de la première ligne de le XAML. Lorsque vous avez terminé, la première ligne doit ressembler à ce qui suit.  
  
    ```xml  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Remplacez le contenu du fichier Page1.xaml, à l’exception de la `using` déclarations en haut du fichier, avec le code suivant.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page1.xaml.cs#2)]  
  
#### <a name="to-create-the-second-wizard-page-ui"></a>Pour créer la deuxième page de l’Assistant
  
1.  Dans le projet ProjectTemplateWizard, ouvrez le menu contextuel pour le fichier Page2.xaml, puis choisissez **ouvrir**.  
  
     Le contrôle utilisateur s'ouvre dans le concepteur.  
  
2.  Dans la vue XAML, remplacez le XAML actuel par le XAML suivant. Le XAML définit une interface utilisateur qui inclut une liste déroulante pour choisir le type de base de la colonne de site, une zone de liste déroulante pour spécifier un groupe intégré ou personnalisé sous lequel vous voulez afficher la colonne de site dans la galerie et une zone de texte pour spécifier le nom de la colonne de site.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../sharepoint/codesnippet/Xaml/sitecolumnprojectitem/projecttemplatewizard/page2.xaml#12)]  
  
3.  Si vous développez un projet Visual Basic, supprimez le `ProjectTemplateWizard` espace de noms à partir de la `Page2` nom de classe dans le `x:Class` attribut de la `UserControl` élément. Il s’agit de la première ligne de le XAML. Lorsque vous avez terminé, la première ligne doit ressembler à ce qui suit.  
  
    ```xml  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Remplacez le contenu du fichier code-behind pour le fichier Page2.xaml, à l’exception de la `using` déclarations en haut du fichier, avec le code suivant.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.vb#3)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/page2.xaml.cs#3)]  
  
## <a name="implement-the-wizard"></a>Implémenter l’Assistant
 Définir la fonctionnalité principale de l’Assistant en implémentant le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface. Cette interface définit les méthodes appelées par Visual Studio lorsque l’Assistant démarre et se termine et à certains moments lors de l’Assistant s’exécute.  
  
#### <a name="to-implement-the-wizard"></a>Pour implémenter l’Assistant  
  
1.  Dans le projet ProjectTemplateWizard, ouvrez le fichier de code SiteColumnProjectWizard.  
  
2.  Remplacez tout le contenu de ce fichier par le code suivant.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]  
  
## <a name="create-the-sharepoint-commands"></a>Créer des commandes SharePoint
 Créez deux commandes personnalisées qui appellent le modèle d’objet de serveur SharePoint. Une seule commande détermine si l’URL du site que l’utilisateur tape dans l’Assistant est valide. L’autre commande Obtient tous les types de champs à partir du site SharePoint spécifié afin que les utilisateurs peuvent sélectionner celui que vous souhaitez utiliser comme base pour leur nouvelle colonne de site.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Pour définir les commandes SharePoint  
  
1.  Dans le **SharePointCommands** de projet, ouvrez le fichier de code de commandes.  
  
2.  Remplacez tout le contenu de ce fichier par le code suivant.  
  
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/VisualBasic/sitecolumnprojectitem/sharepointcommands/commands.vb#9)]
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../sharepoint/codesnippet/CSharp/sitecolumnprojectitem/sharepointcommands/commands.cs#9)]  
  
## <a name="checkpoint"></a>Point de contrôle  
 À ce stade dans la procédure pas à pas, l’intégralité du code pour l’Assistant est désormais dans le projet. Générez le projet pour vous assurer qu’il est compilé sans erreur.  
  
#### <a name="to-build-your-project"></a>Pour générer votre projet  
  
1.  Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.  
  
## <a name="removing-the-keysnk-file-from-the-project-template"></a>Suppression du fichier key.snk à partir du modèle de projet
 Dans [procédure pas à pas : créer un élément de projet de colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), le modèle de projet que vous avez créé contient un fichier key.snk qui est utilisé pour signer chaque instance de projet colonne de Site. Ce fichier key.snk n’est plus nécessaire, car l’Assistant génère désormais un nouveau fichier key.snk pour chaque projet. Supprimer le fichier key.snk du modèle de projet et supprimer des références à ce fichier.  
  
#### <a name="to-remove-the-keysnk-file-from-the-project-template"></a>Pour supprimer le fichier key.snk du modèle de projet  
  
1.  Dans **l’Explorateur de solutions**, sous le **SiteColumnProjectTemplate** nœud, ouvrez le menu contextuel pour le **key.snk** de fichiers, puis choisissez **supprimer**.  
  
2.  Dans la boîte de dialogue de confirmation qui s’affiche, choisissez le **OK** bouton.  
  
3.  Sous le **SiteColumnProjectTemplate** nœud, ouvrez le fichier SiteColumnProjectTemplate.vstemplate, puis supprimez l’élément suivant à partir de celui-ci.  
  
    ```xml  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  Enregistrez et fermez le fichier.  
  
5.  Sous le **SiteColumnProjectTemplate** nœud, ouvrez le fichier ProjectTemplate.csproj ou ProjectTemplate.vbproj et supprimez les éléments suivants `PropertyGroup` élément à partir de celui-ci.  
  
    ```xml  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ``` 
  
6.  Supprimer les éléments suivants `None` élément.  
  
    ```xml  
    <None Include="key.snk" />  
    ```  
  
7.  Enregistrez et fermez le fichier.  
  
## <a name="associating-the-wizard-with-the-project-template"></a>Association de l’Assistant avec le modèle de projet
 Maintenant que vous avez implémenté l’Assistant, vous devez associer l’Assistant avec les **colonne de Site** modèle de projet. Il existe trois procédures, que vous devez effectuer pour ce faire :  
  
1.  Signer l’assembly de l’Assistant avec un nom fort.  
  
2.  Obtenir la clé publique jeton pour l’assembly de l’Assistant.  
  
3.  Ajoutez une référence à l’assembly de l’Assistant dans le fichier .vstemplate pour le **colonne de Site** modèle de projet.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Pour signer l’assembly de l’Assistant avec un nom fort  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ProjectTemplateWizard** de projet, puis choisissez **propriétés**.  
  
2.  Sur le **signature** onglet, sélectionnez le **signer l’assembly** case à cocher.  
  
3.  Dans le **choisir un fichier de clé de nom fort** , choisissez  **\<nouveau... >**.  
  
4.  Dans le **créer une clé de nom fort** boîte de dialogue, entrez un nom pour le nouveau fichier de clé, désactivez le **protéger mon fichier de clé avec un mot de passe** case à cocher, puis choisissez le **OK** bouton.  
  
5.  Ouvrez le menu contextuel pour le **ProjectTemplateWizard** de projet, puis choisissez **Build** pour créer le fichier ProjectTemplateWizard.dll.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Pour obtenir un jeton la clé publique pour l’assembly de l’Assistant  
  
1.  Sur le **Menu Démarrer**, choisissez **tous les programmes**, choisissez **Microsoft Visual Studio**, choisissez **Visual Studio Tools**, puis choisissez  **Invite de commandes développeur**.  
  
     Une fenêtre d’invite de commandes Visual Studio s’ouvre.  
  
2.  Exécutez la commande suivante, en remplaçant *PathToWizardAssembly* avec le chemin d’accès complet à l’assembly ProjectTemplateWizard.dll créé pour le projet ProjectTemplateWizard sur votre ordinateur de développement :  
  
    ```cmd  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Le jeton de clé publique pour l’assembly ProjectTemplateWizard.dll est écrit dans la fenêtre d’invite de commandes Visual Studio.  
  
3.  Ne fermez pas la fenêtre d’invite de commandes Visual Studio. Vous aurez besoin du jeton de clé publique durant la procédure suivante.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Pour ajouter une référence à l’assembly de l’Assistant dans le fichier .vstemplate  
  
1.  Dans **l’Explorateur de solutions**, développez le **SiteColumnProjectTemplate** nœud de projet et ouvrez le fichier SiteColumnProjectTemplate.vstemplate.  
  
2.  Vers la fin du fichier, ajoutez le code suivant `WizardExtension` élément entre les `</TemplateContent>` et `</VSTemplate>` balises. Remplacez le *votre jeton* valeur de la `PublicKeyToken` attribut avec le jeton de clé publique que vous avez obtenue dans la procédure précédente.  
  
    ```xml  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Pour plus d’informations sur la `WizardExtension` élément, consultez [WizardExtension élément &#40;modèles Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Enregistrez et fermez le fichier.  
  
## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-project-template"></a>Ajouter des paramètres remplaçables au fichier Elements.xml dans le modèle de projet
 Ajoutez plusieurs paramètres remplaçables pour la *Elements.xml* fichier dans le projet SiteColumnProjectTemplate. Ces paramètres sont initialisés dans le `RunStarted` méthode dans la `SiteColumnProjectWizard` classe que vous avez défini précédemment. Lorsqu’un utilisateur crée un projet colonne de Site, Visual Studio remplace automatiquement ces paramètres dans le *Elements.xml* fichier dans le nouveau projet avec les valeurs qui ont été spécifiées dans l’Assistant.  
  
 Un paramètre remplaçable est un jeton qui commence et se termine par le caractère de signe dollar ($). En plus de définir vos propres paramètres remplaçables, vous pouvez utiliser des paramètres intégrés qui sont définis et initialisés par le système de projet SharePoint. Pour plus d’informations, consultez [paramètres remplaçables](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Pour ajouter des paramètres remplaçables au fichier Elements.xml
  
1.  Dans le projet SiteColumnProjectTemplate, remplacez le contenu de la *Elements.xml* fichier avec le code XML suivant.  
  
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
  
     Le nouveau code XML modifie les valeurs de la `Name`, `DisplayName`, `Type`, et `Group` attributs aux paramètres remplaçables.  
  
2.  Enregistrez et fermez le fichier.  
  
## <a name="add-the-wizard-to-the-vsix-package"></a>Ajoutez l’Assistant au package VSIX
 Pour déployer l’Assistant avec le package VSIX qui contient le modèle de projet colonne de Site, ajoutez des références au projet d’Assistant et le projet de commandes SharePoint dans le fichier source.extension.vsixmanifest dans le projet VSIX.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Pour ajouter l’Assistant au package VSIX  
  
1.  Dans **l’Explorateur de solutions**, dans le **SiteColumnProjectItem** de projet, ouvrez le menu contextuel pour le **source.extension.vsixmanifest** de fichiers, puis choisissez **Open**.  
  
     Visual Studio ouvre le fichier dans l’éditeur de manifeste.  
  
2.  Sur le **actifs** onglet de l’éditeur, choisissez le **New** bouton.  
  
     Le **ajouter un nouveau composant** boîte de dialogue s’ouvre.  
  
3.  Dans le **Type** , choisissez **Microsoft.VisualStudio.Assembly**.  
  
4.  Dans le **Source** , choisissez **un projet dans la solution actuelle**.  
  
5.  Dans le **projet** , choisissez **ProjectTemplateWizard**, puis choisissez le **OK** bouton.  
  
6.  Sur le **actifs** onglet de l’éditeur, choisissez le **New** bouton à nouveau.  
  
     Le **ajouter un nouveau composant** boîte de dialogue s’ouvre.  
  
7.  Dans le **Type** liste, entrez **SharePoint.Commands.v4**.  
  
8.  Dans le **Source** , choisissez **un projet dans la solution actuelle**.  
  
9. Dans le **projet** , choisissez le **SharePointCommands** de projet, puis choisissez le **OK** bouton.  
  
10. Dans la barre de menus, choisissez **Build** > **générer la Solution**, puis assurez-vous que la solution se génère sans erreur.  
  
## <a name="test-the-wizard"></a>L’Assistant de test
 Vous êtes maintenant prêt à tester l’Assistant. Tout d’abord, démarrez le débogage de la solution SiteColumnProjectItem dans l’instance expérimentale de Visual Studio. Ensuite, testez l’Assistant pour le projet de la colonne de Site dans l’instance expérimentale de Visual Studio. Enfin, générez et exécutez le projet pour vérifier que la colonne de site fonctionne comme prévu.  
  
#### <a name="to-start-debugging-the-solution"></a>Pour démarrer le débogage de la solution  
  
1.  Redémarrez Visual Studio en tant qu’administrateur et ouvrez la solution SiteColumnProjectItem.  
  
2.  Dans le projet ProjectTemplateWizard, ouvrez le fichier de code SiteColumnProjectWizard, puis ajoutez un point d’arrêt à la première ligne de code dans le `RunStarted` (méthode).  
  
3.  Dans la barre de menus, choisissez **déboguer** > **Exceptions**.  
  
4.  Dans le **Exceptions** boîte de dialogue zone, assurez-vous que le **levé** et **User-unhandled** cases à cocher pour **Exceptions Common Language Runtime**sont effacées, puis choisissez le **OK** bouton.  
  
5.  Démarrer le débogage en choisissant le **F5** clé ou, dans la barre de menus, choisissez **déboguer** > **démarrer le débogage**.  
  
     Visual Studio installe l’extension %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Site Column\1.0 et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Pour tester l’Assistant dans Visual Studio  
  
1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **fichier** > **New** > **projet**.  
  
2. Développez le **Visual C#** nœud ou le **Visual Basic** nœud (selon le langage qui prend en charge de votre modèle de projet), développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
3. Dans la liste des modèles de projet, choisissez **colonne de Site**, nommez le projet **SiteColumnWizardTest**, puis choisissez le **OK** bouton.  
  
4. Vérifiez que le code dans l’autre instance de Visual Studio s’arrête au point d’arrêt que vous avez défini précédemment dans le `RunStarted` (méthode).  
  
5. Continuer à déboguer le projet en choisissant le **F5** clé ou, dans la barre de menus, choisissez **déboguer** > **continuer**.  
  
6. Dans le **Assistant Personnalisation de SharePoint**, entrez l’URL du site que vous souhaitez utiliser pour le débogage, puis choisissez le **suivant** bouton.  
  
7. Dans la deuxième page de la **Assistant Personnalisation de SharePoint**, effectuez les sélections suivantes :  
  
   - Dans le **Type** , choisissez **booléenne**.  
  
   - Dans le **groupe** , choisissez **personnalisé Oui/non colonnes**.  
  
   - Dans le **nom** , entrez **ma colonne Oui/non**, puis choisissez le **Terminer** bouton.  
  
     Dans **l’Explorateur de solutions**, un nouveau projet s’affiche et contient un élément de projet nommé **Field1**, et Visual Studio ouvre le projet *Elements.xml* fichier dans l’éditeur.  
  
8. Vérifiez que *Elements.xml* contient les valeurs que vous avez spécifié dans l’Assistant.  
  
#### <a name="to-test-the-site-column-in-sharepoint"></a>Pour tester la colonne de site dans SharePoint  
  
1.  Dans l’instance expérimentale de Visual Studio, choisissez le **F5** clé.  
  
     La colonne de site est empaquetée et déployée vers SharePoint site qui le **URL du Site** spécifie la propriété du projet. Le navigateur web s’ouvre à la page par défaut de ce site.  
  
    > [!NOTE]  
    >  Si le **le débogage de Script est désactivé** boîte de dialogue s’affiche, choisissez le **Oui** pour continuer à déboguer le projet.  
  
2.  Sur le **Actions du Site** menu, choisissez **paramètres du Site**.  
  
3.  Dans la page Paramètres du Site, sous **galeries**, choisissez le **colonnes de Site** lien.  
  
4.  Dans la liste des colonnes de site, vérifiez qu’un **personnalisé Oui/non colonnes** groupe contient une colonne nommée **ma colonne Oui/non**, puis fermez le navigateur web.  
  
## <a name="clean-up-the-development-computer"></a>Nettoyer l’ordinateur de développement
 Une fois que vous avez terminé le test de l’élément de projet, supprimez le modèle de projet à partir de l’instance expérimentale de Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Pour nettoyer l’ordinateur de développement  
  
1.  Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **outils** > **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s’ouvre.  
  
2.  Dans la liste des extensions, choisissez **colonne de Site**, puis choisissez le **désinstallation** bouton.  
  
3.  Dans la boîte de dialogue qui s’affiche, choisissez le **Oui** pour confirmer que vous souhaitez désinstaller l’extension, puis choisissez le **redémarrer maintenant** bouton pour terminer la désinstallation.  
  
4.  Fermez l’instance expérimentale de Visual Studio et l’instance dans laquelle la solution ÉlémentProjetActionPersonnalisée est ouverte.  
  
     Pour plus d’informations sur le déploiement [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extensions, consultez [de livraison des Extensions Visual Studio](/visualstudio/extensibility/shipping-visual-studio-extensions).  
  
## <a name="see-also"></a>Voir aussi
 [Procédure pas à pas : Créer un élément de projet de colonne de site avec un modèle de projet, partie 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Définir les types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Création de modèles d’élément et les modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Référence du schéma de modèle Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Guide pratique pour utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
