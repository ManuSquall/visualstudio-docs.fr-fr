---
title: Créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 2
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
ms.openlocfilehash: c96546f85b21ee0ca8a559059a16158b743cb915
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016105"
---
# <a name="walkthrough-create-a-custom-action-project-item-with-an-item-template-part-2"></a>Procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 2
  Une fois que vous avez défini un type personnalisé d’élément de projet SharePoint et que vous l’avez associé à un modèle d’élément dans Visual Studio, vous pouvez également fournir un Assistant pour le modèle. Vous pouvez utiliser l’Assistant pour collecter des informations auprès des utilisateurs lorsqu’ils utilisent votre modèle pour ajouter une nouvelle instance de l’élément de projet à un projet. Les informations que vous recueillez peuvent être utilisées pour initialiser l’élément de projet.

 Dans cette procédure pas à pas, vous allez ajouter un assistant à l’élément de projet d’action personnalisée qui est illustré dans [procédure pas à pas : créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Quand un utilisateur ajoute un élément de projet d’action personnalisée à un projet SharePoint, l’Assistant recueille des informations sur l’action personnalisée (par exemple son emplacement et l’URL vers laquelle naviguer lorsqu’un utilisateur final le choisit) et ajoute ces informations au fichier *Elements.xml* dans le nouvel élément de projet.

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’un Assistant pour un type d’élément de projet SharePoint personnalisé associé à un modèle d’élément.

- Définition d’une interface utilisateur d’Assistant personnalisée qui ressemble aux Assistants intégrés pour les éléments de projet SharePoint dans Visual Studio.

- L’utilisation de paramètres remplaçables pour initialiser les fichiers projet SharePoint avec les données que vous collectez dans l’Assistant.

- Débogage et test de l’Assistant.

> [!NOTE]
> Vous pouvez télécharger un exemple à partir de [GitHub](https://github.com/SharePoint/PnP/tree/master/Samples/Workflow.Activities) qui montre comment créer des activités personnalisées pour un flux de travail.

## <a name="prerequisites"></a>Prérequis
 Pour effectuer cette procédure pas à pas, vous devez d’abord créer la solution CustomActionProjectItem en effectuant la [procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Pour effectuer cette procédure pas à pas, vous avez également besoin des composants suivants sur l’ordinateur de développement :

- Éditions prises en charge de Windows, SharePoint et Visual Studio.

- Le kit de développement logiciel (SDK) Visual Studio. Cette procédure pas à pas utilise le modèle de **projet VSIX** dans le kit de développement logiciel (SDK) pour créer un package VSIX afin de déployer l’élément de projet. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer la procédure pas à pas :

- Assistants pour les modèles de projet et d’élément dans Visual Studio. Pour plus d’informations, consultez [Comment : utiliser des assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md) et l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.

- Actions personnalisées dans SharePoint. Pour plus d’informations, consultez [action personnalisée](/previous-versions/office/developer/sharepoint-2010/ms458635(v=office.14)).

## <a name="create-the-wizard-project"></a>Créer le projet d’Assistant
 Pour effectuer cette procédure pas à pas, vous devez ajouter un projet à la solution CustomActionProjectItem que vous avez créée dans [procédure pas à pas : créer un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md). Vous allez implémenter l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface et définir l’interface utilisateur de l’Assistant dans ce projet.

#### <a name="to-create-the-wizard-project"></a>Pour créer le projet de l’Assistant

1. Dans Visual Studio, ouvrez la solution CustomActionProjectItem

2. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud solution, choisissez **Ajouter**, puis **nouveau projet**.

3. Dans la boîte de dialogue **nouveau projet** , développez les nœuds **Visual C#** ou **Visual Basic** , puis choisissez le nœud **Windows** .

4. En haut de la boîte de dialogue **nouveau projet** , assurez-vous que **.NET Framework 4,5** est choisi dans la liste des versions du .NET Framework.

5. Choisissez le modèle de projet **bibliothèque de contrôles utilisateur WPF** , nommez le projet **ItemTemplateWizard**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **ItemTemplateWizard** à la solution.

6. Supprimez l’élément UserControl1 du projet.

## <a name="configure-the-wizard-project"></a>Configurer le projet de l’Assistant
 Avant de créer l’Assistant, vous devez ajouter une fenêtre Windows Presentation Foundation (WPF), un fichier de code et des références d’assembly au projet.

#### <a name="to-configure-the-wizard-project"></a>Pour configurer le projet de l’Assistant

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **ItemTemplateWizard** , puis choisissez **Propriétés**.

2. Dans le **Concepteur de projet**, assurez-vous que la version cible de .NET Framework est définie sur .NET Framework 4,5.

     Pour les projets Visual C#, vous pouvez définir cette valeur sous l’onglet **application** . Pour les projets Visual Basic, vous pouvez définir cette valeur sous l’onglet **compiler** . Pour plus d’informations, consultez [Comment : cibler une version du .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

3. Dans le projet **ItemTemplateWizard** , ajoutez un élément de **fenêtre (WPF)** au projet, puis nommez l’élément **WizardWindow**.

4. Ajoutez deux fichiers de code nommés CustomActionWizard et Strings.

5. Ouvrez le menu contextuel du projet **ItemTemplateWizard** , puis choisissez **Ajouter une référence**.

6. Dans la boîte de dialogue **Gestionnaire de références-ItemTemplateWizard** , sous le nœud **assemblys** , choisissez le nœud **Extensions** .

7. Activez les cases à cocher en regard des assemblys suivants, puis choisissez le bouton **OK** :

    - EnvDTE

    - Microsoft. VisualStudio. Shell. 11.0

    - Microsoft.VisualStudio.TemplateWizardInterface

8. Dans **Explorateur de solutions**, dans le dossier **références** du projet ItemTemplateWizard, choisissez la référence **EnvDTE** .

9. Dans la fenêtre **Propriétés** , remplacez la valeur de la propriété **incorporer les types Interop** par **false**.

## <a name="define-the-default-location-and-id-strings-for-custom-actions"></a>Définir l’emplacement et les chaînes d’ID par défaut pour les actions personnalisées
 Chaque action personnalisée a un emplacement et un ID spécifiés dans les `GroupID` `Location` attributs et de l' `CustomAction` élément dans le fichier *Elements.xml* . Au cours de cette étape, vous allez définir certaines des chaînes valides pour ces attributs dans le projet ItemTemplateWizard. Lorsque vous effectuez cette procédure pas à pas, ces chaînes sont écrites dans le fichier *Elements.xml* dans l’élément de projet d’action personnalisée lorsque les utilisateurs spécifient un emplacement et un ID dans l’Assistant.

 Par souci de simplicité, cet exemple ne prend en charge qu’un sous-ensemble des emplacements et des ID par défaut disponibles. Pour obtenir une liste complète, consultez [emplacements et ID des actions personnalisées par défaut](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14)).

#### <a name="to-define-the-default-location-and-id-strings"></a>Pour définir l’emplacement et les chaînes d’ID par défaut

1. afficher.

2. Dans le projet **ItemTemplateWizard** , remplacez le code dans le fichier de code Strings par le code suivant.

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/strings.cs#6)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#6](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/strings.vb#6)]

## <a name="create-the-wizard-ui"></a>Créer l’interface utilisateur de l’Assistant
 Ajoutez du code XAML pour définir l’interface utilisateur de l’Assistant et ajoutez du code pour lier certains des contrôles de l’Assistant aux chaînes d’ID. L’Assistant que vous créez ressemble à l’Assistant intégré pour les projets SharePoint dans Visual Studio.

#### <a name="to-create-the-wizard-ui"></a>Pour créer l’interface utilisateur de l’Assistant

1. Dans le projet **ItemTemplateWizard** , ouvrez le menu contextuel du fichier **WizardWindow. Xaml** , puis choisissez **ouvrir** pour ouvrir la fenêtre dans le concepteur.

2. Dans la vue XAML, remplacez le code XAML actuel par le code XAML suivant. Le code XAML définit une interface utilisateur qui comprend un en-tête, des contrôles pour la spécification du comportement de l’action personnalisée et des boutons de navigation en bas de la fenêtre.

    > [!NOTE]
    > Votre projet comportera des erreurs de compilation après l’ajout de ce code. Ces erreurs disparaissent lorsque vous ajoutez du code dans les étapes ultérieures.

     [!code-xml[SPExtensibility.ProjectItem.CustomAction#9](../sharepoint/codesnippet/Xaml/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml#9)]

    > [!NOTE]
    > La fenêtre créée dans ce XAML est dérivée de la <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe de base. Quand vous ajoutez une boîte de dialogue WPF personnalisée à Visual Studio, nous vous recommandons de dériver votre boîte de dialogue à partir de cette classe de manière à ce qu’elle ait un style cohérent avec d’autres boîtes de dialogue dans Visual Studio et pour éviter des problèmes qui pourraient se produire avec des boîtes de dialogue modales. Pour plus d’informations, consultez [création et gestion de boîtes de dialogue modales](../extensibility/creating-and-managing-modal-dialog-boxes.md).

3. Si vous développez un projet Visual Basic, supprimez l' `ItemTemplateWizard` espace de noms du `WizardWindow` nom de classe dans l' `x:Class` attribut de l' `Window` élément. Cet élément se trouve dans la première ligne du code XAML. Lorsque vous avez terminé, la première ligne doit ressembler au code suivant :

    ```xml
    <Window x:Class="WizardWindow"
    ```

4. Dans le fichier code-behind du fichier WizardWindow. xaml, remplacez le code actuel par le code suivant.

     [!code-vb[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.vb#7)]
     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#7](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/wizardwindow.xaml.cs#7)]

## <a name="implement-the-wizard"></a>Implémenter l’Assistant
 Définissez les fonctionnalités de l’Assistant en implémentant l' <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface.

#### <a name="to-implement-the-wizard"></a>Pour implémenter l’Assistant

1. Dans le projet **ItemTemplateWizard** , ouvrez le fichier de code **CustomActionWizard** , puis remplacez le code actuel dans ce fichier par le code suivant :

     [!code-csharp[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/CSharp/customactionprojectitem/itemtemplatewizard/customactionwizard.cs#8)]
     [!code-vb[SPExtensibility.ProjectItem.CustomAction#8](../sharepoint/codesnippet/VisualBasic/customactionprojectitem/itemtemplatewizard/customactionwizard.vb#8)]

## <a name="checkpoint"></a>Point de contrôle
 À ce stade de la procédure pas à pas, tout le code de l’Assistant se trouve maintenant dans le projet. Générez le projet pour vous assurer qu’il se compile sans erreur.

#### <a name="to-build-your-project"></a>Pour générer votre projet

1. Dans la barre de menus, choisissez **générer**  >  **générer la solution**.

## <a name="associate-the-wizard-with-the-item-template"></a>Associer l’Assistant au modèle d’élément
 Maintenant que vous avez implémenté l’Assistant, vous devez l’associer au modèle d’élément d' **action personnalisé** en effectuant trois étapes principales :

1. Signez l’assembly de l’Assistant avec un nom fort.

2. Obtient le jeton de clé publique pour l’assembly de l’Assistant.

3. Ajoutez une référence à l’assembly de l’Assistant dans le fichier. vstemplate du modèle d’élément d' **action personnalisé** .

#### <a name="to-sign-the-wizard-assembly-with-a-strong-name"></a>Pour signer l’assembly de l’Assistant avec un nom fort

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **ItemTemplateWizard** , puis choisissez **Propriétés**.

2. Sous l'onglet **Signature**, activez la case à cocher **Signer l'assembly**.

3. Dans la liste **choisir un fichier de clé de nom fort** , choisissez **\<New...>** .

4. Dans la boîte de dialogue **créer une clé de nom fort** , entrez un nom, désactivez la case à cocher **protéger le fichier de clé par un mot de passe** , puis choisissez le bouton **OK** .

5. Dans la barre de menus, choisissez **générer**  >  **générer la solution**.

#### <a name="to-get-the-public-key-token-for-the-wizard-assembly"></a>Pour obtenir le jeton de clé publique de l’assembly de l’Assistant

1. Dans une fenêtre d’invite de commandes Visual Studio, exécutez la commande suivante, en remplaçant *PathToWizardAssembly* par le chemin d’accès complet à l’assembly ItemTemplateWizard.dll généré pour le projet ItemTemplateWizard sur votre ordinateur de développement.

    ```xml
    sn.exe -T PathToWizardAssembly
    ```

     Le jeton de clé publique de l’assembly *ItemTemplateWizard.dll* est écrit dans la fenêtre d’invite de commandes de Visual Studio.

2. Laissez la fenêtre d’invite de commandes de Visual Studio ouverte. Vous aurez besoin du jeton de clé publique pour effectuer la procédure suivante.

#### <a name="to-add-a-reference-to-the-wizard-assembly-in-the-vstemplate-file"></a>Pour ajouter une référence à l’assembly de l’Assistant dans le fichier. vstemplate

1. Dans **Explorateur de solutions**, développez le nœud de projet **ItemTemplate** , puis ouvrez le fichier *ItemTemplate. vstemplate* .

2. Près de la fin du fichier, ajoutez l' `WizardExtension` élément suivant entre les `</TemplateContent>` `</VSTemplate>` balises et. Remplacez la valeur *YourToken* de l' `PublicKeyToken` attribut par le jeton de clé publique que vous avez obtenu dans la procédure précédente.

    ```xml
    <WizardExtension>
      <Assembly>ItemTemplateWizard, Version=1.0.0.0, Culture=neutral, PublicKeyToken=YourToken</Assembly>
      <FullClassName>ItemTemplateWizard.CustomActionWizard</FullClassName>
    </WizardExtension>
    ```

     Pour plus d’informations sur l' `WizardExtension` élément, consultez l' [élément WizardExtension &#40;les modèles Visual Studio&#41;](../extensibility/wizardextension-element-visual-studio-templates.md).

3. Enregistrez et fermez le fichier.

## <a name="add-replaceable-parameters-to-the-elementsxml-file-in-the-item-template"></a>Ajouter des paramètres remplaçables au fichier *Elements.xml* dans le modèle d’élément
 Ajoutez plusieurs paramètres remplaçables au fichier *Elements.xml* dans le projet ItemTemplate. Ces paramètres sont initialisés dans la `PopulateReplacementDictionary` méthode de la `CustomActionWizard` classe que vous avez définie précédemment. Quand un utilisateur ajoute un élément de projet d’action personnalisée à un projet, Visual Studio remplace automatiquement ces paramètres dans le fichier *Elements.xml* dans le nouvel élément de projet par les valeurs qu’ils ont spécifiées dans l’Assistant.

 Un paramètre remplaçable est un jeton qui commence et se termine par le caractère dollar ($). Outre la définition de vos propres paramètres remplaçables, vous pouvez utiliser des paramètres prédéfinis que le système de projet SharePoint définit et initialise. Pour plus d’informations, consultez [paramètres remplaçables](../sharepoint/replaceable-parameters.md).

#### <a name="to-add-replaceable-parameters-to-the-elementsxml-file"></a>Pour ajouter des paramètres remplaçables au fichier *Elements.xml*

1. Dans le projet ItemTemplate, remplacez le contenu du fichier *Elements.xml* par le code XML suivant.

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

     Le nouveau code XML modifie les valeurs des `Id` `GroupId` attributs,,, `Location` `Description` et `Url` en paramètres remplaçables.

2. Enregistrez et fermez le fichier.

## <a name="add-the-wizard-to-the-vsix-package"></a>Ajouter l’Assistant au package VSIX
 Dans le fichier source. extension. vsixmanifest du projet VSIX, ajoutez une référence au projet d’Assistant afin qu’il soit déployé avec le package VSIX qui contient l’élément de projet.

#### <a name="to-add-the-wizard-to-the-vsix-package"></a>Pour ajouter l’Assistant au package VSIX

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel à partir du fichier **source. extension. vsixmanifest** dans le projet CustomActionProjectItem, puis choisissez **ouvrir** pour ouvrir le fichier dans l’éditeur de manifeste.

2. Dans l’éditeur de manifeste, choisissez l’onglet **ressources** , puis cliquez sur le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’affiche.

3. Dans la liste **type** , choisissez **Microsoft. VisualStudio. assembly**.

4. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

5. Dans la liste **projet** , choisissez **ItemTemplateWizard**, puis cliquez sur le bouton **OK** .

6. Dans la barre de menus, choisissez **générer**  >  **générer la solution**, puis assurez-vous que la solution est compilée sans erreur.

## <a name="test-the-wizard"></a>Tester l’Assistant
 Vous êtes maintenant prêt à tester l’Assistant. Tout d’abord, commencez par déboguer la solution CustomActionProjectItem dans l’instance expérimentale de Visual Studio. Ensuite, testez l’Assistant pour l’élément de projet d’action personnalisée dans un projet SharePoint de l’instance expérimentale de Visual Studio. Enfin, générez et exécutez le projet SharePoint pour vérifier que l’action personnalisée fonctionne comme prévu.

#### <a name="to-start-to-debug-the-solution"></a>Pour commencer à déboguer la solution

1. Redémarrez Visual Studio avec les informations d’identification d’administration, puis ouvrez la solution CustomActionProjectItem.

2. Dans le projet ItemTemplateWizard, ouvrez le fichier de code CustomActionWizard, puis ajoutez un point d’arrêt à la première ligne de code dans la `RunStarted` méthode.

3. Dans la barre de menus, choisissez **Déboguer**les  >  **exceptions**.

4. Dans la boîte de dialogue **exceptions** , assurez-vous que les cases à cocher **levé** et **non géré** par l’utilisateur pour les **exceptions du Common Language Runtime** sont désactivées, puis choisissez le bouton **OK** .

5. Démarrez le débogage en choisissant la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**  >  **Démarrer le débogage**.

     Visual Studio installe l’extension dans le projet d’action%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Item\1.0 et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.

#### <a name="to-test-the-wizard-in-visual-studio"></a>Pour tester l’Assistant dans Visual Studio

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

2. Développez le nœud **Visual C#** ou **Visual Basic** (selon la langue prise en charge par votre modèle d’élément), développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

3. Dans la liste des modèles de projet, choisissez **projet SharePoint 2010**, nommez le projet **CustomActionWizardTest**, puis choisissez le bouton **OK** .

4. Dans l' **Assistant Personnalisation de SharePoint**, entrez l’URL du site que vous souhaitez utiliser pour le débogage, puis choisissez le bouton **Terminer** .

5. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet, choisissez **Ajouter**, puis **nouvel élément**.

6. Dans la boîte de dialogue **Ajouter un nouvel élément-CustomItemWizardTest** , développez le nœud **SharePoint** , puis développez le nœud **2010** .

7. Dans la liste des éléments de projet, choisissez l’élément d' **action personnalisée** , puis cliquez sur le bouton **Ajouter** .

8. Vérifiez que le code de l’autre instance de Visual Studio s’arrête sur le point d’arrêt que vous avez défini précédemment dans la `RunStarted` méthode.

9. Continuez à déboguer le projet en choisissant la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**  >  **Continuer**.

     L'Assistant Personnalisation de SharePoint apparaît.

10. Sous **emplacement**, choisissez la case d’option **modifier la liste** .

11. Dans la liste **ID de groupe** , choisissez **communications**.

12. Dans la zone **titre** , entrez **Centre de développement SharePoint**.

13. Dans la zone  **Description** , entrez **ouvre le site Web du centre de développement SharePoint**.

14. Dans la zone **URL** , entrez **https://docs.microsoft.com/sharepoint/dev/** , puis choisissez le bouton **Terminer** .

     Visual Studio ajoute un élément nommé **CustomAction1** à votre projet et ouvre le fichier *Elements.xml* dans l’éditeur. Vérifiez que *Elements.xml* contient les valeurs que vous avez spécifiées dans l’Assistant.

#### <a name="to-test-the-custom-action-in-sharepoint"></a>Pour tester l’action personnalisée dans SharePoint

1. Dans l’instance expérimentale de Visual Studio, choisissez la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**  >  **Démarrer le débogage**.

     L’action personnalisée est empaquetée et déployée sur le site SharePoint spécifié par la propriété **URL du site** du projet, et le navigateur Web s’ouvre sur la page par défaut de ce site.

    > [!NOTE]
    > Si la boîte de dialogue **débogage de script désactivé** s’affiche, choisissez le bouton **Oui** .

2. Dans la zone listes du site SharePoint, choisissez le lien **tâches** .

     La page **tâches-toutes les tâches** s’affiche.

3. Sous l’onglet **outils de liste** du ruban, choisissez l’onglet **liste** , puis, dans le groupe **paramètres** , choisissez Paramètres de la **liste**.

     La page Paramètres de la **liste** s’affiche.

4. Sous le titre **communications** en haut de la page, choisissez le lien **Centre de développement SharePoint** , vérifiez que le navigateur ouvre le site Web https://docs.microsoft.com/sharepoint/dev/ , puis fermez le navigateur.

## <a name="cleaning-up-the-development-computer"></a>Nettoyage de l’ordinateur de développement
 Une fois que vous avez fini de tester l’élément de projet, supprimez le modèle d’élément de projet de l’instance expérimentale de Visual Studio.

#### <a name="to-clean-up-the-development-computer"></a>Pour nettoyer l’ordinateur de développement

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **Outils**  >  **extensions et mises à jour**.

     La boîte de dialogue **Extensions et mises à jour** s’ouvre.

2. Dans la liste des extensions, choisissez l’extension d' **élément de projet action personnalisée** , puis cliquez sur le bouton **désinstaller** .

3. Dans la boîte de dialogue qui s’affiche, choisissez le bouton **Oui** pour confirmer que vous souhaitez désinstaller l’extension, puis cliquez sur le bouton **redémarrer maintenant** pour terminer la désinstallation.

4. Fermez les deux instances de Visual Studio (l’instance expérimentale et l’instance de Visual Studio dans laquelle la solution CustomActionProjectItem est ouverte).

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : création d’un élément de projet d’action personnalisé avec un modèle d’élément, partie 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Définir des types d’éléments de projet SharePoint personnalisés](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Créer des modèles d’élément et des modèles de projet pour les éléments de projet SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Référence du schéma de modèle Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Comment : utiliser des Assistants avec des modèles de projet](../extensibility/how-to-use-wizards-with-project-templates.md)
- [ID et emplacements des actions personnalisées par défaut](/previous-versions/office/developer/sharepoint-2010/bb802730(v=office.14))
