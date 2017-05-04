---
title: "Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2 | Microsoft Docs"
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
  - "project items [SharePoint development in Visual Studio], creating template wizards"
  - "SharePoint project items, creating template wizards"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 2d8165d3-4af9-4a5e-bdba-8b2a06b1dc8d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2
  Après avoir défini un type personnalisé d'élément de projet SharePoint et l'avoir associé à un modèle d'élément dans Visual Studio, vous pouvez également fournir un Assistant pour le modèle.  Vous pouvez utiliser l'Assistant pour collecter des informations auprès d'utilisateurs lorsqu'ils utilisent votre modèle pour ajouter à un projet une nouvelle instance de l'élément de projet.  Les informations que vous collectez peuvent être utilisées pour initialiser l'élément de projet.  
  
 Dans cette procédure pas à pas, vous ajouterez un Assistant à l'élément de projet Action personnalisée présenté dans [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  Lorsqu'un utilisateur ajoute un élément de projet action personnalisée à un projet SharePoint, l'assistant collecte également des informations sur l'action personnalisée \(telle que son emplacement et l'URL vers lequel naviguer lorsqu'un utilisateur final le sélectionne\) et ajoute ces informations dans le fichier Elements.xml du nouvel élément de projet.  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Création d'un Assistant pour un type d'élément de projet SharePoint personnalisé associé à un modèle d'élément.  
  
-   Définition d'une interface utilisateur d'Assistant personnalisé semblable aux assistants intégrés des éléments de projet SharePoint dans Visual Studio.  
  
-   Utilisation de paramètres remplaçables pour initialiser les fichiers de projet SharePoint avec les données que vous collectez dans l'Assistant.  
  
-   Débogage et test de l'Assistant.  
  
> [!NOTE]  
>  Vous pouvez télécharger une instance qui contient les projets remplis, de code, et d'autres fichiers pour cette procédure pas \- à \- pas de l'emplacement suivant : [Fichiers projet pour les procédures pas \- à \- pas d'extensibilité d'outils sharepoint](http://go.microsoft.com/fwlink/?LinkId=191369).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez d'abord créer la solution CustomActionProjectItem en suivant la procédure décrite dans [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Vous avez par ailleurs besoin des composants suivants sur l'ordinateur de développement pour exécuter cette procédure pas à pas :  
  
-   Éditions prises windows, de SharePoint, et Visual Studio.  Pour plus d’informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Le kit de développement Visual Studio.  Cette procédure pas à pas utilise le modèle **Projet VSIX** du Kit de développement logiciel \(SDK\) pour créer un package VSIX afin de déployer l'élément de projet.  Pour plus d’informations, consultez [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Une connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer cette procédure pas à pas :  
  
-   Assistants associés aux modèles de projet et d'élément dans Visual Studio.  Pour plus d'informations, consultez [Comment : utiliser des Assistants avec des modèles de projet](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md) et l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
-   Actions personnalisées dans SharePoint.  Pour plus d'informations, consultez [Action personnalisée](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## Création du projet d'Assistant  
 Pour exécuter cette procédure, vous devez ajouter un projet à la solution CustomActionProjectItem que vous avez créé dans [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  Vous implémenterez l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> et définirez l'interface utilisateur de l'Assistant dans ce projet.  
  
#### Pour créer le projet d'Assistant  
  
1.  Dans Visual Studio, ouvrez la solution CustomActionProjectItem  
  
2.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution, choisissez **Ajouter**, puis choisissez **Nouveau projet**.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, le nœud de la solution s'affiche dans l'**Explorateur de solutions** à condition d'avoir activé la case à cocher **Toujours afficher la solution** dans la [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
3.  Dans la boîte de dialogue **Nouveau projet** , développez les nœuds **Visual C\#** ou **Visual Basic** , puis sélectionnez le nœud **Fenêtres** .  
  
4.  En haut de la boîte de dialogue **Nouveau projet** , assurez \-vous que **.NET Framework 4,5** est sélectionnez dans la liste des versions du .NET Framework.  
  
5.  Choisissez le modèle de projet **Bibliothèque de contrôles utilisateur WPF** , nommez le projet **ItemTemplateWizard**, puis choisissez le bouton **OK** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **ItemTemplateWizard** à la solution.  
  
6.  Supprimez l'élément UserControl1 du projet.  
  
## Configuration du projet d'Assistant  
 Avant de créer l'assistant, vous devez ajouter une fenêtre de Windows Presentation Foundation \(WPF\), un fichier de code, et des références d'assembly au projet.  
  
#### Pour configurer le projet d'Assistant  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **ItemTemplateWizard** , puis choisissez **Propriétés**.  
  
2.  Dans **Concepteur de projets**, assurez \-vous que la version cible du. Net Framework a pour valeur le .NET Framework 4,5.  
  
     Pour les projets visual C\#, vous pouvez définir cette valeur sur **Application** tableau.  Pour les projets Visual Basic, vous pouvez définir cette valeur sur **Compiler** tableau.  Pour plus d’informations, consultez [Comment : cibler une version du .NET Framework](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md).  
  
3.  Dans le projet **ItemTemplateWizard** , ajoutez un élément **fenêtre \(WPF\)** au projet, puis nommez l'élément **WizardWindow**.  
  
4.  Ajoutez deux fichiers de code CustomActionWizard nommés et chaînes.  
  
5.  Ouvrez le menu contextuel du projet **ItemTemplateWizard** , puis choisissez **Ajouter une référence**.  
  
6.  Dans la boîte de dialogue **gestionnaire de référence \- ItemTemplateWizard** , sous le nœud **Assemblys** , sélectionnez le nœud **Extensions** .  
  
7.  Activez les cases à cocher en regard de les assemblys suivants, puis choisissez le bouton **OK** :  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  Dans **Explorateur de solutions**, dans le dossier **Références** pour le projet ItemTemplateWizard, sélectionnez la référence **EnvDTE** .  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, le dossier **Références** s'affiche uniquement si la case **Toujours afficher la solution** est cochée dans la [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
9. Dans la fenêtre **Propriétés** , remplacez la valeur de la propriété **Embed Interop Types** par **False**.  
  
## Définition des chaînes d'emplacement et d'ID par défaut pour les actions personnalisées  
 À chaque action personnalisée correspondent un emplacement et un ID spécifiés dans les attributs `GroupID` et `Location` de l'élément `CustomAction` du fichier Elements.xml.  Dans cette étape, vous allez définir certaines des chaînes valides pour ces attributs dans le projet ItemTemplateWizard.  Lorsque vous terminez cette procédure pas \- à \- pas, ces chaînes sont écrites dans le fichier Elements.xml dans l'élément de projet action personnalisée lorsque les utilisateurs spécifiez un emplacement et un ID dans l'assistant.  
  
 Pour plus de simplicité, cet exemple prend en charge uniquement un sous\-ensemble des emplacements et ID par défaut disponibles.  Pour obtenir une liste complète, consultez [Emplacements et ID d'action personnalisée par défaut \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### Pour définir les chaînes d'emplacement et d'ID par défaut  
  
1.  ouvrez.  
  
2.  Dans le projet **ItemTemplateWizard** , remplacez le code dans le fichier de code de chaînes par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/strings.vb#6)]  
  
## Création de l'interface utilisateur de l'Assistant  
 Ajoutez du contenu XAML pour définir l'interface utilisateur de l'Assistant, ainsi que du code permettant de lier certains contrôles de l'Assistant aux chaînes d'ID.  L'assistant que vous créez ressemble à l'assistant intégré des projets sharepoint dans Visual Studio.  
  
#### Pour créer l'interface utilisateur de l'Assistant  
  
1.  Dans le projet **ItemTemplateWizard** , ouvrez le menu contextuel du fichier **WizardWindow.xaml** , puis choisissez **Ouvrir** pour ouvrir la fenêtre dans le concepteur.  
  
2.  En mode XAML, remplacez le code XAML existant par le code XAML suivant.  Le code XAML définit une interface utilisateur qui se compose d'un titre, de contrôles permettant de spécifier le comportement de l'action personnalisée et des boutons de navigation dans la partie inférieure de la fenêtre.  
  
    > [!NOTE]  
    >  Votre projet comportera des erreurs de compilation après avoir ajouté ce code.  Ces erreurs disparaîtront lorsque vous ajouterez du code dans les étapes ultérieures.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  La fenêtre créée dans ce XAML est dérivée de la classe de base d' <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> .  Lorsque vous ajoutez une boîte de dialogue de la personnalisés WPF dans Visual Studio, nous recommandons que vous dérivez votre boîte de dialogue de cette classe pour avoir un style cohérent avec d'autres boîtes de dialogue dans Visual Studio et pour éviter des problèmes susceptibles de se produire avec les boîtes de dialogue modale.  Pour plus d’informations, consultez [Créer et gérer des boîtes de dialogue modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
3.  Si vous développez un projet Visual Basic, supprimez l'espace de noms d' `ItemTemplateWizard` du nom de classe d' `WizardWindow` dans l'attribut d' `x:Class` de l'élément d' `Window` .  Cet élément est aligné en premier du XAML.  Lorsque vous avez terminé, la première ligne doit ressembler au code suivant :  
  
    ```  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Dans le fichier code\-behind correspondant au fichier WizardWindow.xaml, remplacez le code existant par le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/wizardwindow.xaml.cs#7)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/wizardwindow.xaml.vb#7)]  
  
## Implémentation de l'Assistant  
 Définissez les fonctionnalités de l'Assistant en implémentant l'interface <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
#### Pour implémenter l'Assistant  
  
1.  Dans le projet **ItemTemplateWizard** , ouvrez le fichier de code **CustomActionWizard** , puis remplacez le code existant dans ce fichier par le code suivant :  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/cs/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitem.customaction/vb/itemtemplatewizard/customactionwizard.vb#8)]  
  
## Point de contrôle  
 À ce stade de la procédure, l'intégralité du code de l'Assistant fait désormais partie du projet.  Générez le projet afin de garantir sa compilation sans erreur.  
  
#### Pour générer votre projet  
  
1.  Dans la barre de menus, sélectionnez **Générer**, **Générer la solution**.  
  
## Association de l'Assistant au modèle d'élément  
 Maintenant que vous avez implémenté l'assistant, vous devez l'associer au modèle d'élément **action personnalisée** en effectuant trois étapes principales :  
  
1.  Signature de l'assembly de l'Assistant avec un nom fort.  
  
2.  Obtention du jeton de clé publique correspondant à l'assembly de l'Assistant.  
  
3.  Ajout d'une référence à l'assembly de l'Assistant dans le fichier .vstemplate pour le modèle d'élément **Action personnalisée**.  
  
#### Pour signer l'assembly de l'Assistant avec un nom fort  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **ItemTemplateWizard** , puis choisissez **Propriétés**.  
  
2.  Sous l'onglet **Signature**, activez la case à cocher **Signer l'assembly**.  
  
3.  Dans la liste **choisissez un fichier de clé de nom fort** , choisissez **\<New...\>**.  
  
4.  Dans la boîte de dialogue **créez la clé de nom fort** , entrez un nom, désactivez la case à cocher **protégez mon fichier de clé avec un mot de passe** , puis choisissez le bouton **OK** .  
  
5.  Dans la barre de menus, sélectionnez **Générer**, **Générer la solution**.  
  
#### Pour obtenir le jeton de clé publique correspondant à l'assembly de l'Assistant  
  
1.  Dans une fenêtre d'invite de commandes de Visual Studio, exécutez la commande suivante, en remplaçant *PathToWizardAssembly* par le chemin d'accès complet à l'assembly ItemTemplateWizard.dll créé pour le projet ItemTemplateWizard sur votre ordinateur de développement.  
  
    ```  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Le jeton de clé publique correspondant à l'assembly ItemTemplateWizard.dll est écrit dans la fenêtre Invite de commandes de Visual Studio.  
  
2.  Ne fermez pas la fenêtre Invite de commandes de Visual Studio.  Vous aurez besoin du jeton de clé publique pour exécuter la procédure suivante.  
  
#### Pour ajouter une référence à l'assembly de l'Assistant dans le fichier .vstemplate  
  
1.  Dans **Explorateur de solutions**, développez le nœud de projet **ItemTemplate** , puis ouvrez le fichier ItemTemplate.vstemplate.  
  
2.  À l'approche de la fin du fichier, ajoutez l'élément suivant `WizardExtension` entre les balises `</TemplateContent>` et `</VSTemplate>`.  Remplacez la valeur de *YourToken* de l'attribut d' `PublicKeyToken` par le jeton de clé publique que vous avez obtenu dans la procédure précédente.  
  
    ```  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Pour plus d'informations sur l'élément `WizardExtension`, consultez [WizardExtension, élément &#40;modèles Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).  
  
3.  Enregistrez et fermez le fichier.  
  
## Ajout de paramètres remplaçables au fichier Elements.xml du modèle d'élément  
 Ajoutez plusieurs paramètres remplaçables au fichier Elements.xml du projet ItemTemplate.  Ces paramètres sont initialisés dans la méthode `PopulateReplacementDictionary` de la classe `CustomActionWizard` que vous avez définie précédemment.  Lorsqu'un utilisateur ajoute un élément de projet Action personnalisée à un projet, Visual Studio remplace automatiquement ces paramètres dans le fichier Elements.xml du nouvel élément de projet par les valeurs qui ont été spécifiées dans l'Assistant.  
  
 Un paramètre remplaçable est un jeton qui commence et se termine par le signe dollar \($\).  En plus de définir vos propres paramètres remplaçables, vous pouvez utiliser les paramètres prédéfinis que le système de projet SharePoint définit et initialise.  Pour plus d’informations, consultez [Paramètres remplaçables](../sharepoint/replaceable-parameters.md).  
  
#### Pour ajouter des paramètres remplaçables au fichier Elements.xml  
  
1.  Dans le projet ItemTemplate, remplacez le contenu du fichier Elements.xml par le code XML suivant.  
  
    ```  
  
    <Elements Id="$guid8$" xmlns="http://schemas.microsoft.com/sharepoint/">  
      <CustomAction Id="$IdValue$"  
                    GroupId="$GroupIdValue$"  
                    Location="$LocationValue$"  
                    Sequence="1000"  
                    Title="$TitleValue$"  
                    Description="$DescriptionValue$" >  
        <UrlAction Url="$UrlValue$"/>  
      </CustomAction>  
    </Elements>  
    ```  
  
     Dans le nouveau code XML, les paramètres remplaçables se substituent aux valeurs des attributs `Id`, `GroupId`, `Location`, `Description` et `Url`.  
  
2.  Enregistrez et fermez le fichier.  
  
## Ajout de l'Assistant au package VSIX  
 Dans le fichier source.extension.vsixmanifest du projet VSIX, ajoutez une référence au projet d'Assistant afin qu'il vous soit déployé avec le package VSIX qui contient l'élément de projet.  
  
#### Pour ajouter l'Assistant au package VSIX  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du fichier **source.extension.vsixmanifest** dans le projet élémentprojetactionpersonnalisée, puis choisissez **Ouvrir** pour l'ouvrir dans l'éditeur de manifeste.  
  
2.  Dans l'éditeur de manifeste, sélectionnez l'onglet **Composants** , puis choisissez le bouton **Nouveau** .  
  
     La boîte de dialogue **ajoutez le nouveau ressource** s'affiche.  
  
3.  Dans la liste **Type** , choisissez **Microsoft.VisualStudio.Assembly**.  
  
4.  Dans la liste **Source** , choisissez **un projet dans la solution actuelle**.  
  
5.  Dans la liste **Projet** , choisissez **ItemTemplateWizard**, puis choisissez le bouton **OK** .  
  
6.  Dans la barre de menus, sélectionnez **Générer**, **Générer la solution**, puis vérifiez que les compilations de solution sans erreur.  
  
## Test de l'Assistant  
 Vous êtes maintenant prêt à tester l'Assistant.  D'abord, commencez à déboguer la solution CustomActionProjectItem dans l'instance expérimentale de Visual Studio.  Examinez ensuite l'assistant pour l'élément de projet action personnalisée dans un projet SharePoint dans l'instance expérimentale de Visual Studio.  Enfin, générez et exécutez le projet SharePoint pour vous assurer que l'action personnalisée fonctionne comme prévu.  
  
#### Pour commencer à déboguer la solution  
  
1.  Redémarrez Visual Studio avec les informations d'identification d'administration, puis ouvrez la solution élémentprojetactionpersonnalisée.  
  
2.  Dans le projet ItemTemplateWizard, ouvrez le fichier de code CustomActionWizard, puis ajoutez un point d'arrêt sur la première ligne de code dans la méthode d' `RunStarted` .  
  
3.  Dans la barre de menus, sélectionnez **Déboguer**, **Exceptions**.  
  
4.  Dans la boîte de dialogue **Exceptions** , assurez \-vous que les cases à cocher **Levé** et **utilisateur non pris en charge** pour **Exceptions du common langage runtime** sont supprimées, puis choisissez le bouton **OK** .  
  
5.  Commencez à déboguer en choisissant la touche F5, ou, dans la barre de menus, choisissant **Déboguer**, **Démarrer le débogage**.  
  
     Visual Studio installe l'extension sous %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Custom Action Project Item\\1.0 and starts an experimental instance of Visual Studio.  Vous testerez l'élément de projet dans cette instance de Visual Studio.  
  
#### Pour tester l'Assistant dans Visual Studio  
  
1.  Dans l'instance expérimentale de Visual Studio, dans le menu, choisissez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Développez le nœud **Visual C\#** ou **Visual Basic** \(selon le langage qui pris en charge par votre modèle d'élément\), développez le nœud **SharePoint** , puis sélectionnez le nœud **2010** .  
  
3.  Dans la liste des modèles de projet, choisissez **Projet SharePoint 2010**, nommez le projet **CustomActionWizardTest**, puis choisissez le bouton **OK** .  
  
4.  Dans **Assistant personnalisation de SharePoint**, entrez l'URL du site que vous souhaitez utiliser pour le débogage, puis choisissez le bouton **Terminer** .  
  
5.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet, choisissez **Ajouter**, puis choisissez **Nouvel élément**.  
  
6.  Dans la boîte de dialogue **ajoutez le nouvel élément \- CustomItemWizardTest** , développez le nœud **SharePoint** , puis développez le nœud **2010** .  
  
7.  Dans la liste d'éléments de projet, sélectionnez l'élément **action personnalisée** , puis choisissez le bouton **Ajouter** .  
  
8.  Assurez\-vous que le code dans l'autre instance de Visual Studio s'arrête au niveau du point d'arrêt que vous avez défini précédemment dans la méthode `RunStarted`.  
  
9. Continuez à déboguer le projet en sélectionnant la touche F5 ou, dans la barre de menus, choisissant **Déboguer**, **Continuer**.  
  
     L'Assistant Personnalisation de SharePoint s'affiche.  
  
10. Sous **Emplacement**, sélectionnez la case d'option **modification de liste** .  
  
11. Dans la liste **identification groupe** , choisissez **Communications**.  
  
12. Dans la zone **Titre** , entrez **Centre de développement SharePoint**.  
  
13. Dans la zone **Description** , entrez **Ouvre le site Web du centre de développement SharePoint**.  
  
14. Dans la zone **URL** , entrez **http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx**, puis choisissez le bouton **Terminer** .  
  
     le isual studio ajoute un élément nommé **CustomAction1** à votre projet et ouvre le fichier Elements.xml dans l'éditeur.  Vérifiez que le fichier Elements.xml contient les valeurs que vous avez spécifiées dans l'Assistant.  
  
#### Pour tester l'action personnalisée dans SharePoint  
  
1.  Dans l'instance expérimentale de Visual Studio, choisissez la touche F5 ou, dans la barre de menus, sélectionnez **Déboguer**, **Démarrer le débogage**.  
  
     L'action personnalisée est empaquetée et déployée sur le site SharePoint spécifié par la propriété **Recherchez l'URL** du projet, et le navigateur web s'ouvre à la page par défaut de ce site.  
  
    > [!NOTE]  
    >  Si la boîte de dialogue **Débogage de script est désactivé** s'affiche, cliquez sur le bouton **oui** .  
  
2.  Dans la zone de liste du site SharePoint, cliquez sur le lien **Tâches** .  
  
     La page **tâches – toutes tâches** s'affiche.  
  
3.  Sous l'onglet **outils de liste** du ruban, cliquez sur l'onglet **liste** , puis, dans le groupe **Paramètres** , choisissez **Paramètres de liste**.  
  
     La page **Répertoriez les paramètres** s'affiche.  
  
4.  Sous **Communications** en\-tête se en haut de la page, cliquez sur le lien **Centre de développement SharePoint** , vérifiez que le navigateur ouvre le site Web http:\/\/msdn.microsoft.com\/sharepoint\/default.aspx, puis fermez le navigateur.  
  
## Nettoyage de l'ordinateur de développement  
 Une fois le test de l'élément de projet terminé, supprimez le modèle d'élément de projet de l'instance expérimentale de Visual Studio.  
  
#### Pour nettoyer l'ordinateur de développement  
  
1.  Dans l'instance expérimentale de Visual Studio, dans le menu, choisissez **Outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s'ouvre.  
  
2.  Dans la liste d'extensions, sélectionnez l'extension **Élément de projet action personnalisée** , puis choisissez le bouton **Désinstaller** .  
  
3.  Dans la boîte de dialogue qui s'affiche, cliquez sur le bouton **oui** pour confirmer que vous voulez désinstaller l'extension, puis choisissez le bouton **Redémarrez maintenant** pour terminer la désinstallation.  
  
4.  Fermez les deux instances de Visual Studio \(l'instance expérimentale et l'instance de Visual Studio dans laquelle la solution élémentprojetactionpersonnalisée est ouverte\).  
  
## Voir aussi  
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Comment : utiliser des Assistants avec des modèles de projet](../Topic/How%20to:%20Use%20Wizards%20with%20Project%20Templates.md)   
 [Est la valeur par défaut des emplacements personnalisés et les ID d'action](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
  