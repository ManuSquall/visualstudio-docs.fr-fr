---
title: 'Procédure pas à pas : Création d’une Extension de projet SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 39432f20620a3c7e6f374b09943fc73c2d4d2903
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885898"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Procédure pas à pas : Créer une extension de projet SharePoint
  Cette procédure pas à pas illustre comment créer une extension pour les projets SharePoint. Vous pouvez utiliser une extension de projet pour répondre aux événements au niveau du projet tels que quand un projet est ajouté, supprimé ou renommé. Vous pouvez également ajouter des propriétés personnalisées ou répondre lorsqu’une valeur de propriété change. Contrairement aux extensions d’élément de projet, les extensions de projet ne peut pas être associées à un type de projet SharePoint particulier. Lorsque vous créez une extension de projet, l’extension de charge tout type de projet SharePoint est ouvert dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Dans cette procédure pas à pas, vous allez créer une propriété booléenne personnalisée qui est ajoutée à un projet SharePoint créé dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Lorsque la valeur **True**, la nouvelle propriété ajoute ou mappe un dossier de ressources d’Images à votre projet. Lorsque la valeur **False**, le dossier Images est supprimé, s’il existe. Pour plus d’informations, consultez [Comment : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension pour les projets SharePoint qui effectue les opérations suivantes :  
  
    -   Ajoute une propriété de projet personnalisés à la fenêtre Propriétés. La propriété s’applique à un projet SharePoint.  
  
    -   Utilise le modèle objet de projet SharePoint pour ajouter un dossier mappé à un projet.  
  
    -   Utilise le [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (DTE) pour supprimer un dossier mappé à partir du projet de modèle d’objet automation.  
  
-   Création d’un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] package d’Extension (VSIX) pour déployer l’assembly d’extension de la propriété de projet.  
  
-   Débogage et test de la propriété de projet.  
  
## <a name="prerequisites"></a>Prérequis  
 Vous avez besoin des composants suivants sur l’ordinateur de développement pour effectuer cette procédure pas à pas :  
  
-   Éditions prises en charge [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint et [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Cette procédure pas à pas utilise le **projet VSIX** modèle dans le [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] pour créer un package VSIX pour déployer l’extension de propriété de projet. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez créer deux projets :  
  
- Un projet VSIX pour créer le package VSIX pour déployer l’extension de projet.  
  
- Un projet de bibliothèque de classes qui implémente l’extension de projet.  
  
  Démarrer la procédure pas à pas en créant les projets.  
  
#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, puis choisissez le **extensibilité** nœud.  
  
    > [!NOTE]  
    >  Ce nœud est disponible uniquement si vous installez le SDK Visual Studio. Pour plus d’informations, consultez la section conditions préalables plus haut dans cette rubrique.  
  
4.  En haut de la boîte de dialogue, choisissez **.NET Framework 4.5** dans la liste des versions du .NET Framework, puis choisissez le **projet VSIX** modèle.  
  
5.  Dans le **nom** , entrez **ProjectExtensionPackage**, puis choisissez le **OK** bouton.  
  
     Le **ProjectExtensionPackage** projet s’affiche dans **l’Explorateur de solutions**.  
  
#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud de solution, choisissez **ajouter**, puis choisissez **nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, puis choisissez **Windows**.  
  
3.  En haut de la boîte de dialogue, choisissez **.NET Framework 4.5** dans la liste des versions du .NET Framework, puis choisissez le **bibliothèque de classes** modèle de projet.  
  
4.  Dans le **nom** , entrez **ProjectExtension**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **ProjectExtension** projet à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprimer le fichier de code Class1 du projet.  
  
## <a name="configure-the-project"></a>Configurer le projet
 Avant d’écrire du code pour créer l’extension de projet, ajoutez les fichiers de code et des références d’assembly au projet d’extension.  
  
#### <a name="to-configure-the-project"></a>Pour configurer le projet  
  
1.  Ajouter un fichier de code nommé **CustomProperty** au projet ProjectExtension.  
  
2.  Ouvrez le menu contextuel pour le **ProjectExtension** de projet, puis choisissez **ajouter une référence**.  
  
3.  Dans le **Gestionnaire de références - CustomProperty** boîte de dialogue, sélectionnez le **Framework** nœud et sélectionnez la case à cocher en regard des assemblys System.ComponentModel.Composition et System.Windows.Forms.  
  
4.  Choisissez le **Extensions** nœud, sélectionnez la case à cocher en regard des assemblys Microsoft.VisualStudio.SharePoint et EnvDTE, puis choisissez le **OK** bouton.  
  
5.  Dans **l’Explorateur de solutions**, sous le **références** dossier pour le **ProjectExtension** de projet, choisissez **EnvDTE**.  
  
6.  Dans le **propriétés** fenêtre, de modifier le **incorporer les Types Interop** propriété **False**.  
  
## <a name="define-the-new-sharepoint-project-property"></a>Définir la nouvelle propriété de projet SharePoint
 Créez une classe qui définit l’extension de projet et le comportement de la nouvelle propriété de projet. Pour définir la nouvelle extension de projet, la classe implémente le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interface. Implémentez cette interface chaque fois que vous souhaitez définir une extension pour un projet SharePoint. En outre, ajouter le <xref:System.ComponentModel.Composition.ExportAttribute> à la classe. Cet attribut permet de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour détecter et charger votre <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implémentation. Passer le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> type au constructeur de l’attribut.  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>Pour définir la nouvelle propriété de projet SharePoint  
  
1.  Collez le code suivant dans le fichier de code CustomProperty.  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="build-the-solution"></a>Générer la solution
 Ensuite, générez la solution pour vous assurer qu’il est compilé sans erreur.  
  
#### <a name="to-build-the-solution"></a>Pour générer la solution  
  
1.  Dans la barre de menus, choisissez **Générer**  >  **Générer la solution**.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Créer un package VSIX pour déployer l’extension de propriété de projet
 Pour déployer l’extension de projet, utilisez le projet VSIX dans votre solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest qui est inclus dans le projet VSIX. Ensuite, créez le package VSIX en générant la solution.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Pour configurer et créer le package VSIX  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le fichier source.extension.vsixmanifest, puis choisissez le **ouvrir** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ouvre le fichier dans le Concepteur de manifeste. Les informations qui apparaissent dans le **métadonnées** onglet apparaît également dans le **Extensions et mises à jour**. Tous les packages VSIX requièrent le fichier extension.vsixmanifest. Pour plus d’informations sur ce fichier, consultez [VSIX Extension schéma 1.0 référence](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Dans le **Product Name** , entrez **propriété de projet personnalisé**.  
  
3.  Dans le **auteur** , entrez **Contoso**.  
  
4.  Dans le **Description** , entrez **une propriété de projet SharePoint personnalisée qui active ou désactive le mappage du dossier de ressources d’Images au projet**.  
  
5.  Choisissez le **actifs** onglet, puis choisissez le **New** bouton.  
  
     Le **ajouter un nouveau composant** boîte de dialogue s’affiche.  
  
6.  Dans le **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à la `MEFComponent` élément dans le fichier extension.vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MEFComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  Dans le **Source** , choisissez le **un projet dans la solution actuelle** case d’option.  
  
8.  Dans le **projet** , choisissez **ProjectExtension**.  
  
     Cette valeur identifie le nom de l’assembly que vous générez dans le projet.  
  
9. Choisissez **OK** pour fermer la **ajouter un nouveau composant** boîte de dialogue.  
  
10. Dans la barre de menus, choisissez **fichier** > **Enregistrer tout** lorsque vous avez terminé et puis fermez le Concepteur de manifeste.  
  
11. Dans la barre de menus, choisissez **Build** > **générer la Solution**, puis assurez-vous que le projet se compile sans erreur.  
  
12. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ProjectExtensionPackage** de projet, puis choisissez le **ouvrir le dossier dans l’Explorateur de fichiers** bouton.  
  
13. Dans **Explorateur de fichiers**, ouvrez le dossier de sortie de génération pour le projet ProjectExtensionPackage, puis vérifiez que le dossier contient un fichier nommé ProjectExtensionPackage.vsix.  
  
     Par défaut, le dossier de sortie est le... dossier \bin\debug sous le dossier qui contient votre fichier projet.  
  
## <a name="test-the-project-property"></a>Tester la propriété de projet
 Vous êtes maintenant prêt à tester la propriété de projet personnalisé. Il est plus facile à déboguer et tester la nouvelle extension de propriété de projet dans une instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Cette instance de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] est créé lorsque vous exécutez un projet VSIX ou un autre projet d’extensibilité. Une fois que vous déboguez le projet, vous pouvez installer l’extension sur votre système et continuer à déboguer et tester dans une instance normale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Pour déboguer et tester l’extension dans une instance expérimentale de Visual Studio  
  
1.  Redémarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] avec les informations d’identification administratives, puis ouvrez la solution ProjectExtensionPackage.  
  
2.  Démarrer une version debug de votre projet en sélectionnant le **F5** clé ou, dans la barre de menus, choisissez **déboguer** > **démarrer le débogage**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Installe l’extension %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Project Property\1. 0 et démarre une instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  Dans l’instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez un projet SharePoint pour une solution de batterie de serveurs et utiliser les valeurs par défaut pour les autres valeurs dans l’Assistant.  
  
    1.  Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.  
  
    2.  En haut de la **nouveau projet** boîte de dialogue, sélectionnez **.NET Framework 3.5** dans la liste des versions du .NET Framework.  
  
         Extensions de l’outil SharePoint nécessitent des fonctionnalités dans cette version de la [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  Sous le **modèles** nœud, développez le **Visual C#** ou **Visual Basic** nœud, choisissez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
    4.  Choisissez le **projet SharePoint 2010** modèle, puis entrez **ModuleTest** comme nom de votre projet.  
  
4.  Dans **l’Explorateur de solutions**, choisissez le **ModuleTest** nœud du projet.  
  
     Une nouvelle propriété personnalisée **dossier Images de carte** s’affiche dans le **propriétés** fenêtre avec une valeur par défaut **False**.  
  
5.  Modifiez la valeur de cette propriété pour **True**.  
  
     Un dossier de ressources d’Images est ajouté au projet SharePoint.  
  
6.  Modification de la valeur de cette propriété en **False**.  
  
     Si vous choisissez la **Oui** situé dans le **supprimer le dossier Images ?** boîte de dialogue, les Images de dossier de ressources est supprimé du projet SharePoint.  
  
7.  Fermez l'instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Voir aussi
 [Étendre des projets SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Guide pratique pour Ajouter une propriété à des projets SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Effectuer une conversion entre les types de système de projet SharePoint et d’autres types de projet Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Enregistrer les données dans les extensions du système de projet SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associer des données personnalisées avec les extensions d’outils SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
