---
title: 'Procédure pas à pas : extension d’un type d’élément de projet SharePoint | Microsoft Docs'
description: Dans cette procédure pas à pas, vous créez une extension pour un type d’élément de projet SharePoint, tel que l’élément de projet de modèle de connectivité de données métiers (BDC).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a91cbd863ed613804418cd5d1666412a01f8f542
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217695"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>Procédure pas à pas : étendre un type d’élément de projet SharePoint
  Vous pouvez utiliser l’élément de projet **modèle de connectivité de données métiers** pour créer un modèle pour le service de connectivité de données métiers (BDC) dans SharePoint. Par défaut, lorsque vous créez un modèle à l’aide de cet élément de projet, les données du modèle ne sont pas affichées aux utilisateurs. Vous devez également créer une liste externe dans SharePoint pour permettre aux utilisateurs d’afficher les données.

 Dans cette procédure pas à pas, vous allez créer une extension pour l’élément de projet **modèle de connectivité de données métiers** . Les développeurs peuvent utiliser l’extension pour créer une liste externe dans leur projet qui affiche les données dans le modèle BDC. Cette procédure pas à pas décrit les tâches suivantes :

- Création d’une extension Visual Studio qui effectue deux tâches principales :

  - Il génère une liste externe qui affiche les données dans un modèle BDC. L’extension utilise le modèle objet pour le système de projet SharePoint pour générer un fichier *Elements.xml* qui définit la liste. Il ajoute également le fichier au projet afin qu’il soit déployé avec le modèle BDC.

  - Elle ajoute un élément de menu contextuel aux éléments de projet de **modèle de connectivité de données métiers** dans **Explorateur de solutions**. Les développeurs peuvent cliquer sur cet élément de menu pour générer une liste externe pour le modèle BDC.

- Génération d’un package d’extension Visual Studio (VSIX) pour déployer l’assembly d’extension.

- Test de l’extension.

## <a name="prerequisites"></a>Prérequis
 Pour effectuer cette procédure pas à pas, vous avez besoin des composants suivants sur l’ordinateur de développement :

- Éditions prises en charge de Microsoft Windows, SharePoint et Visual Studio.

- Le [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Cette procédure pas à pas utilise le modèle de **projet VSIX** dans le kit de développement logiciel (SDK) pour créer un package VSIX afin de déployer l’élément de projet. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer la procédure pas à pas :

- Service BDC dans [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] . Pour plus d’informations, consultez [architecture BDC](/previous-versions/office/developer/sharepoint-2010/ee558876(v=office.14)).

- Schéma XML pour les modèles BDC. Pour plus d’informations, consultez [infrastructure de modèle BDC](/previous-versions/office/developer/sharepoint-2010/ee556378(v=office.14)).

## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez créer deux projets :

- Projet VSIX pour créer le package VSIX pour déployer l’extension d’élément de projet.

- Projet de bibliothèque de classes qui implémente l’extension d’élément de projet.

  Démarrez la procédure pas à pas en créant les projets.

#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

3. Dans la boîte de dialogue **nouveau projet** , développez les nœuds **Visual C#** ou **Visual Basic** , puis choisissez le nœud **extensibilité** .

    > [!NOTE]
    > Le nœud **extensibilité** est disponible uniquement si vous installez le kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez la section conditions préalables, plus haut dans cette rubrique.

4. Dans la liste en haut de la boîte de dialogue **nouveau projet** , choisissez **.NET Framework 4,5**.

     Les extensions des outils SharePoint requièrent des fonctionnalités de cette version du .NET Framework.

5. Choisissez le modèle de **projet VSIX** .

6. Dans la zone **nom** , entrez **GenerateExternalDataLists**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **GenerateExternalDataLists** à **Explorateur de solutions**.

7. Si le fichier source. extension. vsixmanifest ne s’ouvre pas automatiquement, ouvrez le menu contextuel du projet GenerateExternalDataLists, puis choisissez **ouvrir** .

8. Vérifiez que le fichier source. extension. vsixmanifest contient une entrée non vide (entrez Contoso) pour le champ auteur, enregistrez le fichier, puis fermez-le.

#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution **GenerateExternalDataLists** , choisissez **Ajouter**, puis **nouveau projet**.

2. Dans la boîte de dialogue **Ajouter un nouveau projet** , développez les nœuds **Visual C#** ou **Visual Basic** , puis choisissez le nœud **Windows** .

3. Dans la liste en haut de la boîte de dialogue, choisissez **.NET Framework 4,5**.

4. Dans la liste des modèles de projet, choisissez **bibliothèque de classes**.

5. Dans la zone **nom** , entrez **BdcProjectItemExtension**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le projet **BdcProjectItemExtension** à la solution et ouvre le fichier de code Class1 par défaut.

6. Supprimez le fichier de code Class1 du projet.

## <a name="configure-the-extension-project"></a>Configurer le projet d’extension
 Avant d’écrire du code pour créer l’extension d’élément de projet, ajoutez les fichiers de code et les références d’assembly au projet d’extension.

#### <a name="to-configure-the-project"></a>Pour configurer le projet

1. Dans le projet BdcProjectItemExtension, ajoutez deux fichiers de code portant les noms suivants :

    - ProjectItemExtension

    - GenerateExternalDataLists

2. Choisissez le projet BdcProjectItemExtension, puis, dans la barre de menus, choisissez **projet**  >  **Ajouter une référence**.

3. Sous le nœud **assemblys** , choisissez le nœud **Framework** , puis activez la case à cocher pour chacun des assemblys suivants :

    - System.ComponentModel.Composition

    - WindowsBase

4. Sous le nœud **assemblys** , choisissez le nœud **Extensions** , puis activez la case à cocher de l’assembly suivant :

    - Microsoft. VisualStudio. SharePoint

5. Choisissez le bouton **OK**.

## <a name="define-the-project-item-extension"></a>Définir l’extension d’élément de projet
 Créez une classe qui définit l’extension de l’élément de projet de **modèle de connectivité de données métiers** . Pour définir l’extension, la classe implémente l' <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interface. Implémentez cette interface chaque fois que vous souhaitez étendre un type existant d’élément de projet.

#### <a name="to-define-the-project-item-extension"></a>Pour définir l’extension d’élément de projet

1. Collez le code suivant dans le fichier de code ProjectItemExtension.

    > [!NOTE]
    > Après avoir ajouté ce code, le projet comportera des erreurs de compilation. Ces erreurs disparaissent lorsque vous ajoutez du code dans les étapes ultérieures.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb" id="Snippet1":::

## <a name="create-the-external-data-lists"></a>Créer les listes de données externes
 Ajoutez une définition partielle de la `GenerateExternalDataListsExtension` classe qui crée une liste de données externes pour chaque entité dans le modèle BDC. Pour créer la liste de données externes, ce code lit d’abord les données d’entité dans le modèle BDC en analysant les données XML dans le fichier de modèle BDC. Ensuite, il crée une instance de liste basée sur le modèle BDC et ajoute cette instance de liste au projet.

#### <a name="to-create-the-external-data-lists"></a>Pour créer les listes de données externes

1. Collez le code suivant dans le fichier de code GenerateExternalDataLists.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs" id="Snippet2":::

## <a name="checkpoint"></a>Point de contrôle
 À ce stade de la procédure pas à pas, tout le code de l’extension d’élément de projet se trouve maintenant dans le projet. Générez la solution pour vous assurer que le projet se compile sans erreur.

#### <a name="to-build-the-solution"></a>Pour générer la solution

1. Dans la barre de menus, choisissez **générer**  >  **générer la solution**.

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>Créer un package VSIX pour déployer l’extension d’élément de projet
 Pour déployer l’extension, utilisez le projet VSIX dans votre solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source. extension. vsixmanifest qui est inclus dans le projet VSIX. Ensuite, créez le package VSIX en générant la solution.

#### <a name="to-configure-and-create-the-vsix-package"></a>Pour configurer et créer le package VSIX

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du fichier source. extension. vsixmanifest dans le projet GenerateExternalDataLists, puis choisissez **ouvrir**.

     Visual Studio ouvre le fichier dans l’éditeur de manifeste. Le fichier source. extension. vsixmanifest est la base du fichier extension. vsixmanifest est requis par tous les packages VSIX. Pour plus d’informations sur ce fichier, consultez [Référence du schéma d’extension VSIX 1,0](/previous-versions/dd393700(v=vs.110)).

2. Dans la zone **nom du produit** , entrez générateur de liste de **données externes**.

3. Dans la zone **auteur** , entrez **contoso**.

4. Dans la zone **Description** , entrez **une extension pour les éléments de projet de modèle de connectivité de données métiers qui peuvent être utilisés pour générer des listes de données externes**.

5. Sous l’onglet **ressources** de l’éditeur, choisissez le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’affiche.

6. Dans la liste **type** , choisissez **Microsoft. VisualStudio. MEFComponent**.

    > [!NOTE]
    > Cette valeur correspond à l' `MefComponent` élément dans le fichier extension. vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MefComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

8. Dans la liste **projet** , choisissez **BdcProjectItemExtension**, puis cliquez sur le bouton **OK** .

9. Dans la barre de menus, choisissez **générer**  >  **générer la solution**.

10. Assurez-vous que le projet est compilé et généré sans erreurs.

11. Assurez-vous que le dossier de sortie de la génération pour le projet GenerateExternalDataLists contient maintenant le fichier GenerateExternalDataLists. vsix.

     Par défaut, le dossier de sortie de la génération est le.. dossier \bin\Debug sous le dossier qui contient votre fichier projet.

## <a name="test-the-project-item-extension"></a>Tester l’extension d’élément de projet
 Vous êtes maintenant prêt à tester l’extension d’élément de projet. Tout d’abord, commencez à déboguer le projet d’extension dans l’instance expérimentale de Visual Studio. Ensuite, utilisez l’extension dans l’instance expérimentale de Visual Studio pour générer une liste externe pour un modèle BDC. Enfin, ouvrez la liste externe sur le site SharePoint pour vérifier qu’elle fonctionne comme prévu.

#### <a name="to-start-debugging-the-extension"></a>Pour démarrer le débogage de l’extension

1. Si nécessaire, redémarrez Visual Studio avec les informations d’identification d’administration, puis ouvrez la solution GenerateExternalDataLists.

2. Dans le projet BdcProjectItemExtension, ouvrez le fichier de code ProjectItemExtension, puis ajoutez un point d’arrêt à la ligne de code dans la `Initialize` méthode.

3. Ouvrez le fichier de code GenerateExternalDataLists, puis ajoutez un point d’arrêt à la première ligne de code dans la `GenerateExternalDataLists_Execute` méthode.

4. Démarrez le débogage en choisissant la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**  >  **Démarrer le débogage**.

     Visual Studio installe l’extension de%UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External Data List Generator\1.0 et démarre une instance expérimentale de Visual Studio. Vous allez tester l’élément de projet dans cette instance de Visual Studio.

#### <a name="to-test-the-extension"></a>Pour tester l’extension

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **projet**.

2. Dans la boîte de dialogue **nouveau projet** , développez le nœud **modèles** , développez le nœud **Visual C#** , développez le nœud **SharePoint** , puis choisissez **2010**.

3. Dans la liste en haut de la boîte de dialogue, assurez-vous que **.NET Framework 3,5** est sélectionné. Les projets pour [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] nécessitent cette version du .NET Framework.

4. Dans la liste des modèles de projet, choisissez **projet SharePoint 2010**.

5. Dans la zone **nom** , entrez **SharePointProjectTestBDC**, puis choisissez le bouton **OK** .

6. Dans l’Assistant Personnalisation de SharePoint, entrez l’URL du site que vous souhaitez utiliser pour le débogage, choisissez **déployer en tant que solution de batterie**, puis choisissez le bouton **Terminer** .

7. Ouvrez le menu contextuel du projet SharePointProjectTestBDC, choisissez **Ajouter**, puis **nouvel élément**.

8. Dans la boîte de dialogue **Ajouter newItem-SharePointProjectTestBDC** , développez le nœud langue installée, puis développez le nœud **SharePoint** .

9. Choisissez le nœud **2010** , puis choisissez le modèle **modèle de connectivité de données métiers (solution de batterie uniquement)** .

10. Dans la zone **nom** , entrez **TestBDCModel**, puis cliquez sur le bouton **Ajouter** .

11. Vérifiez que le code de l’autre instance de Visual Studio s’arrête sur le point d’arrêt que vous avez défini dans la `Initialize` méthode du fichier de code ProjectItemExtension.

12. Dans l’instance arrêtée de Visual Studio, choisissez la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**  >  **Continuer** pour continuer à déboguer le projet.

13. Dans l’instance expérimentale de Visual Studio, choisissez la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**  >  **Démarrer le débogage** pour générer, déployer et exécuter le projet **TestBDCModel** .

     Le navigateur Web s’ouvre sur la page par défaut du site SharePoint spécifié pour le débogage.

14. Vérifiez que la section **listes** de la zone lancement rapide ne contient pas encore de liste basée sur le modèle BDC par défaut dans le projet. Vous devez d’abord créer une liste de données externes, soit à l’aide de l’interface utilisateur SharePoint, soit à l’aide de l’extension d’élément de projet.

15. Fermez le navigateur web.

16. Dans l’instance de Visual Studio sur laquelle le projet TestBDCModel est ouvert, ouvrez le menu contextuel du nœud **TestBDCModel** dans **Explorateur de solutions**, puis choisissez **générer la liste de données externes**.

17. Vérifiez que le code de l’autre instance de Visual Studio s’arrête sur le point d’arrêt que vous avez défini dans la `GenerateExternalDataLists_Execute` méthode. Appuyez sur la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**  >  **Continuer** pour continuer à déboguer le projet.

18. L’instance expérimentale de Visual Studio ajoute une instance de liste nommée **Entity1DataList** au projet TestBDCModel, et l’instance génère également une fonctionnalité nommée **feature2** pour l’instance de liste.

19. Appuyez sur la touche **F5** ou, dans la barre de menus, choisissez **Déboguer**  >  **Démarrer le débogage** pour générer, déployer et exécuter le projet TestBDCModel.

     Le navigateur Web s’ouvre sur la page par défaut du site SharePoint utilisé pour le débogage.

20. Dans la section **listes** de la zone lancement rapide, choisissez la liste **Entity1DataList** .

21. Vérifiez que la liste contient des colonnes nommées identificateur1 et message, en plus d’un élément qui a une valeur identificateur1 égale à 0 et une valeur de message de Hello World.

     Le modèle de projet de **modèle de connectivité de données métiers** génère le modèle BDC par défaut qui fournit toutes ces données.

22. Fermez le navigateur web.

## <a name="clean-up-the-development-computer"></a>Nettoyer l’ordinateur de développement
 Une fois que vous avez fini de tester l’extension d’élément de projet, supprimez la liste externe et le modèle BDC du site SharePoint et supprimez l’extension d’élément de projet de Visual Studio.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>Pour supprimer la liste de données externes du site SharePoint

1. Dans la zone lancement rapide du site SharePoint, choisissez la liste **Entity1DataList** .

2. Dans le ruban sur le site SharePoint, choisissez l’onglet **liste** .

3. Sous l’onglet **liste** , dans le groupe **paramètres** , choisissez **paramètres** de la liste.

4. Sous **autorisations et gestion**, choisissez **supprimer cette liste**, puis choisissez **OK** pour confirmer que vous souhaitez envoyer la liste à la corbeille.

5. Fermez le navigateur web.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>Pour supprimer le modèle BDC du site SharePoint

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **générer** un  >  **retrait**.

     Visual Studio supprime le modèle BDC du site SharePoint.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Pour supprimer l’extension d’élément de projet de Visual Studio

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **Outils**  >  **extensions et mises à jour**.

     La boîte de dialogue **Extensions et mises à jour** s’ouvre.

2. Dans la liste des extensions, choisissez **Générateur de listes de données externes**, puis cliquez sur le bouton **désinstaller** .

3. Dans la boîte de dialogue qui s’affiche, choisissez **Oui** pour confirmer que vous souhaitez désinstaller l’extension.

4. Choisissez **redémarrer maintenant** pour terminer la désinstallation.

5. Fermez les deux instances de Visual Studio (l’instance expérimentale et l’instance dans laquelle la solution GenerateExternalDataLists est ouverte).

## <a name="see-also"></a>Voir aussi
- [Étendre le système de projet SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Créer un modèle de connectivité de données métiers](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Concevoir un modèle de connectivité de données métiers](../sharepoint/designing-a-business-data-connectivity-model.md)