---
title: 'Procédure pas à pas : Création d’un élément de projet d’Action personnalisé avec un modèle d’élément, partie 2 | Microsoft Docs'
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
ms.openlocfilehash: 13d3c9db34824808cf5e02fbe7fb1af3911dfd0f
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118973"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Procédure pas à pas : Créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 2
  Une fois que vous définissez un type d’élément de projet SharePoint personnalisé et l’associez à un modèle d’élément dans Visual Studio, vous souhaiterez également fournir un Assistant pour le modèle. Vous pouvez utiliser l’Assistant pour collecter des informations auprès des utilisateurs lorsqu’ils utilisent votre modèle pour ajouter une nouvelle instance de l’élément de projet à un projet. Les informations que vous recueillez peuvent être utilisées pour initialiser l’élément de projet.  
  
 Dans cette procédure pas à pas, vous allez ajouter un Assistant à l’élément de projet d’Action personnalisée qui est illustré dans [procédure pas à pas : créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Lorsqu’un utilisateur ajoute un élément de projet d’Action personnalisé à un projet SharePoint, l’Assistant recueille des informations sur l’action personnalisée (par exemple, son emplacement et l’URL vers laquelle naviguer lorsqu’un utilisateur final choisit) et ajoute ces informations pour le *Elements.xml* fichier dans le nouvel élément de projet.  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un Assistant pour un type d’élément de projet SharePoint personnalisé associé à un modèle d’élément.  
  
-   Définition d’un Assistant personnalisé l’interface utilisateur semblable aux Assistants intégrés pour les éléments de projet SharePoint dans Visual Studio.  
  
-   À l’aide des paramètres remplaçables pour initialiser les fichiers de projet SharePoint avec les données que vous collectez dans l’Assistant.  
  
-   Débogage et test de l’Assistant.  
  
> [!NOTE]  
>  Vous pouvez télécharger un exemple de [Github](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) qui montre comment créer des activités personnalisées pour un flux de travail.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure pas à pas, vous devez d’abord créer la solution CustomActionProjectItem en effectuant [procédure pas à pas : créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 Vous devez également les composants suivants sur l’ordinateur de développement pour effectuer cette procédure pas à pas :  
  
-   Éditions prises en charge de Windows, SharePoint et Visual Studio. Pour plus d’informations, consultez [configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Le Kit de développement logiciel avec Visual Studio. Cette procédure pas à pas utilise le **projet VSIX** modèle dans le Kit de développement logiciel pour créer un package VSIX pour déployer l’élément de projet. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Connaissance des concepts suivants est utile, mais pas obligatoire, pour suivre la procédure pas à pas :  
  
-   Assistants pour les modèles de projet et d’élément dans Visual Studio. Pour plus d’informations, consultez [Comment : utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md) et <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.  
  
-   Actions personnalisées dans SharePoint. Pour plus d’informations, consultez [Custom Action](http://go.microsoft.com/fwlink/?LinkId=177800).  
  
## <a name="create-the-wizard-project"></a>Créer le projet d’Assistant
 Pour effectuer cette procédure pas à pas, vous devez ajouter un projet à la solution CustomActionProjectItem que vous avez créé dans [procédure pas à pas : créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Vous allez implémenter le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> d’interface et de définir l’interface utilisateur de l’Assistant dans ce projet.  
  
#### <a name="to-create-the-wizard-project"></a>Pour créer le projet d’Assistant  
  
1.  Dans Visual Studio, ouvrez la solution CustomActionProjectItem  
  
2.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud de solution, choisissez **ajouter**, puis choisissez **nouveau projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, puis choisissez le **Windows** nœud.  
  
4.  En haut de la **nouveau projet** boîte de dialogue zone, assurez-vous que l’option **.NET Framework 4.5** est choisi dans la liste des versions du .NET Framework.  
  
5.  Choisissez le **bibliothèque de contrôles utilisateur WPF** modèle de projet, nommez le projet **ItemTemplateWizard**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **ItemTemplateWizard** projet à la solution.  
  
6.  Supprimer l’élément UserControl1 du projet.  
  
## <a name="configure-the-wizard-project"></a>Configurer le projet d’Assistant
 Avant de créer l’Assistant, vous devez ajouter une fenêtre Windows Presentation Foundation (WPF), un fichier de code et les références d’assembly au projet.  
  
#### <a name="to-configure-the-wizard-project"></a>Pour configurer le projet d’Assistant  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel à partir de la **ItemTemplateWizard** nœud de projet, puis choisissez **propriétés**.  
  
2.  Dans le **Concepteur de projet**, assurez-vous que le framework cible est défini sur .NET Framework 4.5.  
  
     Pour les projets Visual c#, vous pouvez définir cette valeur sur le **Application** onglet. Pour les projets Visual Basic, vous pouvez définir cette valeur sur le **compiler** onglet. Pour plus d’informations, consultez [Guide pratique pour cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
3.  Dans le **ItemTemplateWizard** de projet, ajoutez un **fenêtre (WPF)** élément au projet, puis nommez l’élément **WizardWindow**.  
  
4.  Ajoutez deux fichiers de code nommés CustomActionWizard et des chaînes.  
  
5.  Ouvrez le menu contextuel pour le **ItemTemplateWizard** de projet, puis choisissez **ajouter une référence**.  
  
6.  Dans le **Gestionnaire de références - ItemTemplateWizard** boîte de dialogue, sous le **assemblys** nœud, choisissez le **Extensions** nœud.  
  
7.  Sélectionnez les cases à cocher en regard des assemblys suivants, puis choisissez le **OK** bouton :  
  
    -   EnvDTE  
  
    -   Microsoft.VisualStudio.Shell.11.0  
  
    -   Microsoft.VisualStudio.TemplateWizardInterface  
  
8.  Dans **l’Explorateur de solutions**, dans le **références** dossier pour le projet ItemTemplateWizard, choisissez le **EnvDTE** référence.  
  
9. Dans le **propriétés** fenêtre, modifiez la valeur de la **incorporer les Types Interop** propriété **False**.  
  
## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Définir l’emplacement par défaut et les chaînes d’ID pour les actions personnalisées
 Chaque action personnalisée a un emplacement et un ID qui est spécifié dans le `GroupID` et `Location` les attributs de la `CustomAction` élément dans le *Elements.xml* fichier. Dans cette étape, vous définissez des chaînes valides pour ces attributs dans le projet ItemTemplateWizard. Lorsque vous terminez cette procédure pas à pas, ces chaînes sont écrites dans le *Elements.xml* fichier dans l’élément de projet d’Action personnalisée lorsque les utilisateurs de spécifier un emplacement et un ID de l’Assistant.  
  
 Par souci de simplicité, cet exemple prend en charge uniquement un sous-ensemble des ID et les emplacements par défaut disponibles. Pour obtenir la liste complète, consultez [par défaut des emplacements personnalisés Action et ID](http://go.microsoft.com/fwlink/?LinkId=181964).  
  
#### <a name="to-define-the-default-location-and-id-strings"></a>Pour définir l’emplacement par défaut et les chaînes d’ID
  
1.  Ouvrez.  
  
2.  Dans le **ItemTemplateWizard** du projet, remplacez le code dans le fichier de code de chaînes avec le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]  
  
## <a name="create-the-wizard-ui"></a>Créer l’interface utilisateur de l’Assistant
 Ajoutez le XAML pour définir l’interface utilisateur de l’Assistant et ajouter du code permettant de lier certains des contrôles dans l’Assistant pour les chaînes d’identification. L’Assistant que vous créez est similaire à l’Assistant intégré pour les projets SharePoint dans Visual Studio.  
  
#### <a name="to-create-the-wizard-ui"></a>Pour créer l’interface utilisateur de l’Assistant
  
1.  Dans le **ItemTemplateWizard** de projet, ouvrez le menu contextuel pour le **WizardWindow.xaml** de fichiers, puis choisissez **ouvrir** pour ouvrir la fenêtre dans le concepteur.  
  
2.  Dans la vue XAML, remplacez le XAML actuel par le XAML suivant. Le XAML définit une interface utilisateur qui comprend un titre, de contrôles permettant de spécifier le comportement de l’action personnalisée et les boutons de navigation en bas de la fenêtre.  
  
    > [!NOTE]  
    >  Votre projet aura des erreurs de compilation après avoir ajouté ce code. Ces erreurs disparaissent lorsque vous ajoutez du code dans les étapes ultérieures.  
  
     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]  
  
    > [!NOTE]  
    >  La fenêtre qui est créée dans ce XAML est dérivée de la <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe de base. Lorsque vous ajoutez une boîte de dialogue WPF personnalisée à Visual Studio, nous vous recommandons de dériver votre boîte de dialogue à partir de cette classe pour que la cohérence du style avec d’autres boîtes de dialogue dans Visual Studio et éviter les problèmes susceptibles de se produire avec les boîtes de dialogue modales. Pour plus d’informations, consultez [création et la gestion des boîtes de dialogue modales](/visualstudio/extensibility/creating-and-managing-modal-dialog-boxes).  
  
3.  Si vous développez un projet Visual Basic, supprimez le `ItemTemplateWizard` espace de noms à partir de la `WizardWindow` nom de classe dans le `x:Class` attribut de la `Window` élément. Cet élément est dans la première ligne de le XAML. Lorsque vous avez terminé, la première ligne doit ressembler au code suivant :  
  
    ```xml  
    <Window x:Class="WizardWindow"  
    ```  
  
4.  Dans le fichier code-behind pour le fichier WizardWindow.xaml, remplacez le code actuel par le code suivant.  
  
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]  
  
## <a name="implement-the-wizard"></a>Implémenter l’Assistant
 Définissez les fonctionnalités de l’Assistant en implémentant le <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.  
  
#### <a name="to-implement-the-wizard"></a>Pour implémenter l’Assistant  
  
1.  Dans le **ItemTemplateWizard** projet, ouvrez le **CustomActionWizard** fichier de code, puis remplacez le code en cours dans ce fichier par le code suivant :  
  
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]  
  
## <a name="checkpoint"></a>Point de contrôle  
 À ce stade dans la procédure pas à pas, l’intégralité du code pour l’Assistant est désormais dans le projet. Générez le projet pour vous assurer qu’il est compilé sans erreur.  
  
#### <a name="to-build-your-project"></a>Pour générer votre projet  
  
1.  Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.  
  
## <a name="associate-the-wizard-with-the-item-template"></a>L’Assistant association avec le modèle d’élément
 Maintenant que vous avez implémenté l’Assistant, vous devez l’associer avec le **Custom Action** modèle d’élément en trois étapes principales :  
  
1.  Signer l’assembly de l’Assistant avec un nom fort.  
  
2.  Obtenir la clé publique jeton pour l’assembly de l’Assistant.  
  
3.  Ajoutez une référence à l’assembly de l’Assistant dans le fichier .vstemplate pour le **Custom Action** modèle d’élément.  
  
#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Pour signer l’assembly de l’Assistant avec un nom fort  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel à partir de la **ItemTemplateWizard** nœud de projet, puis choisissez **propriétés**.  
  
2.  Sur le **signature** onglet, sélectionnez le **signer l’assembly** case à cocher.  
  
3.  Dans le **choisir un fichier de clé de nom fort** , choisissez  **\<nouveau... >**.  
  
4.  Dans le **créer une clé de nom fort** boîte de dialogue, entrez un nom, désactivez le **protéger mon fichier de clé avec un mot de passe** case à cocher, puis choisissez le **OK** bouton.  
  
5.  Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.  
  
#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Pour obtenir un jeton la clé publique pour l’assembly de l’Assistant  
  
1.  Dans une fenêtre d’invite de commandes Visual Studio, exécutez la commande suivante en remplaçant de la commande *PathToWizardAssembly* avec le chemin d’accès complet à l’assembly ItemTemplateWizard.dll créé pour le projet ItemTemplateWizard sur votre développement ordinateur.  
  
    ```xml  
    sn.exe -T PathToWizardAssembly  
    ```  
  
     Le jeton de clé publique pour le *ItemTemplateWizard.dll créé* assembly est écrite dans la fenêtre d’invite de commandes Visual Studio.  
  
2.  Ne fermez pas la fenêtre d’invite de commandes Visual Studio. Vous aurez besoin du jeton de clé publique pour terminer la procédure suivante.  
  
#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Pour ajouter une référence à l’assembly de l’Assistant dans le fichier .vstemplate  
  
1.  Dans **l’Explorateur de solutions**, développez le **ItemTemplate** nœud de projet, puis ouvrez le *ItemTemplate.vstemplate* fichier.  
  
2.  Vers la fin du fichier, ajoutez le code suivant `WizardExtension` élément entre les `</TemplateContent>` et `</VSTemplate>` balises. Remplacez le *YourToken* valeur de la `PublicKeyToken` attribut avec le jeton de clé publique que vous avez obtenue dans la procédure précédente.  
  
    ```xml  
    <WizardExtension>  
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>  
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>  
    </WizardExtension>  
    ```  
  
     Pour plus d’informations sur la `WizardExtension` élément, consultez [WizardExtension élément &#40;modèles Visual Studio&#41;](/visualstudio/extensibility/wizardextension-element-visual-studio-templates).  
  
3.  Enregistrez et fermez le fichier.  
  
## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Ajouter des paramètres remplaçables pour la *Elements.xml* fichier dans le modèle d’élément
 Ajoutez plusieurs paramètres remplaçables pour la *Elements.xml* fichier dans le projet ItemTemplate. Ces paramètres sont initialisés dans le `PopulateReplacementDictionary` méthode dans la `CustomActionWizard` classe que vous avez défini précédemment. Lorsqu’un utilisateur ajoute un élément de projet d’Action personnalisée à un projet, Visual Studio remplace automatiquement ces paramètres dans le *Elements.xml* fichier dans le nouvel élément de projet avec les valeurs qui ont été spécifiées dans l’Assistant.  
  
 Un paramètre remplaçable est un jeton qui commence et se termine par le caractère de signe dollar ($). En plus de définir vos propres paramètres remplaçables, vous pouvez utiliser des paramètres intégrés qui définit le système de projet SharePoint et l’initialise. Pour plus d’informations, consultez [paramètres remplaçables](../sharepoint/replaceable-parameters.md).  
  
#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Pour ajouter des paramètres remplaçables pour la *Elements.xml* fichier
  
1.  Dans le projet ItemTemplate, remplacez le contenu de la *Elements.xml* fichier avec le code XML suivant.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
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
  
     Le nouveau code XML modifie les valeurs de la `Id`, `GroupId`, `Location`, `Description`, et `Url` attributs aux paramètres remplaçables.  
  
2.  Enregistrez et fermez le fichier.  
  
## <a name="add-the-wizard-to-the-vsix-package"></a>Ajoutez l’Assistant au package VSIX
 Dans le fichier source.extension.vsixmanifest dans le projet VSIX, ajoutez une référence au projet d’Assistant afin qu’elle est déployée avec le package VSIX qui contient l’élément de projet.  
  
#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Pour ajouter l’Assistant au package VSIX  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel à partir de la **source.extension.vsixmanifest** de fichiers dans le projet ÉlémentProjetActionPersonnalisée, puis choisissez **ouvrir** pour ouvrir le fichier dans l’éditeur de manifeste.  
  
2.  Dans l’éditeur de manifeste, choisissez le **actifs** onglet, puis choisissez le **New** bouton.  
  
     Le **ajouter un nouveau composant** boîte de dialogue s’affiche.  
  
3.  Dans le **Type** , choisissez **Microsoft.VisualStudio.Assembly**.  
  
4.  Dans le **Source** , choisissez **un projet dans la solution actuelle**.  
  
5.  Dans le **projet** , choisissez **ItemTemplateWizard**, puis choisissez le **OK** bouton.  
  
6.  Dans la barre de menus, choisissez **Build** > **générer la Solution**, puis assurez-vous que la solution est compilée sans erreurs.  
  
## <a name="test-the-wizard"></a>L’Assistant de test
 Vous êtes maintenant prêt à tester l’Assistant. Tout d’abord, commencez le débogage de la solution CustomActionProjectItem dans l’instance expérimentale de Visual Studio. Testez ensuite l’Assistant pour l’élément de projet d’Action personnalisée dans un projet SharePoint dans l’instance expérimentale de Visual Studio. Enfin, générez et exécutez le projet SharePoint pour vérifier que l’action personnalisée fonctionne comme prévu.  
  
#### <a name="to-start-to-debug-the-solution"></a>Pour commencer à déboguer la solution  
  
1.  Redémarrez Visual Studio en tant qu’administrateur et ouvrez la solution ÉlémentProjetActionPersonnalisée.  
  
2.  Dans le projet ItemTemplateWizard, ouvrez le fichier de code CustomActionWizard, puis ajoutez un point d’arrêt à la première ligne de code dans le `RunStarted` (méthode).  
  
3.  Dans la barre de menus, choisissez **déboguer** > **Exceptions**.  
  
4.  Dans le **Exceptions** boîte de dialogue zone, assurez-vous que le **levé** et **User-unhandled** cases à cocher pour **Exceptions Common Language Runtime**sont effacées, puis choisissez le **OK** bouton.  
  
5.  Démarrer le débogage en choisissant le **F5** clé, ou, dans la barre de menus, choisissez **déboguer** > **démarrer le débogage**.  
  
     Visual Studio installe l’extension %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Item\1.0 de projet d’Action et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.  
  
#### <a name="to-test-the-wizard-in-visual-studio"></a>Pour tester l’Assistant dans Visual Studio  
  
1.  Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **fichier** > **New** > **projet**.  
  
2.  Développez le **Visual C#** ou **Visual Basic** nœud (selon le langage qui prend en charge de votre modèle d’élément), développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
3.  Dans la liste des modèles de projet, choisissez **projet SharePoint 2010**, nommez le projet **CustomActionWizardTest**, puis choisissez le **OK** bouton.  
  
4.  Dans le **Assistant Personnalisation de SharePoint**, entrez l’URL du site que vous souhaitez utiliser pour le débogage, puis choisissez le **Terminer** bouton.  
  
5.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet, choisissez **ajouter**, puis choisissez **un nouvel élément**.  
  
6.  Dans le **ajouter un nouvel élément - CustomItemWizardTest** boîte de dialogue, développez le **SharePoint** nœud, puis développez le **2010** nœud.  
  
7.  Dans la liste des éléments de projet, choisissez le **Custom Action** d’élément, puis choisissez le **ajouter** bouton.  
  
8.  Vérifiez que le code dans l’autre instance de Visual Studio s’arrête au point d’arrêt que vous avez défini précédemment dans le `RunStarted` (méthode).  
  
9. Continuer à déboguer le projet en choisissant le **F5** clé ou, dans la barre de menus, choisissez **déboguer** > **continuer**.  
  
     L’Assistant de personnalisation de SharePoint s’affiche.  
  
10. Sous **emplacement**, choisissez le **modifiez liste** case d’option.  
  
11. Dans le **ID de groupe** , choisissez **Communications**.  
  
12. Dans le **titre** , entrez **centre de développement SharePoint**.  
  
13. Dans le **Description** , entrez **ouvre le site Web Centre de développement SharePoint**.  
  
14. Dans le **URL** , entrez **http://msdn.microsoft.com/sharepoint/default.aspx**, puis choisissez le **Terminer** bouton.  
  
     Visual Studio ajoute un élément nommé **CustomAction1** à votre projet et l’ouvre le *Elements.xml* fichier dans l’éditeur. Vérifiez que *Elements.xml* contient les valeurs que vous avez spécifié dans l’Assistant.  
  
#### <a name="to-test-the-custom-action-in-sharepoint"></a>Pour tester l’action personnalisée dans SharePoint  
  
1.  Dans l’instance expérimentale de Visual Studio, choisissez le **F5** clé ou, dans la barre de menus, choisissez **déboguer** > **démarrer le débogage**.  
  
     L’action personnalisée est empaquetée et déployée sur le site SharePoint spécifié par le **URL du Site** propriété du projet et le navigateur web s’ouvre à la page par défaut de ce site.  
  
    > [!NOTE]  
    >  Si le **le débogage de Script est désactivé** boîte de dialogue s’affiche, choisissez le **Oui** bouton.  
  
2.  Dans la zone de listes du site SharePoint, choisissez le **tâches** lien.  
  
     Le **tâches - toutes les tâches** page s’affiche.  
  
3.  Sur le **outils de liste** onglet du ruban, choisissez le **liste** onglet, puis, dans le **paramètres** de groupe, choisissez **liste paramètres**.  
  
     Le **liste paramètres** page s’affiche.  
  
4.  Sous le **Communications** titre vers le haut de la page, choisissez le **centre de développement SharePoint** lier, vérifiez que le navigateur ouvre le site Web http://msdn.microsoft.com/sharepoint/default.aspx, puis fermez le navigateur.  
  
## <a name="cleaning-up-the-development-computer"></a>Nettoyage de l’ordinateur de développement
 Une fois que vous avez terminé le test de l’élément de projet, supprimez le modèle d’élément de projet à partir de l’instance expérimentale de Visual Studio.  
  
#### <a name="to-clean-up-the-development-computer"></a>Pour nettoyer l’ordinateur de développement  
  
1.  Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **outils** > **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s’ouvre.  
  
2.  Dans la liste des extensions, choisissez le **élément de projet d’Action personnalisée** extension, puis choisissez le **désinstallation** bouton.  
  
3.  Dans la boîte de dialogue qui s’affiche, choisissez le **Oui** pour confirmer que vous souhaitez désinstaller l’extension, puis choisissez le **redémarrer maintenant** bouton pour terminer la désinstallation.  
  
4.  Fermez les deux instances de Visual Studio (l’instance expérimentale et l’instance de Visual Studio dans laquelle la solution ÉlémentProjetActionPersonnalisée est ouverte).  
  
## <a name="see-also"></a>Voir aussi
 [Procédure pas à pas : Créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Définir les types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Créer des modèles d’élément et les modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Référence du schéma de modèle Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)   
 [Comment : utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)   
 [ID et emplacements d’Action personnalisée par défaut](http://go.microsoft.com/fwlink/?LinkId=181964)  
  
