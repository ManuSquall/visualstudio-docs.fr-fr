---
title: "Procédure pas à pas : Étendre un Type d’élément de projet SharePoint | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e2f39fc15d73b2019e739d7695f40cf0e3fd0940
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-extending-a-sharepoint-project-item-type"></a>Procédure pas à pas : extension d'un type d'élément de projet SharePoint
  Vous pouvez utiliser la **modèle de connectivité de données métiers** élément de projet pour créer un modèle pour le service de connectivité de données métiers (BDC) dans SharePoint. Par défaut, lorsque vous créez un modèle à l’aide de cet élément de projet, les données dans le modèle ne sont pas affichées aux utilisateurs. Vous devez également créer une liste externe dans SharePoint pour permettre aux utilisateurs d’afficher les données.  
  
 Dans cette procédure pas à pas, vous allez créer une extension pour le **modèle de connectivité de données métiers** élément de projet. Les développeurs peuvent utiliser l’extension pour créer une liste externe dans leur projet qui affiche les données dans le modèle BDC. Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’une extension Visual Studio qui exécute deux tâches principales :  
  
    -   Il génère une liste externe qui affiche les données dans un modèle BDC. L’extension utilise le modèle d’objet pour le système de projet SharePoint pour générer un fichier Elements.xml qui définit la liste. Il ajoute également le fichier au projet de sorte qu’il est déployé avec le modèle BDC.  
  
    -   Il ajoute un élément de menu contextuel pour le **modèle de connectivité de données métiers** dans des éléments de projet **l’Explorateur de solutions**. Les développeurs peuvent cliquez sur cet élément de menu pour générer une liste externe pour le modèle BDC.  
  
-   Création d’un package d’Extension Visual Studio (VSIX) pour déployer l’assembly d’extension.  
  
-   Test de l’extension.  
  
## <a name="prerequisites"></a>Prérequis  
 Vous devez disposer des composants suivants sur l’ordinateur de développement pour terminer cette procédure pas à pas :  
  
-   Éditions prises en charge de Microsoft Windows, SharePoint et Visual Studio. Pour plus d’informations, consultez [configuration requise pour le développement de Solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Cette procédure pas à pas utilise le **projet VSIX** modèle dans le Kit de développement pour créer un package VSIX pour déployer l’élément de projet. Pour plus d’informations, consultez [extension des outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Connaissance des concepts suivants s’avère utile, mais n’est pas requis pour terminer la procédure pas à pas :  
  
-   Le service BDC dans [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]. Pour plus d’informations, consultez [Architecture BDC](http://go.microsoft.com/fwlink/?LinkId=177798).  
  
-   Le schéma XML pour les modèles BDC. Pour plus d’informations, consultez [Infrastructure de modèle BDC](http://go.microsoft.com/fwlink/?LinkId=177799).  
  
## <a name="creating-the-projects"></a>Création des projets  
 Pour effectuer cette procédure pas à pas, vous devez créer deux projets :  
  
-   Un projet VSIX pour créer le package VSIX pour déployer l’extension d’élément de projet.  
  
-   Un projet de bibliothèque de classes qui implémente l’extension d’élément de projet.  
  
 Démarrer la procédure pas à pas en créant les projets.  
  
#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, puis choisissez le **extensibilité** nœud.  
  
    > [!NOTE]  
    >  Le **extensibilité** nœud est disponible uniquement si vous installez le Kit de développement logiciel Visual Studio. Pour plus d’informations, consultez la section conditions préalables plus haut dans cette rubrique.  
  
4.  Dans la liste en haut de la **nouveau projet** boîte de dialogue, choisissez **.NET Framework 4.5**.  
  
     Extensions des outils SharePoint nécessitent des fonctionnalités dans cette version du .NET Framework.  
  
5.  Choisissez le **projet VSIX** modèle.  
  
6.  Dans le **nom** , entrez **GenerateExternalDataLists**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Ajoute le **GenerateExternalDataLists** projet **l’Explorateur de solutions**.  
  
7.  Si le fichier source.extension.vsixmanifest ne s’ouvre pas automatiquement, ouvrez le menu contextuel dans le projet GenerateExternalDataLists, puis choisissez **ouvrir**  
  
8.  Vérifiez que le fichier source.extension.vsixmanifest possède une entrée non vide (Entrez Contoso) pour le champ Author, enregistrez le fichier et fermez-le.  
  
#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **GenerateExternalDataLists** nœud de la solution, choisissez **ajouter**, puis choisissez **nouveau projet**.  
  
2.  Dans le **ajouter un nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, puis choisissez le **Windows** nœud.  
  
3.  Dans la liste en haut de la boîte de dialogue, choisissez **.NET Framework 4.5**.  
  
4.  Dans la liste des modèles de projet, choisissez **bibliothèque de classes**.  
  
5.  Dans le **nom** , entrez **BdcProjectItemExtension**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Ajoute le **BdcProjectItemExtension** projet à la solution et ouvre le fichier de code Class1 par défaut.  
  
6.  Supprime le fichier de code Class1 du projet.  
  
## <a name="configuring-the-extension-project"></a>Configuration du projet d’Extension  
 Avant d’écrire de code pour créer l’extension d’élément de projet, ajoutez les références d’assembly au projet d’extension et les fichiers de code.  
  
#### <a name="to-configure-the-project"></a>Pour configurer le projet  
  
1.  Dans le projet BdcProjectItemExtension, ajoutez deux fichiers de code qui portent les noms suivants :  
  
    -   ProjectItemExtension  
  
    -   GenerateExternalDataLists  
  
2.  Choisissez le projet BdcProjectItemExtension, puis, dans la barre de menus, **projet**, **ajouter une référence**.  
  
3.  Sous le **assemblys** nœud, choisissez le **Framework** nœud, puis activez la case à cocher pour chacun des assemblys suivants :  
  
    -   System.ComponentModel.Composition  
  
    -   WindowsBase  
  
4.  Sous le **assemblys** nœud, choisissez le **Extensions** nœud et sélectionnez la case à cocher pour l’assembly suivant :  
  
    -   Microsoft.VisualStudio.SharePoint  
  
5.  Sélectionnez le bouton **OK** .  
  
## <a name="defining-the-project-item-extension"></a>Définition de l’Extension d’élément de projet  
 Créer une classe qui définit l’extension pour le **modèle de connectivité de données métiers** élément de projet. Pour définir l’extension, la classe implémente le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interface. Implémentez cette interface chaque fois que vous souhaitez étendre un type d’élément de projet existant.  
  
#### <a name="to-define-the-project-item-extension"></a>Pour définir l’extension d’élément de projet  
  
1.  Collez le code suivant dans le fichier de code ProjectItemExtension.  
  
    > [!NOTE]  
    >  Après avoir ajouté ce code, le projet aura des erreurs de compilation. Ces erreurs disparaître lorsque vous ajoutez du code dans les étapes ultérieures.  
  
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]  
  
## <a name="creating-the-external-data-lists"></a>Création des listes de données externes  
 Ajoutez une définition partielle de la `GenerateExternalDataListsExtension` classe qui crée une liste de données externes pour chaque entité dans le modèle BDC. Pour créer la liste de données externes, ce code lit d’abord les données d’entité dans le modèle BDC en analysant les données XML dans le fichier de modèle BDC. Ensuite, il crée une instance de liste qui est basée sur le modèle BDC et ajoute cette instance de liste au projet.  
  
#### <a name="to-create-the-external-data-lists"></a>Pour créer des listes de données externes  
  
1.  Collez le code suivant dans le fichier de code GenerateExternalDataLists.  
  
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]  
  
## <a name="checkpoint"></a>Point de contrôle  
 À ce stade dans la procédure pas à pas, l’intégralité du code pour l’extension d’élément de projet est maintenant dans le projet. Générez la solution pour vous assurer que le projet se compile sans erreur.  
  
#### <a name="to-build-the-solution"></a>Pour générer la solution  
  
1.  Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
## <a name="creating-a-vsix-package-to-deploy-the-project-item-extension"></a>Création d’un Package VSIX pour déployer l’Extension d’élément de projet  
 Pour déployer l’extension, utilisez le projet VSIX dans votre solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest qui est inclus dans le projet VSIX. Ensuite, créez le package VSIX en générant la solution.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Pour configurer et créer le package VSIX  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le fichier source.extension.vsixmanifest dans le projet GenerateExternalDataLists, puis choisissez **ouvrir**.  
  
     Visual Studio ouvre le fichier dans l’éditeur de manifeste. Le fichier source.extension.vsixmanifest est que la base du fichier extension.vsixmanifest requis par tous les packages VSIX. Pour plus d’informations sur ce fichier, consultez [une Extension de schéma 1.0 référence VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Dans le **Product Name** , entrez **Générateur de liste de données externe**.  
  
3.  Dans le **auteur** , entrez **Contoso**.  
  
4.  Dans le **Description** , entrez **une extension pour les éléments de projet de modèle de connectivité de données métiers qui peut être utilisé pour générer des listes de données externes**.  
  
5.  Sur le **actifs** onglet de l’éditeur, choisissez le **nouveau** bouton.  
  
     Le **ajouter un nouveau composant** boîte de dialogue s’affiche.  
  
6.  Dans le **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à la `MefComponent` élément dans le fichier extension.vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MEFComponent, élément (schéma VSX)](http://msdn.microsoft.com/en-us/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Dans le **Source** , choisissez **un projet dans la solution actuelle**.  
  
8.  Dans le **projet** , choisissez **BdcProjectItemExtension**, puis choisissez le **OK** bouton.  
  
9. Dans la barre de menus, choisissez **Générer**, puis **Générer la solution**.  
  
10. Assurez-vous que le projet se compile et s’il se génère sans erreur.  
  
11. Assurez-vous que le dossier de sortie de génération pour le projet GenerateExternalDataLists contienne désormais le fichier GenerateExternalDataLists.vsix.  
  
     Par défaut, le dossier de sortie est le... dossier \bin\debug sous le dossier qui contient votre fichier projet.  
  
## <a name="testing-the-project-item-extension"></a>Test de l’Extension d’élément de projet  
 Vous êtes maintenant prêt à tester l’extension d’élément de projet. Commencez à déboguer le projet d’extension dans l’instance expérimentale de Visual Studio. Ensuite, utilisez l’extension dans l’instance expérimentale de Visual Studio pour générer une liste externe pour un modèle BDC. Enfin, ouvrez la liste externe sur le site SharePoint pour vérifier qu’il fonctionne comme prévu.  
  
#### <a name="to-start-debugging-the-extension"></a>Pour démarrer le débogage de l’extension  
  
1.  Si nécessaire, redémarrez Visual Studio avec des informations d’identification d’administration et ouvrez la solution GenerateExternalDataLists.  
  
2.  Dans le projet BdcProjectItemExtension, ouvrez le fichier de code ProjectItemExtension et puis ajoutez un point d’arrêt à la ligne de code dans le `Initialize` (méthode).  
  
3.  Ouvrez le fichier de code GenerateExternalDataLists et puis ajoutez un point d’arrêt à la première ligne de code dans le `GenerateExternalDataLists_Execute` (méthode).  
  
4.  Démarrer le débogage en choisissant la touche F5 ou, dans la barre de menus, en choisissant **déboguer**, **démarrer le débogage**.  
  
     Visual Studio installe l’extension %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External externe\1. 0 de liste de données et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.  
  
#### <a name="to-test-the-extension"></a>Pour tester l’extension  
  
1.  Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **fichier**, **nouveau**, **projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez le **modèles** nœud, développez le **Visual C#** nœud, développez le **SharePoint** nœud, puis Choisissez **2010**.  
  
3.  Dans la liste en haut de la boîte de dialogue, assurez-vous que **.NET Framework 3.5** est sélectionnée. Pour les projets [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] requièrent cette version du .NET Framework.  
  
4.  Dans la liste des modèles de projet, choisissez **projet SharePoint 2010**.  
  
5.  Dans le **nom** , entrez **SharePointProjectTestBDC**, puis choisissez le **OK** bouton.  
  
6.  Dans l’Assistant Personnalisation de SharePoint, entrez l’URL du site que vous souhaitez utiliser pour le débogage, choisissez **déployer une solution de batterie de serveurs**, puis choisissez le **Terminer**bouton.  
  
7.  Ouvrez le menu contextuel pour le projet SharePointProjectTestBDC, choisissez **ajouter**, puis choisissez **un nouvel élément**.  
  
8.  Dans le **ajouter NewItem - SharePointProjectTestBDC** boîte de dialogue, développez le nœud de la langue installée, développez la **SharePoint** nœud.  
  
9. Choisissez le **2010** nœud, puis choisissez le **modèle de connectivité de données métiers (Solution de batterie uniquement)** modèle.  
  
10. Dans le **nom** , entrez **TestModèleBDC**, puis choisissez le **ajouter** bouton.  
  
11. Vérifiez que le code dans l’autre instance de Visual Studio s’arrête au point d’arrêt que vous définissez dans le `Initialize` du fichier de code ProjectItemExtension (méthode).  
  
12. Dans l’instance arrêté de Visual Studio, choisissez le **F5** clé, ou dans la barre de menus, choisissez **déboguer**, **continuer** pour continuer à déboguer le projet.  
  
13. Dans l’instance expérimentale de Visual Studio, choisissez le **F5** de clé, ou, dans la barre de menus, choisissez **déboguer**, **démarrer le débogage** pour générer, déployer et exécuter le  **TestModèleBDC** projet.  
  
     Le navigateur web s’ouvre à la page par défaut du site SharePoint qui est spécifié pour le débogage.  
  
14. Vérifiez que le **répertorie** section dans la zone Lancement rapide ne contient pas encore une liste qui est basée sur le modèle BDC par défaut dans le projet. Vous devez d’abord créer une liste de données externes, à l’aide de l’interface utilisateur SharePoint ou à l’aide de l’extension d’élément de projet.  
  
15. Fermez le navigateur web.  
  
16. Dans l’instance de Visual Studio qui contient le projet TestModèleBDC est ouvert, ouvrez le menu contextuel pour le **TestModèleBDC** nœud **l’Explorateur de solutions**, puis choisissez **générer les données externes Liste**.  
  
17. Vérifiez que le code dans l’autre instance de Visual Studio s’arrête au point d’arrêt que vous définissez dans le `GenerateExternalDataLists_Execute` (méthode). Choisissez le **F5** de clé, ou, dans la barre de menus, choisissez **déboguer**, **continuer** pour continuer à déboguer le projet.  
  
18. L’instance expérimentale de Visual Studio ajoute une instance de liste qui est nommée **Entity1DataList** à la TestModèleBDC projet et l’instance génère également une fonctionnalité qui est nommée **Feature2** pour obtenir la liste instance.  
  
19. Choisissez le **F5** de clé, ou, dans la barre de menus, choisissez **déboguer**, **démarrer le débogage** pour générer, déployer et exécuter le projet TestModèleBDC.  
  
     Le navigateur web s’ouvre à la page par défaut du site SharePoint qui est utilisé pour le débogage.  
  
20. Dans le **répertorie** section de la zone de lancement rapide, choisissez le **Entity1DataList** liste.  
  
21. Vérifiez que la liste contient des colonnes nommées Identifier1 et Message, en plus d’un élément qui a une valeur identificateur1 de 0 et la valeur Message Hello World.  
  
     Le **modèle de connectivité de données métiers** modèle de projet génère le modèle BDC par défaut qui fournit toutes les données.  
  
22. Fermez le navigateur web.  
  
## <a name="cleaning-up-the-development-computer"></a>Nettoyage de l’ordinateur de développement  
 Après avoir terminé le test de l’extension d’élément de projet, supprimez la liste externe et le modèle BDC à partir du site SharePoint et supprimez l’extension d’élément de projet à partir de Visual Studio.  
  
#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Pour supprimer de la liste de données externes à partir du site SharePoint  
  
1.  Dans la zone Lancement rapide du site SharePoint, choisissez le **Entity1DataList** liste.  
  
2.  Dans le ruban sur le site SharePoint, choisissez le **liste** onglet.  
  
3.  Sur le **liste** sous l’onglet du **paramètres** groupe, choisissez **paramètres de la liste**.  
  
4.  Sous **autorisations et gestion**, choisissez **supprimer cette liste**, puis choisissez **OK** pour confirmer que vous souhaitez envoyer la liste à la Corbeille.  
  
5.  Fermez le navigateur web.  
  
#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Pour supprimer le modèle BDC à partir du site SharePoint  
  
1.  Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **générer**, **Retract**.  
  
     Visual Studio supprime le modèle BDC à partir du site SharePoint.  
  
#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Pour supprimer l’extension d’élément de projet à partir de Visual Studio  
  
1.  Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s’ouvre.  
  
2.  Dans la liste des extensions, choisissez **Générateur de liste de données externe**, puis choisissez le **désinstallation** bouton.  
  
3.  Dans la boîte de dialogue qui s’affiche, choisissez **Oui** pour confirmer que vous voulez désinstaller l’extension.  
  
4.  Choisissez **redémarrer maintenant** pour terminer la désinstallation.  
  
5.  Fermez les deux instances de Visual Studio (l’instance expérimentale et l’instance dans laquelle la solution GenerateExternalDataLists est ouverte).  
  
## <a name="see-also"></a>Voir aussi  
 [Extension du système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Création d’un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Conception d’un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  