---
title: "Walkthrough: Creating a SharePoint Project Extension"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 5547e2ed-47a3-48f1-9619-42149c03df76
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Walkthrough: Creating a SharePoint Project Extension
  Cette procédure pas à pas illustre la création d'une extension pour les projets SharePoint.  Vous pouvez utiliser une extension de projet pour répondre aux événements au niveau de le projet par exemple lorsqu'un projet est ajouté, supprimé, renommé ou.  Vous pouvez également ajouter des propriétés personnalisées ou répondre lorsqu'une valeur de propriété change.  Contrairement aux extensions d'élément de projet, les extensions de projet ne peuvent pas être associées à un type de projet SharePoint particulier.  Lorsque vous créez une extension de projet, celle\-ci est chargée dès l'ouverture d'un projet SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Dans cette procédure pas à pas, vous créez une propriété booléenne personnalisée qui est ajoutée à tout projet SharePoint créé dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Lorsqu'elle a la valeur **True**, la nouvelle propriété ajoute ou mappe un dossier ressource Images à votre projet.  Lorsqu'elle a la valeur **False**, le dossier Images est supprimé, s'il existe.  Pour plus d’informations, consultez [Comment : ajouter et supprimer des dossiers mappés](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Création d'une extension [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], pour les projets SharePoint, qui effectue les opérations suivantes :  
  
    -   Ajoute une propriété de projet personnalisée à la fenêtre Propriétés.  La propriété s'applique à tout projet SharePoint.  
  
    -   Utilise le modèle d'objet du projet SharePoint pour ajouter un dossier mappé à un projet.  
  
    -   Utilise le modèle objet Automation principal \(DTE\) dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour supprimer un dossier mappé du projet.  
  
-   Génération d'un package VSIX \(Visual Studio Extension\) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pour déployer l'assembly d'extension de la propriété du projet.  
  
-   Débogage et test de la propriété du projet.  
  
## Composants requis  
 Vous avez besoin des composants suivants sur l'ordinateur de développement pour terminer cette procédure pas à pas :  
  
-   Éditions de [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint et [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] prises en charge.  Pour plus d’informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  Cette procédure pas à pas se base sur le modèle **Projet VSIX** dans le [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] pour créer un package VSIX nécessaire au déploiement de l'extension de propriété du projet.  Pour plus d’informations, consultez [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## Création du projet  
 Pour exécuter cette procédure pas à pas, vous devez créer deux projets :  
  
-   Un projet VSIX pour créer le package VSIX afin de déployer l'extension de projet.  
  
-   Un projet de bibliothèque de classes qui implémente l'extension de projet.  
  
 Démarrez la procédure pas à pas en créant les projets.  
  
#### Pour créer le projet VSIX  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
3.  Dans la boîte de dialogue **Nouveau projet** , développez les nœuds **Visual C\#** ou **Visual Basic** , puis sélectionnez le nœud **Extensibilité** .  
  
    > [!NOTE]  
    >  Ce nœud est disponible uniquement si vous installez le kit de développement Visual Studio.  Pour plus d'informations, consultez la section des composants requis plus haut dans cette rubrique.  
  
4.  En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework, puis choisissez le modèle **projet VSIX** .  
  
5.  Dans la zone **Nom** , entrez **ProjectExtensionPackage**, puis choisissez le bouton **OK** .  
  
     Le projet **ProjectExtensionPackage** apparaît dans **Explorateur de solutions**.  
  
#### Pour créer le projet d'extension  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution, choisissez **Ajouter**, puis choisissez **Nouveau projet**.  
  
    > [!NOTE]  
    >  Dans les projets d' [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , le nœud de la solution s'affiche dans **Explorateur de solutions** uniquement si la case à cocher **Toujours solution show** est sélectionnée dans [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Dans la boîte de dialogue **Nouveau projet** , développez les nœuds **Visual C\#** ou **Visual Basic** , puis choisissez **Fenêtres**.  
  
3.  En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework, puis choisissez le modèle de projet **Bibliothèque de classes** .  
  
4.  Dans la zone **Nom** , entrez **ProjectExtension**, puis choisissez le bouton **OK** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **ProjectExtension** à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprimez le fichier de code Class1 du projet.  
  
## Configuration du projet  
 Avant d'écrire le code pour créer l'extension de projet, ajoutez les fichiers de code et les références d'assembly au projet d'extension.  
  
#### Pour configurer le projet  
  
1.  Ajoutez un fichier de code nommé **CustomProperty** au projet ProjectExtension.  
  
2.  Ouvrez le menu contextuel du projet **ProjectExtension** , puis choisissez **Ajouter une référence**.  
  
3.  Dans la boîte de dialogue **gestionnaire de référence – CustomProperty** , sélectionnez le nœud **framework** , puis activez la case à cocher en regard de les assemblys System.ComponentModel.Composition et System.Windows.Forms.  
  
4.  Sélectionnez le nœud **Extensions** , activez la case à cocher en regard de les assemblys Microsoft.VisualStudio.SharePoint et EnvDTE, puis choisissez le bouton **OK** .  
  
5.  Dans **Explorateur de solutions**, sous le dossier **Références** pour le projet **ProjectExtension** , choisissez **EnvDTE**.  
  
6.  Dans la fenêtre **Propriétés**, affectez à la propriété **Incorporer les types d'interopérabilité** la valeur **False**.  
  
## Définition de la nouvelle propriété de projet SharePoint  
 Créez une classe qui définit l'extension de projet et le comportement de la nouvelle propriété de projet.  Pour définir la nouvelle extension de projet, la classe implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Implémentez cette interface chaque fois que vous souhaitez définir une extension pour un projet SharePoint.  En outre, ajoutez l'attribut <xref:System.ComponentModel.Composition.ExportAttribute> à la classe.  Cet attribut permet à [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] de découvrir et de charger votre implémentation <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Communiquez le type <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> au constructeur de l'attribut.  
  
#### Pour définir la nouvelle propriété de projet SharePoint  
  
1.  Collez le code suivant dans le fichier de code CustomProperty.  
  
     [!code-csharp[SPExt_ProjectExtension#1](../snippets/csharp/VS_Snippets_OfficeSP/spext_projectextension/cs/projectextension/customproperty.cs#1)]
     [!code-vb[SPExt_ProjectExtension#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_projectextension/vb/projectextension/customproperty.vb#1)]  
  
## Génération de la solution  
 Ensuite, générez la solution afin de garantir sa compilation sans erreur.  
  
#### Pour générer la solution  
  
1.  Dans la barre de menus, sélectionnez **Générer**, **Générer la solution**.  
  
## Création d'un package VSIX pour déployer l'extension de propriété de projet  
 Pour déployer l'extension de projet, utilisez le projet VSIX dans votre solution pour créer un package VSIX.  En premier lieu, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest qui est inclus dans le projet VSIX.  Ensuite, créez le package VSIX en générant la solution.  
  
#### Pour configurer et créer le package VSIX  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du fichier source.extension.vsixmanifest, puis choisissez le bouton **Ouvrir** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ouvre le fichier dans le concepteur de manifestes.  Les informations qui s'affichent dans l'onglet **métadonnées** également s'affichent dans **Extensions et mises à jour**. Tous les packages VSIX requièrent le fichier extension.vsixmanifest.  Pour plus d'informations sur ce fichier, consultez [Référence de schéma d'extensions VSIX](http://msdn.microsoft.com/fr-fr/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Dans la zone **nom de produit** , entrez **Propriété de projet personnalisée**.  
  
3.  Dans la zone **Author** , entrez **Contoso**.  
  
4.  Dans la zone **Description** , entrez **Une propriété personnalisée de projet SharePoint qui bascule le mappage du dossier ressource images au projet**.  
  
5.  Sélectionnez l'onglet **Composants** , puis choisissez le bouton **Nouveau** .  
  
     La boîte de dialogue **ajoutez le nouveau ressource** s'affiche.  
  
6.  Dans la liste **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à l'élément `MEFComponent` dans le fichier extension.vsixmanifest.  Cet élément spécifie le nom d'un assembly d'extension dans le package VSIX.  Pour plus d’informations, consultez [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/fr-fr/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Dans la liste **Source** , sélectionnez la case d'option **un projet dans la solution actuelle** .  
  
8.  Dans la liste **Projet** , choisissez **ProjectExtension**.  
  
     Cette valeur identifie le nom de l'assembly que vous générez dans le projet.  
  
9. Choisissez **OK** pour fermer la boîte de dialogue **ajoutez le nouveau ressource** .  
  
10. Dans la barre de menus, sélectionnez **Fichier**, **Enregistrer tout** lorsque vous avez terminé, puis fermez le concepteur de manifestes.  
  
11. Dans la barre de menus, sélectionnez **Générer**, **Générer la solution**, puis vérifiez que le projet se compile sans erreurs.  
  
12. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **ProjectExtensionPackage** , puis choisissez le bouton **Ouvrir le dossier dans l'Explorateur de fichiers** .  
  
13. Dans **Explorateur de fichiers**, ouvrez le dossier de sortie de la génération pour le projet ProjectExtensionPackage, puis vérifiez que le répertoire contient un fichier nommé ProjectExtensionPackage.vsix.  
  
     Par défaut, le dossier de sortie de la génération est le dossier ..  \\bin\\Debug sous le dossier qui contient votre fichier projet.  
  
## Test de la propriété de projet  
 Vous êtes maintenant prêt à tester la propriété de projet personnalisée.  Il est plus facile de déboguer et tester la nouvelle extension de propriété de projet dans une instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Cette instance d' [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] est créée lorsque vous exécutez un projet VSIX ou tout autre projet d'extensibilité.  Après avoir mis au point le projet, vous pouvez installer l'extension sur votre système puis continuer à le déboguer et tester dans une instance normale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### Pour déboguer et tester l'extension dans une instance expérimentale de Visual Studio  
  
1.  Redémarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] avec les informations d'identification d'administration, puis ouvrez la solution ProjectExtensionPackage.  
  
2.  Démarrez une version debug de votre projet soit en choisissant la clé **F5** ou, dans la barre de menus, choisissant **Déboguer**, **Démarrer le débogage**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] installe l'extension dans %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Custom Project Property \\ 1,0 et démarre une instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  Dans l'instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], créez un projet SharePoint pour une solution de batterie, puis utilisez les valeurs par défaut pour les autres valeurs dans l'assistant.  
  
    1.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
    2.  En haut de la boîte de dialogue **Nouveau projet** , choisissez **.NET Framework 3.5** dans la liste des versions du .NET Framework.  
  
         Les extensions d'outils SharePoint nécessitent des fonctionnalités dans cette version de [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  Sous le nœud **Modèles** , développez le nœud **Visual C\#** ou **Visual Basic** , sélectionnez le nœud **SharePoint** , puis sélectionnez le nœud **2010** .  
  
    4.  Sélectionnez le modèle **Projet SharePoint 2010** , puis entrez **ModuleTest** comme nom de votre projet.  
  
4.  Dans **Explorateur de solutions**, sélectionnez le nœud de projet **ModuleTest** .  
  
     Une nouvelle propriété personnalisée **Map Images Folder** s'affiche dans la fenêtre **Propriétés** avec **False** comme valeur par défaut.  
  
5.  Remplacez la valeur de cette propriété par **True**.  
  
     Un dossier ressource Images est ajouté au projet SharePoint.  
  
6.  Remplacez la valeur de cette propriété à **False**.  
  
     Si vous choisissez le bouton **oui** dans la boîte de dialogue **Supprimez le dossier images ?** , le dossier ressource images est supprimé du projet SharePoint.  
  
7.  Fermez l'instance expérimentale de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## Voir aussi  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  