---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un &#233;l&#233;ment de projet Colonne de site avec un mod&#232;le de projet, deuxi&#232;me&#160;partie | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éléments de projet (développement SharePoint dans Visual Studio), création d’Assistants Modèle"
  - "éléments de projet SharePoint, création d’Assistants modèle"
  - "développement SharePoint dans Visual Studio, définition de nouveaux types d’éléments de projet"
ms.assetid: da14207d-ac09-41ba-b387-c7f881b2a366
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;un &#233;l&#233;ment de projet Colonne de site avec un mod&#232;le de projet, deuxi&#232;me&#160;partie
  Après avoir défini un type personnalisé d'élément de projet SharePoint et l'avoir associé à un modèle de projet dans Visual Studio, vous pouvez également fournir un Assistant pour le modèle.  Vous pouvez utiliser l'Assistant pour collecter des informations auprès des utilisateurs lorsqu'ils emploient votre modèle pour créer un projet qui contient l'élément de projet.  Les informations que vous collectez peuvent être utilisées pour initialiser l'élément de projet.  
  
 Dans cette procédure pas à pas, vous ajouterez un Assistant au modèle de projet Colonne de site qui est illustré dans [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, première partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  Lorsqu'un utilisateur crée un projet Colonne de site, l'Assistant collecte également des informations sur la colonne de site \(par exemple son type de base et groupe\) et ajoute ces informations dans le fichier Elements.xml du nouveau projet.  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Création d'un Assistant pour un type d'élément de projet SharePoint personnalisé associé à un modèle de projet.  
  
-   Définition d'une interface utilisateur d'Assistant personnalisé semblable aux Assistants intégrés pour les projets SharePoint dans Visual Studio.  
  
-   Création de deux *commandes SharePoint* utilisées pour faire appel à un site SharePoint sur l'ordinateur local pendant l'exécution de l'Assistant.  Les commandes SharePoint sont des méthodes susceptibles d'être utilisées par les extensions Visual Studio en vue d'appeler des API dans le modèle objet serveur SharePoint.  Pour plus d'informations, consultez [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Utilisation de paramètres remplaçables pour initialiser les fichiers de projet SharePoint avec les données que vous collectez dans l'Assistant.  
  
-   Création d'un fichier .snk dans chaque instance du projet Colonne de site.  Ce fichier est utilisé pour signer la sortie de projet afin que l'assembly de la solution SharePoint puisse être déployé dans le GAC \(Global Assembly Cache\).  
  
-   Débogage et test de l'Assistant.  
  
> [!NOTE]  
>  Il vous est possible de télécharger un exemple qui contient les projets terminés, du code et d'autres fichiers pour cette procédure pas à pas depuis l'emplacement suivant :  [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=191369](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez d'abord créer la solution SiteColumnProjectItem en suivant la procédure décrite dans [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, première partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 Vous avez par ailleurs besoin des composants suivants sur l'ordinateur de développement pour exécuter cette procédure pas à pas :  
  
-   Éditions prises en charge de Microsoft Windows, SharePoint et Visual Studio.  Pour plus d'informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Le kit de développement logiciel Visual Studio  Cette procédure pas à pas utilise le modèle **Projet VSIX** du Kit de développement logiciel \(SDK\) pour créer un package VSIX afin de déployer l'élément de projet.  Pour plus d'informations, consultez [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Une connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer cette procédure pas à pas :  
  
-   Assistants associés aux modèles de projet et d'élément dans Visual Studio.  Pour plus d'informations, consultez [Comment : utiliser des Assistants avec des modèles de projet](~/extensibility/how-to-use-wizards-with-project-templates.md) et l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
-   Colonnes de site dans SharePoint.  Pour plus d’informations, consultez [Colonnes](http://go.microsoft.com/fwlink/?LinkId=183547).  
  
##  <a name="wizardcomponents"></a> Présentation des composants de l'Assistant  
 L'Assistant qui est représenté dans cette procédure pas à pas contient plusieurs composants.  Le tableau suivant décrit ces composants.  
  
|Composant|Description|  
|---------------|-----------------|  
|Implémentation de l'Assistant|Il s'agit d'une classe nommée `SiteColumnProjectWizard` qui implémente l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Cette interface définit les méthodes appelées par Visual Studio lorsque l'Assistant démarre et finit et à certains moments pendant l'exécution de l'Assistant.|  
|Interface utilisateur de l'Assistant|Il s'agit d'une fenêtre WPF nommée `WizardWindow`.  Cette fenêtre se compose de deux contrôles utilisateur nommés `Page1` et `Page2`.  Ces contrôles utilisateur représentent les deux pages de l'Assistant.<br /><br /> Dans cette procédure pas à pas, la méthode <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> de l'implémentation de l'Assistant affiche l'interface utilisateur de l'Assistant.|  
|Modèle de données de l'Assistant|Il s'agit d'une classe intermédiaire nommée `SiteColumnWizardModel` qui fournit une couche entre l'interface utilisateur de l'Assistant et l'implémentation de l'Assistant.  Cet exemple utilise cette classe pour rendre abstrait le lien entre l'implémentation de l'Assistant et l'interface utilisateur de l'Assistant ; cette classe n'est pas un composant requis de tous les Assistants.<br /><br /> Dans cette procédure pas à pas, l'implémentation de l'Assistant transmet un objet `SiteColumnWizardModel` dans la fenêtre de l'Assistant lorsque l'interface utilisateur de l'Assistant s'affiche.  L'interface utilisateur de l'Assistant utilise des méthodes de cet objet pour enregistrer les valeurs des contrôles de l'interface utilisateur, et pour effectuer des tâches, notamment vérifier que l'URL d'entrée du site est valide.  Une fois que l'utilisateur a terminé avec l'Assistant, l'implémentation de l'Assistant utilise l'objet `SiteColumnWizardModel` pour déterminer l'état final de l'interface utilisateur.|  
|Gestionnaire de signature des projets|Il s'agit d'une classe d'assistance nommée `ProjectSigningManager` utilisée par l'implémentation de l'Assistant pour créer un fichier key.snk dans chaque nouvelle instance de projet.|  
|Commandes SharePoint|Ce sont des méthodes utilisées par le modèle de données de l'Assistant pour faire appel au site SharePoint local pendant l'exécution de l'Assistant.  Étant donné que les commandes SharePoint doivent cibler le .NET Framework 3.5, ces commandes sont implémentées dans un assembly différent du reste du code de l'Assistant.|  
  
## Création du projet  
 Pour exécuter cette procédure pas à pas, vous devez ajouter plusieurs projets à la solution SiteColumnProjectItem que vous avez créée dans [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, première partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md) :  
  
-   Un projet WPF.  Vous implémenterez l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> et définirez l'interface utilisateur de l'Assistant dans ce projet.  
  
-   Un projet de bibliothèque de classes qui définit les commandes SharePoint.  Ce projet doit cibler .NET Framework 3.5.  
  
 Démarrez la procédure pas à pas en créant les projets.  
  
#### Pour créer le projet WPF  
  
1.  Dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ouvrez la solution SiteColumnProjectItem.  
  
2.  Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution **SiteColumnProjectItem**, choisissez **Ajouter**, puis **Nouveau Projet**.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, le nœud de la solution s'affiche uniquement lorsque la case à cocher **Toujours afficher la solution** est activée dans la [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
3.  En haut de la boîte de dialogue **Ajouter nouveau projet**, vérifiez que **.NET Framework 4.5** est sélectionné dans la liste des versions du .NET Framework.  
  
4.  Développez les nœuds **Visual C\#** ou **Visual Basic**, puis choisissez le nœud **Windows**.  
  
5.  Dans la liste des modèles de projet, sélectionnez **Bibliothèque de contrôles utilisateur WPF**, nommez le projet **ProjectTemplateWizard**, puis cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **ProjectTemplateWizard** à la solution et ouvre le fichier par défaut UserControl1.xaml.  
  
6.  Supprimez le fichier UserControl1.xaml du projet.  
  
#### Pour créer le projet de commandes SharePoint  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution SiteColumnProjectItem, choisissez **Ajouter**, puis **Nouveau projet**.  
  
2.  En haut de la boîte de dialogue **Ajouter un nouveau projet**, choisissez **.NET Framework 3.5** dans la liste des versions du .NET Framework.  
  
3.  Développez les nœuds **Visual C\#** ou  **Visual Basic**, puis choisissez le nœud **Windows**.  
  
4.  Sélectionnez le modèle de projet **Bibliothèque de classes**, nommez le projet **SharePointCommands**, puis cliquez sur **OK**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **SharePointCommands** à la solution et ouvre le fichier par défaut de code Class1.  
  
5.  Supprimez le fichier de code Class1 du projet.  
  
## Configuration des projets  
 Avant de créer l'Assistant, vous devez ajouter certains fichiers de code et des références d'assembly aux projets.  
  
#### Pour configurer le projet d'Assistant  
  
1.  Dans l' **Explorateur de solutions**, ouvrez le menu contextuel pour le nœud du projet **ProjectTemplateWizard**, et choisissez **Propriétés**.  
  
2.  Dans le **Concepteur de projets**, choisissez l'onglet **Application** pour un projet Visual C\# ou l'onglet **Compiler** pour un projet Visual Basic.  
  
3.  Assurez\-vous que la version cible du. Net Framework est réglée sur .NET Framework 4.5, et pas sur le profil client .NET Framework 4.5.  
  
     Pour plus d'informations, consultez [Comment : cibler une version du .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
4.  Ouvrez le menu contextuel pour le projet **ProjectTemplateWizard**, sélectionnez **Ajoute**, puis **Nouvel élément**.  
  
5.  Sélectionnez l'élément **Fenêtre \(WPF\)**, nommez l'élément **WizardWindow**, puis cliquez sur **Ajouter**.  
  
6.  Ajoutez deux éléments **Contrôle utilisateur \(WPF\)** au projet, et nommez\-les **Page1** et **Page2**.  
  
7.  Ajoutez quatre fichiers de code au projet, et donnez\-leur les noms suivants :  
  
    -   SiteColumnProjectWizard  
  
    -   SiteColumnWizardModel  
  
    -   ProjectSigningManager  
  
    -   CommandIds  
  
8.  Ouvrez le menu contextuel pour le nœud du projet **ProjectTemplateWizard**, puis sélectionnez **Ajouter une Référence**.  
  
9. Développez le nœud **Assemblys**, choisissez le nœud **Extensions**, puis sélectionnez les cases à cocher à côté des assemblys suivants :  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.OLE.Interop  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.10.0  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
10. Cliquez sur le bouton **OK** pour ajouter des assemblys au projet.  
  
11. Dans l' **Explorateur de solutions**, sous le dossier **Références** du projet **ProjectTemplateWizard**, cliquez sur **EnvDTE**.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, le dossier **Références** s'affiche uniquement si la case **Toujours afficher la solution** est cochée dans la [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
12. Dans la fenêtre **Propriétés**, affectez **False** à la valeur **Incorporer les types d'interopérabilité**.  
  
13. Si vous développez un projet Visual Basic, importez l'espace de noms ProjectTemplateWizard dans votre projet avec le **Concepteur de projet**.  
  
     Pour plus d'informations, consultez [Comment : ajouter ou supprimer des espaces de noms importés &#40;Visual Basic&#41;](~/ide/how-to-add-or-remove-imported-namespaces-visual-basic.md).  
  
#### Pour configurer le projet SharePointCommands  
  
1.  Dans l' **Explorateur de solutions**, choisissez le nœud de projet **SharePointCommands**.  
  
2.  Dans la barre de menus, choisissez **Projet**,  **Ajouter un élément existant**.  
  
3.  Dans la boîte de dialogue **Ajouter un élément existant**, recherchez le dossier contenant les fichiers de code pour le projet ProjectTemplateWizard, puis choisissez le fichier de code **CommandIds**.  
  
4.  Cliquez sur la flèche en regard du bouton **Ajouter**, puis choisissez l'option **Ajouter en tant que lien** sur le menu qui s'affiche.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le fichier de code au projet **SharePointCommands** sous la forme d'un lien.  Le fichier de code se trouve dans le projet **ProjectTemplateWizard**, mais le code dans le fichier est également compilé dans le projet **SharePointCommands**.  
  
5.  Dans le projet **SharePointCommands**, ajoutez un autre fichier de code appelé Commands.  
  
6.  Sélectionnez le projet SharePointCommands, puis, dans la barre de menus, sélectionnez **Projet**, **Ajouter une référence**.  
  
7.  Développez le nœud **Assemblys**, choisissez le nœud **Extensions**, puis sélectionnez les cases à cocher à côté des assemblys suivants :  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
8.  Cliquez sur le bouton **OK** pour ajouter des assemblys au projet.  
  
## Création du modèle d'Assistant, du gestionnaire de signature et des ID des commandes SharePoint  
 Ajoutez le code au projet ProjectTemplateWizard pour implémenter les composants suivants dans l'exemple :  
  
-   Les ID des commandes SharePoint.  Ces chaînes de caractères identifient les commandes SharePoint qui sont utilisées par l'Assistant.  À une étape ultérieure de cette procédure, vous ajouterez le code au projet SharePointCommands pour implémenter les commandes.  
  
-   Le modèle de données de l'Assistant.  
  
-   Le gestionnaire de signature du projet.  
  
 Pour plus d'informations sur ces composants, consultez [Présentation des composants de l'Assistant](#wizardcomponents).  
  
#### Pour définir les ID des commandes SharePoint  
  
1.  Dans le projet ProjectTemplateWizard, ouvrez le fichier de code CommandIds, puis remplacez le contenu entier de ce fichier par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/commandids.cs#5)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/commandids.vb#5)]  
  
#### Pour créer le modèle d'Assistant  
  
1.  Ouvrez le fichier de code SiteColumnWizardModel, puis remplacez le contenu entier de ce fichier par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/sitecolumnwizardmodel.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/sitecolumnwizardmodel.vb#6)]  
  
#### Pour créer le gestionnaire de signature de projet  
  
1.  Ouvrez le fichier de code ProjectSigningManager, puis remplacez le contenu entier de ce fichier par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/projectsigningmanager.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/projectsigningmanager.vb#8)]  
  
## Création de l'interface utilisateur de l'Assistant  
 Ajoutez la syntaxe XAML pour définir l'interface utilisateur de la fenêtre de l'Assistant et les deux contrôles utilisateur qui fournissent l'interface utilisateur pour les pages de l'Assistant, puis ajoutez le code pour définir le comportement de la fenêtre et des contrôles utilisateur.  L'Assistant que vous créez ressemble à l'Assistant intégré des projets SharePoint dans Visual Studio.  
  
> [!NOTE]  
>  Dans les étapes suivantes, Votre projet comportera des erreurs de compilation après avoir ajouté la syntaxe XAML ou le code à votre projet.  Ces erreurs disparaîtront lorsque vous ajouterez du code dans les étapes ultérieures.  
  
#### Pour créer l'interface utilisateur de la fenêtre de l'Assistant  
  
1.  Dans le projet ProjectTemplateWizard, ouvrez le menu contextuel du fichier WizardWindow.xaml, puis choisissez **Ouvrir** pour ouvrir la fenêtre dans le concepteur.  
  
2.  Dans la vue XAML du concepteur, remplacez le code XAML actuel par le code XAML suivant.  Le code XAML définit une interface utilisateur qui comprend un titre, <xref:System.Windows.Controls.Grid>, contenant les pages de l'Assistant et des boutons de navigation dans la partie inférieure de la fenêtre.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/wizardwindow.xaml#10)]  
  
    > [!NOTE]  
    >  La fenêtre créée dans ce XAML est dérivée de la classe de base <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>.  Lorsque vous ajoutez une boîte de dialogue WPF personnalisée dans Visual Studio, nous vous recommandons de dériver votre boîte de dialogue de cette classe pour assurer la cohérence du style avec d'autres boîtes de dialogue Visual Studio et pour éviter des problèmes de boîte de dialogue modale qui risqueraient de se produire.  Pour plus d'informations, consultez [Créer et gérer des boîtes de dialogue modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
3.  Si vous développez un projet Visual Basic, supprimez l'espace de noms `ProjectTemplateWizard` du nom de la classe `WizardWindow` dans l'attribut `x:Class` de l'élément `Window`.  Vet élément se trouve dans la première ligne du code XAML.  Lorsque vous avez terminé, la première ligne doit se présenter comme l'exemple suivant :  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Ouvrez le fichier code\-behind correspondant au fichier WizardWindow.xaml.  
  
5.  Remplacez le contenu du fichier, à l'exception des déclarations `using` en haut du fichier, par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/wizardwindow.xaml.cs#4)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/wizardwindow.xaml.vb#4)]  
  
#### Pour créer la première page de l'interface utilisateur de l'Assistant  
  
1.  Dans le projet ProjectTemplateWizard, ouvrez le menu contextuel pour du fichier Page1.xaml, puis choisissez **Ouvrir** pour ouvrir le contrôle utilisateur dans le concepteur.  
  
2.  Dans la vue XAML du concepteur, remplacez le code XAML actuel par le code XAML suivant.  Le code XAML définit une interface utilisateur qui comprend une zone de texte où les utilisateurs peuvent entrer l'URL des sites locaux qu'ils souhaitent utiliser pour le débogage.  L'interface utilisateur inclut également des cases d'option avec lesquelles les utilisateurs peuvent spécifier si le projet est un projet bac à sable.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page1.xaml#11)]  
  
3.  Si vous développez un projet Visual Basic, supprimez l'espace de noms `ProjectTemplateWizard` du nom de la classe `Page1` dans l'attribut `x:Class` de l'élément `UserControl`.  Cette indication se trouve dans la première ligne du code XAML.  Lorsque vous avez terminé, la première ligne doit se présenter comme suit :  
  
    ```  
    <UserControl x:Class="Page1"  
    ```  
  
4.  Remplacez le contenu du fichier Page1.xaml, à l'exception des déclarations `using` en haut du fichier, par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page1.xaml.cs#2)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/page1.xaml.vb#2)]  
  
#### Pour créer la deuxième page de l'Assistant  
  
1.  Dans le projet ProjectTemplateWizard, ouvrez le menu contextuel du fichier Page2.xaml, puis choisissez **Ouvrir**.  
  
     Le contrôle utilisateur s'affiche dans le concepteur.  
  
2.  Dans la vue XAML, remplacez le XAML courant par le code XAML suivant.  Le code XAML définit une interface utilisateur qui comprend une liste déroulante permettant de sélectionner le type de base de la colonne de site, une zone de liste déroulante pour spécifier un groupe intégré ou personnalisé sous lequel vous pouvez afficher la colonne de site dans la galerie et enfin une zone de texte pour spécifier le nom de la colonne de site.  
  
     [!code-xml[SPExtensibility.ProjectItem.SiteColumn#12](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page2.xaml#12)]  
  
3.  Si vous développez un projet Visual Basic, supprimez l'espace de noms `ProjectTemplateWizard` du nom de la classe `Page2` dans l'attribut `x:Class` de l'élément `UserControl`.  Cette indication se trouve dans la première ligne du code XAML.  Lorsque vous avez terminé, la première ligne doit se présenter comme suit :  
  
    ```  
    <UserControl x:Class="Page2"  
    ```  
  
4.  Remplacez le contenu du fichier code\-behind correspondant au fichier Page2.xaml, à l'exception des déclarations de `using` en haut du fichier, par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/page2.xaml.cs#3)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/page2.xaml.vb#3)]  
  
## Implémentation de l'Assistant  
 Définissez les principales fonctionnalités de l'Assistant en implémentant l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  Cette interface définit les méthodes appelées par Visual Studio lorsque l'Assistant démarre et finit et à certains moments pendant l'exécution de l'Assistant.  
  
#### Pour implémenter l'Assistant  
  
1.  Dans le projet ProjectTemplateWizard, ouvrez le fichier de code SiteColumnProjectWizard.  
  
2.  Remplacez le contenu entier de ce fichier par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/projecttemplatewizard/sitecolumnprojectwizard.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/projecttemplatewizard/sitecolumnprojectwizard.vb#7)]  
  
## Création de commandes SharePoint  
 Créez deux commandes personnalisées faisant appel au modèle objet serveur SharePoint.  Une commande détermine si l'URL du site que l'utilisateur entre dans l'Assistant est valide.  L'autre commande permet d'obtenir tous les types de champ du site SharePoint spécifié afin que les utilisateurs puissent sélectionner celle à utiliser comme base pour la nouvelle colonne de site.  
  
#### Pour définir les commandes SharePoint  
  
1.  Dans le projet **SharePointCommands**, ouvrez le fichier de code Commands.  
  
2.  Remplacez le contenu entier de ce fichier par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.SiteColumn#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/cs/sharepointcommands/commands.cs#9)]
     [!code-vb[SPExtensibility.ProjectItem.SiteColumn#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.sitecolumn/vb/sharepointcommands/commands.vb#9)]  
  
## Point de contrôle  
 À ce stade de la procédure, l'intégralité du code de l'Assistant fait désormais partie du projet.  Générez le projet afin de garantir sa compilation sans erreur.  
  
#### Pour générer votre projet  
  
1.  Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
## Suppression du fichier key.snk du modèle de projet  
 Dans [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, première partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md), le modèle de projet que vous avez créé contient un fichier key.snk utilisé pour signer chaque instance du projet Colonne de site.  Ce fichier key.snk n'est plus nécessaire parce que l'Assistant génère désormais un nouveau fichier key.snk pour chaque projet.  Supprimez le fichier key.snk du modèle de projet et supprimez les références à ce fichier.  
  
#### Pour supprimer le fichier key.snk du modèle de projet  
  
1.  Dans l' **Explorateur de solutions**, sous le nœud **SiteColumnProjectTemplate**, ouvrez le menu contextuel du fichier **key.snk**, puis choisissez **Supprimer**.  
  
2.  Dans la boîte de dialogue de confirmation qui apparaît, cliquez sur **OK**.  
  
3.  Sous le nœud **SiteColumnProjectTemplate**, ouvrez le fichier SiteColumnProjectTemplate.vstemplate, puis supprimez en l'élément suivant.  
  
    ```  
    <ProjectItem ReplaceParameters="false" TargetFileName="key.snk">key.snk</ProjectItem>  
    ```  
  
4.  Enregistrez et fermez le fichier.  
  
5.  Sous le nœud **SiteColumnProjectTemplate**, ouvrez le fichier ProjectTemplate.csproj ou ProjectTemplate.vbproj, puis supprimez en l'élément `PropertyGroup` suivant.  
  
    ```  
    <PropertyGroup>  
      <SignAssembly>true</SignAssembly>  
      <AssemblyOriginatorKeyFile>key.snk</AssemblyOriginatorKeyFile>  
    </PropertyGroup>  
    ```  
  
6.  Supprimez l'élément `None` suivant.  
  
    ```  
    <None Include="key.snk" />  
    ```  
  
7.  Enregistrez et fermez le fichier.  
  
## Association de l'Assistant au modèle de projet  
 Maintenant que vous avez implémenté l'Assistant, vous devez l'associer au modèle de projet **Colonne de site**.  Cette opération se déroule en trois étapes :  
  
1.  Signature de l'assembly de l'Assistant avec un nom fort.  
  
2.  Obtention du jeton de clé publique correspondant à l'assembly de l'Assistant.  
  
3.  Ajoutez une référence à l'assembly de l'Assistant dans le fichier .vstemplate du modèle de projet **Colonne de site**.  
  
#### Pour signer l'assembly de l'Assistant avec un nom fort  
  
1.  Dans l' **Explorateur de solutions**, ouvrez le menu contextuel du projet **ProjectTemplateWizard**, puis choisissez **Propriétés**.  
  
2.  Sous l'onglet **Signature**, activez la case à cocher **Signer l'assembly**.  
  
3.  Dans la liste **Choisir un nom fort de fichier clé**, cliquez sur **\<Nouveau...\>**.  
  
4.  Dans la boîte de dialogue **Créer un nom fort de clé**, entrez un nom pour le nouveau fichier clé et désactivez la case à cocher **Protéger mon fichier de clé avec un mot de passe**. Enfin, cliquez sur **OK**.  
  
5.  Ouvrez le menu contextuel du projet **ProjectTemplateWizard**, puis choisissez **Générer** pour créer le fichier ProjectTemplateWizard.dll.  
  
#### Pour obtenir le jeton de clé publique correspondant à l'assembly de l'Assistant  
  
1.  Sur le **Menu Démarrer**, choisissez **Tous les programmes**, **Microsoft Visual Studio**, puis **Visual Studio Tools**, et enfin **Invite de commandes développeur**.  
  
     Une fenêtre Invite de commandes de Visual Studio s'ouvre.  
  
2.  Exécutez la commande suivante, remplaçant le *PathToWizardAssembly* par le chemin d'accès complet à l'assembly ProjectTemplateWizard.dll créé pour le projet ProjectTemplateWizard sur votre ordinateur de développement.  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Le jeton de clé publique correspondant à l'assembly ProjectTemplateWizard.dll est écrit dans la fenêtre Invite de commandes de Visual Studio.  
  
3.  Ne fermez pas la fenêtre Invite de commandes de Visual Studio.  Vous aurez besoin du jeton de clé publique pour la procédure suivante.  
  
#### Pour ajouter une référence à l'assembly de l'Assistant dans le fichier .vstemplate  
  
1.  Dans l'**Explorateur de solutions**, développez le nœud du projet **SiteColumnProjectTemplate** et ouvrez le fichier SiteColumnProjectTemplate.vstemplate.  
  
2.  À l'approche de la fin du fichier, ajoutez l'élément suivant `WizardExtension` entre les balises `</TemplateContent>` et `</VSTemplate>`.  Remplacez la valeur de *your token* de l'attribut `PublicKeyToken` par le jeton de clé publique que vous avez obtenu dans la procédure précédente.  
  
    ```  
    <WizardExtension>  
      <Assembly>ProjectTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=your token</Assembly>  
      <FullClassName>ProjectTemplateWizard.SiteColumnProjectWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Pour plus d'informations sur l'élément `WizardExtension`, consultez [WizardExtension, élément &#40;modèles Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).  
  
3.  Enregistrez et fermez le fichier.  
  
## Ajout de paramètres remplaçables au fichier Elements.xml du modèle de projet  
 Ajoutez plusieurs paramètres remplaçables au fichier Elements.xml du projet SiteColumnProjectTemplate.  Ces paramètres sont initialisés dans la méthode `RunStarted` de la classe `SiteColumnProjectWizard` que vous avez définie précédemment.  Lorsqu'un utilisateur crée un projet Colonne de site, Visual Studio remplace automatiquement ces paramètres dans le fichier Elements.xml du nouvel élément de projet par les valeurs qui ont été spécifiées dans l'Assistant.  
  
 Un paramètre remplaçable est un jeton qui commence et se termine par le signe dollar \($\).  Vous pouvez non seulement définir vos propres paramètres remplaçables, mais également utiliser des paramètres intégrés qui sont définis et initialisés par le système de projet SharePoint.  Pour plus d'informations, consultez [Paramètres remplaçables](../sharepoint/replaceable-parameters.md).  
  
#### Pour ajouter des paramètres remplaçables au fichier Elements.xml  
  
1.  Dans le projet SiteColumnProjectTemplate, remplacez le contenu du fichier Elements.xml par le code XML suivant.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <Field ID="{$guid5$}"   
             Name="$fieldname$"   
             DisplayName="$fieldname$"   
             Type="$selectedfieldtype$"   
             Group="$selectedgrouptype$">  
      </Field>  
    </Elements>  
    ```  
  
     Dans le nouveau code XML, les paramètres remplaçables se substituent aux valeurs des attributs `Name`, `DisplayName`, `Type` et `Group`.  
  
2.  Enregistrez et fermez le fichier.  
  
## Ajout de l'Assistant au package VSIX  
 Pour déployer l'Assistant avec le package VSIX qui contient le modèle du projet Colonne de site, ajoutez des références au projet d'Assistant et au projet de commandes SharePoint dans le fichier source.extension.vsixmanifest du projet VSIX.  
  
#### Pour ajouter l'Assistant au package VSIX  
  
1.  Dans l' **Explorateur de solutions**, dans le projet **SiteColumnProjectItem**, ouvrez le menu contextuel du fichier **source.extension.vsixmanifest**, puis choisissez **Ouvrir**.  
  
     Visual Studio ouvre le fichier dans l'éditeur de manifeste.  
  
2.  Sous l'onglet **Composants** de l'éditeur, choisissez le bouton **Nouveau**.  
  
     La boîte de dialogue **Ajouter un nouveau composant** s'ouvre.  
  
3.  Dans la liste **Type**, choisissez **Microsoft.VisualStudio.Assembly**.  
  
4.  Dans la liste **Source**, choisissez **Un projet dans la solution actuelle**.  
  
5.  Dans la liste **Project**, choisissez **ProjectTemplateWizard**, puis choisissez le bouton **OK**.  
  
6.  Sous l'onglet **Composants** de l'éditeur, cliquez à nouveau sur **Nouveau**.  
  
     La boîte de dialogue **Ajouter un nouveau composant** s'ouvre.  
  
7.  Dans la liste **Type**, entrez **SharePoint.Commands.v4**.  
  
8.  Dans la liste **Source**, choisissez **Un projet dans la solution actuelle**.  
  
9. Dans la liste **Projet**, sélectionnez le projet **SharePointCommands**, puis cliquez sur **OK**.  
  
10. Dans la barre de menus, sélectionnez **Générer**, **Générer la solution**, puis vérifiez que les solutions se construisent sans erreurs.  
  
## Test de l'Assistant  
 Vous êtes maintenant prêt à tester l'Assistant.  Commencez à déboguer la solution SiteColumnProjectItem dans l'instance expérimentale de Visual Studio.  Ensuite, testez l'Assistant du projet Colonne du site dans l'instance expérimentale de Visual Studio.  Enfin, générez et exécutez le projet pour vous assurer que la colonne de site fonctionne comme prévu.  
  
#### Pour commencer à déboguer la solution  
  
1.  Redémarrez Visual Studio avec les droits d'administrateur et ouvrez la solution SiteColumnProjectItem.  
  
2.  Dans le projet ProjectTemplateWizard, ouvrez le fichier code SiteColumnProjectWizard puis ajoutez un point d'arrêt au niveau de la première ligne de code dans la méthode `RunStarted`.  
  
3.  Sur la barre de menus, choisissez **Débogage**, **Exceptions**.  
  
4.  Dans la boîte de dialogue **Exceptions**, vérifiez que les cases à cocher **Levé** et **Non géré par l'utilisateur** correspondant à **Exceptions Common Language Runtime** sont désactivées, puis cliquez sur **OK**.  
  
5.  Démarrez le débogage en appuyant sur la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**, **Démarrer le débogage**.  
  
     Visual Studio installe l'extension sous %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Site Column\\1.0 et démarre une instance expérimentale de Visual Studio.  Vous testerez l'élément de projet dans cette instance de Visual Studio.  
  
#### Pour tester l'Assistant dans Visual Studio  
  
1.  Dans l'instance expérimentale de Visual Studio, dans la barre de menu, sélectionnez **Fichier**, **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Développez le nœud **Visual C\#** ou **Visual Basic** \(selon le langage pris en charge par votre modèle de projet\), développez **SharePoint**, puis cliquez sur le nœud **2010**.  
  
3.  Dans la liste des modèles de projet, choisissez **Site Column**, nommez\-le **SiteColumnWizardTest**, puis cliquez sur **OK**.  
  
4.  Assurez\-vous que le code dans l'autre instance de Visual Studio s'arrête au niveau du point d'arrêt que vous avez défini précédemment dans la méthode `RunStarted`.  
  
5.  Continuez à déboguer le projet en cliquant sur la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**, **Continuer**.  
  
6.  Dans **l'Assistant Personnalisation de SharePoint**, saisissez l'URL du site que vous souhaitez utiliser pour le débogage, puis cliquez sur **Suivant**.  
  
7.  Dans la deuxième page de l'**Assistant Personnalisation de SharePoint**, effectuez les sélections suivantes :  
  
    -   Dans la liste **Type**, choisissez **Booléen**.  
  
    -   Dans la liste **Groupe**, choisissez **Colonnes Oui\/Non personnalisées**.  
  
    -   Dans la zone **Nom**, entrez Ma colonne Oui\/Non, puis cliquez sur **Terminer**.  
  
     Dans l' **Explorateur de solutions**, un nouveau projet apparaît et contient un élément de projet nommé **Field1** et Visual Studio ouvre le fichier Elements.xml du projet dans l'éditeur.  
  
8.  Vérifiez que le fichier Elements.xml contient les valeurs que vous avez spécifiées dans l'Assistant.  
  
#### Pour tester la colonne de site dans SharePoint  
  
1.  Dans l'instance expérimentale de Visual Studio, appuyez sur F5.  
  
     La colonne du site est empaquetée et déployée sur le site SharePoint que la propriété **URL de site** du projet spécifie.  Le navigateur Web s'ouvre à la page par défaut de ce site.  
  
    > [!NOTE]  
    >  Si la boîte de dialogue **Le débogage de script est désactivé** s'affiche, cliquez sur **Oui** pour continuer à déboguer le projet.  
  
2.  Dans le menu **Actions de site**, cliquez sur **Paramètres du site**.  
  
3.  Dans la page Paramètres du site, sous **Galeries**, choisissez le lien **Colonnes de site**.  
  
4.  Dans la liste des colonnes de site, vérifiez qu'il existe un groupe **Colonnes personnalisées Oui\/Non** qui contient une colonne nommée **Ma colonne Oui\/Non**, puis fermez le navigateur web.  
  
## Nettoyage de l'ordinateur de développement  
 Une fois le test de l'élément de projet terminé, supprimez le modèle de projet de l'instance expérimentale de Visual Studio.  
  
#### Pour nettoyer l'ordinateur de développement  
  
1.  Dans l'instance expérimentale de Visual Studio, dans la barre de menu, cliquez sur **Outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s'ouvre.  
  
2.  Dans la liste des extensions, choisissez **Colonne de site**, puis cliquez sur **Désinstaller**.  
  
3.  Dans la boîte de dialogue qui apparaît, cliquez sur **Oui** pour confirmer que vous voulez désinstaller l'extension, puis cliquez sur **Redémarrer maintenant** pour terminer la désinstallation.  
  
4.  Fermez les deux instances de Visual Studio \(l'instance expérimentale et l'instance de Visual Studio dans laquelle la solution CustomActionProjectItem est ouverte\).  
  
     Pour plus d'informations sur le déploiement d'extensions [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], consultez [Envoi des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
## Voir aussi  
 [Procédure pas à pas : création d'un élément de projet Colonne de site avec un modèle de projet, première partie](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Comment : utiliser des Assistants avec des modèles de projet](~/extensibility/how-to-use-wizards-with-project-templates.md)  
  
  