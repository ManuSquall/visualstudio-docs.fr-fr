---
title: 'Procédure pas à pas : création d’une extension de projet SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5df10e2da9e6b4c31894dce0669e9aa0e580b92f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015081"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Procédure pas à pas : créer une extension de projet SharePoint
  Cette procédure pas à pas illustre la création d’une extension pour les projets SharePoint. Vous pouvez utiliser une extension de projet pour répondre aux événements au niveau du projet, par exemple lors de l’ajout, de la suppression ou du changement de nom d’un projet. Vous pouvez également ajouter des propriétés personnalisées ou répondre en cas de modification d’une valeur de propriété. Contrairement aux extensions d’élément de projet, les extensions de projet ne peuvent pas être associées à un type de projet SharePoint particulier. Lorsque vous créez une extension de projet, l’extension est chargée lorsque l’un des types de projet SharePoint est ouvert dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Dans cette procédure pas à pas, vous allez créer une propriété booléenne personnalisée qui est ajoutée à un projet SharePoint créé dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Quand la valeur est **true**, la nouvelle propriété ajoute, ou mappe, un dossier de ressources images à votre projet. Quand la valeur est **false**, le dossier images est supprimé, s’il existe. Pour plus d’informations, consultez [Comment : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md).

 Cette procédure pas à pas décrit les tâches suivantes :

- Création [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] d’une extension pour les projets SharePoint qui effectue les opérations suivantes :

  - Ajoute une propriété de projet personnalisée à la Fenêtre Propriétés. La propriété s’applique à n’importe quel projet SharePoint.

  - Utilise le modèle objet de projet SharePoint pour ajouter un dossier mappé à un projet.

  - Utilise le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modèle objet Automation (DTE) pour supprimer un dossier mappé du projet.

- Génération d’un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’extension (VSIX) pour déployer l’assembly d’extension de la propriété du projet.

- Débogage et test de la propriété de projet.

## <a name="prerequisites"></a>Prérequis
 Pour effectuer cette procédure pas à pas, vous avez besoin des composants suivants sur l’ordinateur de développement :

- Éditions prises en charge de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] , SharePoint et [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- L’[!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]opérateur Cette procédure pas à pas utilise le modèle de **projet VSIX** dans le [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] pour créer un package VSIX pour déployer l’extension de propriété de projet. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez créer deux projets :

- Projet VSIX pour créer le package VSIX pour déployer l’extension de projet.

- Projet de bibliothèque de classes qui implémente l’extension de projet.

  Démarrez la procédure pas à pas en créant les projets.

#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

3. Dans la boîte de dialogue **nouveau projet** , développez les nœuds **Visual C#** ou **Visual Basic** , puis choisissez le nœud **extensibilité** .

    > [!NOTE]
    > Ce nœud est disponible uniquement si vous installez le kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez la section conditions préalables, plus haut dans cette rubrique.

4. En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework, puis choisissez le modèle de **projet VSIX** .

5. Dans la zone **nom** , entrez **ProjectExtensionPackage**, puis choisissez le bouton **OK** .

     Le projet **ProjectExtensionPackage** s’affiche dans **Explorateur de solutions**.

#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud solution, choisissez **Ajouter**, puis **nouveau projet**.

2. Dans la boîte de dialogue **nouveau projet** , développez les nœuds **Visual C#** ou **Visual Basic** , puis choisissez **Windows**.

3. En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework, puis choisissez le modèle de projet **bibliothèque de classes** .

4. Dans la zone **nom** , entrez **ProjectExtension**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **ProjectExtension** à la solution et ouvre le fichier de code Class1 par défaut.

5. Supprimez le fichier de code Class1 du projet.

## <a name="configure-the-project"></a>Configurer le projet
 Avant d’écrire du code pour créer l’extension de projet, ajoutez les fichiers de code et les références d’assembly au projet d’extension.

#### <a name="to-configure-the-project"></a>Pour configurer le projet

1. Ajoutez un fichier de code nommé **CustomProperty** au projet ProjectExtension.

2. Ouvrez le menu contextuel du projet **ProjectExtension** , puis choisissez **Ajouter une référence**.

3. Dans la boîte de dialogue **Gestionnaire de références-CustomProperty** , choisissez le nœud **Framework** , puis activez la case à cocher en regard des assemblys System. ComponentModel. composition et System. Windows. Forms.

4. Choisissez le nœud **Extensions** , activez la case à cocher en regard des assemblys Microsoft. VisualStudio. SharePoint et EnvDTE, puis choisissez le bouton **OK** .

5. Dans **Explorateur de solutions**, sous le dossier **références** du projet **ProjectExtension** , choisissez **EnvDTE**.

6. Dans la fenêtre **Propriétés** , affectez la **valeur false**à la propriété **incorporer les types Interop** .

## <a name="define-the-new-sharepoint-project-property"></a>Définir la propriété de projet SharePoint
 Créez une classe qui définit l’extension de projet et le comportement de la nouvelle propriété de projet. Pour définir la nouvelle extension de projet, la classe implémente l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interface. Implémentez cette interface chaque fois que vous souhaitez définir une extension pour un projet SharePoint. Ajoutez également <xref:System.ComponentModel.Composition.ExportAttribute> à la classe. Cet attribut permet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] à de découvrir et de charger votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implémentation. Transmettez le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> type au constructeur de l’attribut.

#### <a name="to-define-the-new-sharepoint-project-property"></a>Pour définir la nouvelle propriété de projet SharePoint

1. Collez le code suivant dans le fichier de code CustomProperty.

     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]

## <a name="build-the-solution"></a>Générez la solution.
 Ensuite, générez la solution pour vous assurer qu’elle est compilée sans erreur.

#### <a name="to-build-the-solution"></a>Pour générer la solution

1. Dans la barre de menus, choisissez **générer**  >  **générer la solution**.

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Créer un package VSIX pour déployer l’extension de propriété de projet
 Pour déployer l’extension de projet, utilisez le projet VSIX dans votre solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source. extension. vsixmanifest qui est inclus dans le projet VSIX. Ensuite, créez le package VSIX en générant la solution.

#### <a name="to-configure-and-create-the-vsix-package"></a>Pour configurer et créer le package VSIX

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du fichier source. extension. vsixmanifest, puis choisissez le bouton **ouvrir** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le fichier dans le concepteur de manifeste. Les informations qui s’affichent sous l’onglet **métadonnées** apparaissent également dans **extensions et mises à jour**. Tous les packages VSIX requièrent le fichier extension. vsixmanifest. Pour plus d’informations sur ce fichier, consultez [Référence du schéma d’extension VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. Dans la zone **nom du produit** , entrez propriété de **projet personnalisée**.

3. Dans la zone **auteur** , entrez **contoso**.

4. Dans la zone **Description** , entrez **une propriété de projet SharePoint personnalisée qui bascule le mappage du dossier de ressources images sur le projet**.

5. Sélectionnez l’onglet **ressources** , puis cliquez sur le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’affiche.

6. Dans la liste **type** , choisissez **Microsoft. VisualStudio. MEFComponent**.

    > [!NOTE]
    > Cette valeur correspond à l' `MEFComponent` élément dans le fichier extension. vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MefComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Dans la liste **source** , sélectionnez la case d’option **un projet dans la solution actuelle** .

8. Dans la liste **projet** , choisissez **ProjectExtension**.

     Cette valeur identifie le nom de l’assembly que vous générez dans le projet.

9. Choisissez **OK** pour fermer la boîte de dialogue **Ajouter un nouvel élément** multimédia.

10. Dans la barre de menus, choisissez **fichier**  >  **enregistrer tout** lorsque vous avez terminé, puis fermez le concepteur de manifeste.

11. Dans la barre de menus, choisissez **générer**  >  **générer la solution**, puis assurez-vous que le projet se compile sans erreur.

12. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **ProjectExtensionPackage** , puis choisissez le bouton **ouvrir le dossier dans l’Explorateur de fichiers** .

13. Dans l' **Explorateur de fichiers**, ouvrez le dossier de sortie de la génération pour le projet ProjectExtensionPackage, puis vérifiez que le dossier contient un fichier nommé ProjectExtensionPackage. vsix.

     Par défaut, le dossier de sortie de la génération est le.. dossier \bin\Debug sous le dossier qui contient votre fichier projet.

## <a name="test-the-project-property"></a>Tester la propriété du projet
 Vous êtes maintenant prêt à tester la propriété de projet personnalisée. Il est plus facile de déboguer et de tester la nouvelle extension de propriété de projet dans une instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Cette instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] est créée lorsque vous exécutez un projet VSIX ou un autre projet d’extensibilité. Après avoir débogué le projet, vous pouvez installer l’extension sur votre système, puis continuer à déboguer et à le tester dans une instance normale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Pour déboguer et tester l’extension dans une instance expérimentale de Visual Studio

1. Redémarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] avec les informations d’identification d’administration, puis ouvrez la solution ProjectExtensionPackage.

2. Démarrez une version Debug de votre projet en choisissant la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**  >  **Démarrer le débogage**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] installe l’extension sur le projet%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Property\1.0 et démarre une instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

3. Dans l’instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , créez un projet SharePoint pour une solution de batterie de serveurs et utilisez les valeurs par défaut pour les autres valeurs de l’Assistant.

    1. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

    2. En haut de la boîte de dialogue **nouveau projet** , choisissez **.NET Framework 3,5** dans la liste des versions du .NET Framework.

         Les extensions d’outils SharePoint nécessitent des fonctionnalités dans cette version de [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

    3. Sous le nœud **modèles** , développez le nœud **Visual C#** ou **Visual Basic** , choisissez le nœud **SharePoint** , puis choisissez le nœud **2010** .

    4. Choisissez le modèle de **projet SharePoint 2010** , puis entrez **ModuleTest** comme nom de votre projet.

4. Dans **Explorateur de solutions**, choisissez le nœud de projet **ModuleTest** .

     Un nouveau **dossier images de mappage** de propriétés personnalisées s’affiche dans la fenêtre **Propriétés** avec la valeur par défaut **false**.

5. Remplacez la valeur de cette propriété par **true**.

     Un dossier de ressources images est ajouté au projet SharePoint.

6. Remplacez la valeur de cette propriété par **false**.

     Si vous choisissez le bouton **Oui** dans la boîte de dialogue **supprimer le dossier images ?** , le dossier de ressources images est supprimé du projet SharePoint.

7. Fermez l'instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

## <a name="see-also"></a>Voir aussi
- [Étendre des projets SharePoint](../sharepoint/extending-sharepoint-projects.md)
- [Comment : ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Effectuer une conversion entre des types système de projet SharePoint et d’autres types de projets Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Enregistrer des données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [Associer des données personnalisées à des extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
