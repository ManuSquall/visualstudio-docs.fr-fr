---
title: Créer une étape de déploiement personnalisée pour les projets SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0053b279dfdc0fd80608efb7fb663cacf217f1c7
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984938"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Procédure pas à pas : création d’une étape de déploiement personnalisée pour les projets SharePoint
  Lorsque vous déployez un projet SharePoint, Visual Studio exécute une série d’étapes de déploiement dans un ordre spécifique. Visual Studio comprend de nombreuses étapes de déploiement intégrées, mais vous pouvez également créer les vôtres.

 Dans cette procédure pas à pas, vous allez créer une étape de déploiement personnalisée pour mettre à niveau des solutions sur un serveur qui exécute SharePoint. Visual Studio inclut des étapes de déploiement intégrées pour de nombreuses tâches, telles que le retrait ou l’ajout de solutions, mais il n’inclut pas d’étape de déploiement pour la mise à niveau des solutions. Par défaut, lorsque vous déployez une solution SharePoint, Visual Studio rétracte d’abord la solution (si elle est déjà déployée), puis redéploie l’intégralité de la solution. Pour plus d’informations sur les étapes de déploiement intégrées, consultez [déployer, publier et mettre à niveau des packages de solution SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

 Cette procédure pas à pas décrit les tâches suivantes :

- Création d’une extension Visual Studio qui effectue deux tâches principales :

  - L’extension définit une étape de déploiement personnalisée pour mettre à niveau des solutions SharePoint.

  - L’extension crée une extension de projet qui définit une nouvelle configuration de déploiement, qui est un ensemble d’étapes de déploiement qui sont exécutées pour un projet donné. La nouvelle configuration de déploiement comprend l’étape de déploiement personnalisée et plusieurs étapes de déploiement intégrées.

- Créez deux commandes SharePoint personnalisées appelées par l’assembly d’extension. Les commandes SharePoint sont des méthodes qui peuvent être appelées par des assemblys d’extension pour utiliser des API dans le modèle d’objet serveur pour SharePoint. Pour plus d’informations, consultez [appel des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

- Génération d’un package d’extension Visual Studio (VSIX) pour déployer les deux assemblys.

- Test de la nouvelle étape de déploiement.

## <a name="prerequisites"></a>Configuration requise
 Pour effectuer cette procédure pas à pas, vous avez besoin des composants suivants sur l’ordinateur de développement :

- Éditions prises en charge de Windows, SharePoint et Visual Studio.

- Le kit de développement logiciel (SDK) Visual Studio. Cette procédure pas à pas utilise le modèle de **projet VSIX** dans le kit de développement logiciel (SDK) pour créer un package VSIX afin de déployer l’extension. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).

  La connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer la procédure pas à pas :

- Utilisation du modèle d’objet serveur pour SharePoint. Pour plus d’informations, consultez [utilisation du modèle objet côté serveur SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee538251(v=office.14)).

- Solutions SharePoint. Pour plus d’informations, consultez [vue d’ensemble des solutions](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

- Mise à niveau des solutions SharePoint. Pour plus d’informations, consultez [mise à niveau d’une solution](/previous-versions/office/developer/sharepoint-2010/aa543659(v=office.14)).

## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez créer trois projets :

- Projet VSIX pour créer le package VSIX pour déployer l’extension.

- Projet de bibliothèque de classes qui implémente l’extension. Ce projet doit cibler le .NET Framework 4,5.

- Projet de bibliothèque de classes qui définit les commandes SharePoint personnalisées. Ce projet doit cibler le .NET Framework 3,5.

  Démarrez la procédure pas à pas en créant les projets.

#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX

1. Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.

3. Dans la boîte de dialogue **nouveau projet** , développez les nœuds  **C# Visual** ou **Visual Basic** , puis choisissez le nœud **extensibilité** .

    > [!NOTE]
    > Le nœud **extensibilité** est disponible uniquement si vous installez le kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez la section conditions préalables, plus haut dans cette rubrique.

4. En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework.

5. Choisissez le modèle de **projet VSIX** , nommez le projet **UpgradeDeploymentStep**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **UpgradeDeploymentStep** à **Explorateur de solutions**.

#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution UpgradeDeploymentStep, choisissez **Ajouter**, puis **nouveau projet**.

2. Dans la boîte de dialogue **nouveau projet** , développez les nœuds  **C# Visual** ou **Visual Basic** , puis choisissez le nœud **Windows** .

3. En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework.

4. Choisissez le modèle de projet **bibliothèque de classes** , nommez le projet **DeploymentStepExtension**, puis choisissez le bouton **OK** .

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **DeploymentStepExtension** à la solution et ouvre le fichier de code Class1 par défaut.

5. Supprimez le fichier de code Class1 du projet.

#### <a name="to-create-the-sharepoint-command-project"></a>Pour créer le projet de commande SharePoint

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution UpgradeDeploymentStep, choisissez **Ajouter**, puis **nouveau projet**.

2. Dans la boîte de dialogue **nouveau projet** , développez  **C# Visual** ou **Visual Basic**, puis choisissez le nœud **Windows** .

3. En haut de la boîte de dialogue, choisissez **.NET Framework 3,5** dans la liste des versions du .NET Framework.

4. Choisissez le modèle de projet **bibliothèque de classes** , nommez le projet **SharePointCommands**, puis choisissez le bouton **OK** .

     Visual Studio ajoute le projet **SharePointCommands** à la solution et ouvre le fichier de code Class1 par défaut.

5. Supprimez le fichier de code Class1 du projet.

## <a name="configure-the-projects"></a>Configurer les projets
 Avant d’écrire du code pour créer l’étape de déploiement personnalisée, vous devez ajouter des fichiers de code et des références d’assembly, et vous devez configurer les projets.

#### <a name="to-configure-the-deploymentstepextension-project"></a>Pour configurer le projet DeploymentStepExtension

1. Dans le projet **DeploymentStepExtension** , ajoutez deux fichiers de code portant les noms suivants :

    - UpgradeStep

    - DeploymentConfigurationExtension

2. Ouvrez le menu contextuel du projet DeploymentStepExtension, puis choisissez **Ajouter une référence**.

3. Sous l’onglet **Framework** , activez la case à cocher de l’assembly System. ComponentModel. composition.

4. Sous l’onglet **Extensions** , activez la case à cocher de l’assembly Microsoft. VisualStudio. SharePoint, puis choisissez le bouton **OK** .

#### <a name="to-configure-the-sharepointcommands-project"></a>Pour configurer le projet SharePointCommands

1. Dans le projet **SharePointCommands** , ajoutez un fichier de code nommé commandes.

2. Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **SharePointCommands** , puis choisissez **Ajouter une référence**.

3. Sous l’onglet **Extensions** , activez les cases à cocher pour les assemblys suivants, puis cliquez sur choisir le bouton **OK** .

    - Microsoft. SharePoint

    - Microsoft. VisualStudio. SharePoint. Commands

## <a name="define-the-custom-deployment-step"></a>Définir l’étape de déploiement personnalisée
 Créez une classe qui définit l’étape de déploiement de la mise à niveau. Pour définir l’étape de déploiement, la classe implémente l’interface <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>. Implémentez cette interface chaque fois que vous souhaitez définir une étape de déploiement personnalisée.

#### <a name="to-define-the-custom-deployment-step"></a>Pour définir l’étape de déploiement personnalisée

1. Dans le projet **DeploymentStepExtension** , ouvrez le fichier de code UpgradeStep, puis collez-y le code suivant.

    > [!NOTE]
    > Une fois que vous avez ajouté ce code, le projet rencontre des erreurs de compilation, mais il disparaît lorsque vous ajoutez du code dans les étapes ultérieures.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]

## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Créer une configuration de déploiement incluant l’étape de déploiement personnalisée
 Créez une extension de projet pour la nouvelle configuration de déploiement, qui comprend plusieurs étapes de déploiement intégrées et la nouvelle étape de déploiement de mise à niveau. En créant cette extension, vous aidez les développeurs SharePoint à utiliser l’étape de déploiement de mise à niveau dans les projets SharePoint.

 Pour créer la configuration de déploiement, la classe implémente l’interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>. Implémentez cette interface chaque fois que vous souhaitez créer une extension de projet SharePoint.

#### <a name="to-create-the-deployment-configuration"></a>Pour créer la configuration de déploiement

1. Dans le projet **DeploymentStepExtension** , ouvrez le fichier de code DeploymentConfigurationExtension, puis collez-y le code suivant.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]

## <a name="create-the-custom-sharepoint-commands"></a>Créer les commandes SharePoint personnalisées
 Créez deux commandes personnalisées qui appellent le modèle d’objet serveur pour SharePoint. Une commande détermine si une solution est déjà déployée ; l’autre commande met à niveau une solution.

#### <a name="to-define-the-sharepoint-commands"></a>Pour définir les commandes SharePoint

1. Dans le projet **SharePointCommands** , ouvrez le fichier de code Commands, puis collez le code suivant dans celui-ci.

     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]

## <a name="checkpoint"></a>Point de contrôle
 À ce stade de la procédure pas à pas, tout le code de l’étape de déploiement personnalisée et les commandes SharePoint se trouvent maintenant dans les projets. Générez-les pour vous assurer qu’elles se compilent sans erreur.

#### <a name="to-build-the-projects"></a>Pour générer les projets

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **DeploymentStepExtension** , puis choisissez **générer**.

2. Ouvrez le menu contextuel du projet **SharePointCommands** , puis choisissez **générer**.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Créer un package VSIX pour déployer l’extension
 Pour déployer l’extension, utilisez le projet VSIX dans votre solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source. extension. vsixmanifest dans le projet VSIX. Créez ensuite le package VSIX en générant la solution.

#### <a name="to-configure-and-create-the-vsix-package"></a>Pour configurer et créer le package VSIX

1. Dans **Explorateur de solutions**, sous le projet **UpgradeDeploymentStep** , ouvrez le menu contextuel du fichier **source. extension. vsixmanifest** , puis choisissez **ouvrir**.

     Visual Studio ouvre le fichier dans l’éditeur de manifeste. Le fichier source. extension. vsixmanifest est la base du fichier extension. vsixmanifest requis par tous les packages VSIX. Pour plus d’informations sur ce fichier, consultez [Référence du schéma d’extension VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).

2. Dans la zone **nom du produit** , entrez **étape de déploiement de la mise à niveau pour les projets SharePoint**.

3. Dans la zone **auteur** , entrez **contoso**.

4. Dans la zone **Description** , entrez **fournit une étape de déploiement de mise à niveau personnalisée qui peut être utilisée dans les projets SharePoint**.

5. Sous l’onglet **ressources** de l’éditeur, choisissez le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’affiche.

6. Dans la liste **type** , choisissez **Microsoft. VisualStudio. MEFComponent**.

    > [!NOTE]
    > Cette valeur correspond à l’élément `MefComponent` dans le fichier extension. vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MefComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).

7. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

8. Dans la liste **projet** , choisissez **DeploymentStepExtension**, puis cliquez sur le bouton **OK** .

9. Dans l’éditeur de manifeste, cliquez à nouveau sur le bouton **nouveau** .

     La boîte de dialogue **Ajouter un nouvel élément** multimédia s’affiche.

10. Dans la liste **type** , entrez **SharePoint. Commands. v4**.

    > [!NOTE]
    > Cet élément spécifie une extension personnalisée que vous souhaitez inclure dans l’extension Visual Studio. Pour plus d’informations, consultez [élément Asset (schéma VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).

11. Dans la liste **source** , choisissez **un projet dans la solution actuelle**.

12. Dans la liste **projet** , choisissez **SharePointCommands**, puis le bouton **OK** .

13. Dans la barre de menus, choisissez **générer** > **générer la solution**, puis assurez-vous que la solution est compilée sans erreurs.

14. Assurez-vous que le dossier de sortie de la génération pour le projet UpgradeDeploymentStep contient désormais le fichier UpgradeDeploymentStep. vsix.

     Par défaut, le dossier de sortie de la génération est le.. dossier \bin\Debug sous le dossier qui contient votre fichier projet.

## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Préparer le test de l’étape de déploiement de la mise à niveau
 Pour tester l’étape de déploiement de la mise à niveau, vous devez d’abord déployer un exemple de solution sur le site SharePoint. Commencez par déboguer l’extension dans l’instance expérimentale de Visual Studio. Créez ensuite une définition de liste et une instance de liste à utiliser pour tester l’étape de déploiement, puis déployez-la sur le site SharePoint. Ensuite, modifiez la définition de liste et l’instance de liste, puis Redéployez-les pour montrer comment le processus de déploiement par défaut remplace les solutions sur le site SharePoint.

 Plus loin dans cette procédure pas à pas, vous modifierez la définition de liste et l’instance de liste, puis vous les mettrez à niveau sur le site SharePoint.

#### <a name="to-start-debugging-the-extension"></a>Pour démarrer le débogage de l’extension

1. Redémarrez Visual Studio avec les informations d’identification d’administration, puis ouvrez la solution UpgradeDeploymentStep.

2. Dans le projet DeploymentStepExtension, ouvrez le fichier de code UpgradeStep, puis ajoutez un point d’arrêt à la première ligne de code dans les méthodes `CanExecute` et `Execute`.

3. Démarrez le débogage en choisissant la touche **F5** ou, dans la barre de menus, en choisissant **déboguer** > **Démarrer le débogage**.

4. Visual Studio installe l’extension à l’étape de déploiement%UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade pour SharePoint Projects\1.0 et démarre une instance expérimentale de Visual Studio. Vous allez tester l’étape de déploiement de la mise à niveau dans cette instance de Visual Studio.

#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Pour créer un projet SharePoint avec une définition de liste et une instance de liste

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **fichier** > **nouveau** > **projet**.

2. Dans la boîte de dialogue **nouveau projet** , développez le nœud **visuel C#**  ou le nœud **Visual Basic** , développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

3. En haut de la boîte de dialogue, assurez-vous que **.NET Framework 3,5** s’affiche dans la liste des versions du .NET Framework.

    Les projets pour [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] nécessitent cette version du .NET Framework.

4. Dans la liste des modèles de projet, choisissez **projet SharePoint 2010**, nommez le projet **EmployeesListDefinition**, puis choisissez le bouton **OK** .

5. Dans l' **Assistant Personnalisation de SharePoint**, entrez l’URL du site que vous souhaitez utiliser pour le débogage.

6. Sous **quel est le niveau de confiance de cette solution SharePoint**, sélectionnez la case **d’option déployer en tant que solution de batterie** .

   > [!NOTE]
   > L’étape de déploiement de la mise à niveau ne prend pas en charge les solutions sandbox.

7. Choisissez le bouton **Terminer** .

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet EmployeesListDefinition.

8. Ouvrez le menu contextuel du projet EmployeesListDefinition, choisissez **Ajouter**, puis **nouvel élément**.

9. Dans la boîte de dialogue **Ajouter un nouvel élément-EmployeesListDefinition** , développez le nœud **SharePoint** , puis choisissez le nœud **2010** .

10. Choisissez le modèle d’élément de **liste** , nommez la **liste Item Employees**, puis choisissez le bouton **Ajouter** .

     L’Assistant Personnalisation de SharePoint s’affiche.

11. Dans la page **choisir les paramètres de liste** , vérifiez les paramètres suivants, puis choisissez le bouton **Terminer** :

    1. La **liste employés** apparaît dans la zone **quel nom voulez-vous afficher pour votre liste ?** .

    2. La case **d’option créer une liste personnalisable basée sur :** est sélectionnée.

    3. La **valeur par défaut (vide)** est choisie dans la liste **créer une liste personnalisable basée sur :** .

       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée l’élément de liste Employees avec une colonne title et une instance vide unique et ouvre le concepteur de listes.

12. Dans le concepteur de listes, sous l’onglet **colonnes** , choisissez la ligne **tapez un nom de colonne nouveau ou existant** , puis ajoutez les colonnes suivantes dans la liste **nom complet** de la colonne :

    1. Prénom

    2. Société

    3. Téléphone professionnel

    4. Courriel

13. Enregistrez tous les fichiers, puis fermez le concepteur de listes.

14. Dans **Explorateur de solutions**, développez le nœud **Employees List** , puis développez le nœud **Employees List instance** enfant.

15. Dans le fichier *Elements. xml* , remplacez le code XML par défaut dans ce fichier par le code XML suivant. Ce code XML modifie le nom de la liste en **Employees** et ajoute des informations pour un employé nommé Jim Hance.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
        <Data>
          <Rows>
            <Row>
              <Field Name="Title">Hance</Field>
              <Field Name="FirstName">Jim</Field>
              <Field Name="Company">Contoso</Field>
              <Field Name="Business Phone">555-555-5555</Field>
              <Field Name="E-Mail">jim@contoso.com</Field>
            </Row>
          </Rows>
        </Data>
      </ListInstance>
    </Elements>
    ```

16. Enregistrez et fermez le fichier *Elements. xml* .

17. Ouvrez le menu contextuel du projet EmployeesListDefinition, puis choisissez **ouvrir** ou **Propriétés**.

     Le concepteur de propriétés s’ouvre.

18. Sous l’onglet **SharePoint** , désactivez la case à cocher **retrait automatique après le débogage** , puis enregistrez les propriétés.

#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Pour déployer la définition de liste et l’instance de liste

1. Dans **Explorateur de solutions**, choisissez le nœud de projet **EmployeesListDefinition** .

2. Dans la fenêtre **Propriétés** , assurez-vous que la propriété **configuration du déploiement actif** est définie sur **par défaut**.

3. Appuyez sur la touche **F5** ou, dans la barre de menus, choisissez **déboguer** > **Démarrer le débogage**.

4. Vérifiez que le projet est correctement généré, que le navigateur Web ouvre sur le site SharePoint, que l’élément **listes** dans la barre lancement rapide comprend la nouvelle liste **employés** et que la liste **employés** comprend l’entrée pour Jim Hance.

5. Fermez le navigateur web.

#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Pour modifier la définition de liste et l’instance de liste, puis les redéployer

1. Dans le projet EmployeesListDefinition, ouvrez le fichier *Elements. xml* qui est un enfant de l’élément de projet de l' **instance Employee List** .

2. Supprimez l’élément `Data` et ses enfants pour supprimer l’entrée de Jim Hance dans la liste.

     Lorsque vous avez terminé, le fichier doit contenir le code XML suivant.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">
      <ListInstance Title="Employees"
                    OnQuickLaunch="TRUE"
                    TemplateType="10000"
                    Url="Lists/Employees"
                    Description="Simple list to test upgrade deployment step">
      </ListInstance>
    </Elements>
    ```

3. Enregistrez et fermez le fichier *Elements. xml* .

4. Ouvrez le menu contextuel de l’élément de projet **List Employees** , puis choisissez **ouvrir** ou **Propriétés**.

5. Dans le concepteur de listes, choisissez l’onglet **vues** .

6. Dans la liste **colonnes sélectionnées** , choisissez **pièces jointes**, puis appuyez sur la touche < pour déplacer cette colonne vers la liste **colonnes disponibles** .

7. Répétez l’étape précédente pour déplacer la colonne de **téléphone professionnel** de la liste **colonnes sélectionnées** vers la liste **colonnes disponibles** .

     Cette action supprime ces champs de la vue par défaut de la liste **Employees** sur le site SharePoint.

8. Démarrez le débogage en choisissant la touche **F5** ou, dans la barre de menus, en choisissant **déboguer** > **Démarrer le débogage**.

9. Vérifiez que la boîte de dialogue **conflits de déploiement** s’affiche.

     Cette boîte de dialogue apparaît lorsque Visual Studio tente de déployer une solution (l’instance de liste) sur un site SharePoint sur lequel cette solution a déjà été déployée. Cette boîte de dialogue ne s’affiche pas lorsque vous exécutez l’étape de déploiement de mise à niveau plus loin dans cette procédure pas à pas.

10. Dans la boîte de dialogue **conflits de déploiement** , sélectionnez la case d’option **résoudre automatiquement** .

     Visual Studio supprime l’instance de liste sur le site SharePoint, déploie l’élément de liste dans le projet, puis ouvre le site SharePoint.

11. Dans la section **listes** de la barre lancement rapide, choisissez la liste **employés** , puis vérifiez les informations suivantes :

    - Les colonnes **pièces jointes** et **Téléphone privé** ne s’affichent pas dans cette vue de la liste.

    - La liste est vide. Lorsque vous avez utilisé la configuration de déploiement **par défaut** pour redéployer la solution, la liste des **employés** a été remplacée par la nouvelle liste vide dans votre projet.

## <a name="test-the-deployment-step"></a>Tester l’étape de déploiement
 Vous êtes maintenant prêt à tester l’étape de déploiement de la mise à niveau. Tout d’abord, ajoutez un élément à l’instance de liste dans SharePoint. Modifiez ensuite la définition de liste et l’instance de liste, mettez-les à niveau sur le site SharePoint et confirmez que l’étape de déploiement de la mise à niveau ne remplace pas le nouvel élément.

#### <a name="to-manually-add-an-item-to-the-list"></a>Pour ajouter manuellement un élément à la liste

1. Dans le ruban sur le site SharePoint, sous l’onglet **outils de liste** , choisissez l’onglet **éléments** .

2. Dans le **nouveau** groupe, choisissez **nouvel élément**.

     Vous pouvez également choisir le lien **Ajouter un nouvel élément** dans la liste d’éléments.

3. Dans la fenêtre **employés-nouvel élément** , dans la zone **titre** , entrez **Gestionnaire d’outils**.

4. Dans la zone **prénom** , entrez **Andy**.

5. Dans la zone **société** , tapez **contoso**.

6. Choisissez le bouton **Enregistrer** , vérifiez que le nouvel élément apparaît dans la liste, puis fermez le navigateur Web.

     Plus loin dans cette procédure pas à pas, vous utiliserez cet élément pour vérifier que l’étape de déploiement de la mise à niveau ne remplace pas le contenu de cette liste.

#### <a name="to-test-the-upgrade-deployment-step"></a>Pour tester l’étape de déploiement de la mise à niveau

1. Dans l’instance expérimentale de Visual Studio, dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **EmployeesListDefinition** , puis choisissez **Propriétés**.

    L’éditeur/concepteur de propriétés s’ouvre.

2. Sous l’onglet **SharePoint** , définissez la propriété **configuration du déploiement actif** sur **mettre à niveau**.

    Cette configuration de déploiement personnalisée comprend la nouvelle étape de déploiement de mise à niveau.

3. Ouvrez le menu contextuel de l’élément de projet **List Employees** , puis choisissez **Propriétés** ou **ouvrir**.

    L’éditeur/concepteur de propriétés s’ouvre.

4. Sous l’onglet **vues** , choisissez la **colonne courrier électronique** , puis la clé **<** pour déplacer cette colonne de la liste **colonnes sélectionnées** vers la liste **colonnes disponibles** .

    Cette action supprime ces champs de la vue par défaut de la liste **Employees** sur le site SharePoint.

5. Démarrez le débogage en choisissant la touche **F5** ou, dans la barre de menus, en choisissant **déboguer** > **Démarrer le débogage**.

6. Vérifiez que le code de l’autre instance de Visual Studio s’arrête sur le point d’arrêt que vous avez défini précédemment dans la méthode `CanExecute`.

7. Appuyez de nouveau sur la touche **F5** ou, dans la barre de menus, choisissez **déboguer** > **Continuer**.

8. Vérifiez que le code s’arrête sur le point d’arrêt que vous avez défini précédemment dans la méthode `Execute`.

9. Appuyez sur la touche **F5** ou, dans la barre de menus, choisissez **déboguer** > **Continuer** une dernière fois.

     Le navigateur Web ouvre le site SharePoint.

10. Dans la section **listes** de la zone lancement rapide, choisissez la liste **employés** , puis vérifiez les informations suivantes :

    - L’élément que vous avez ajouté manuellement (pour Andy, le gestionnaire d’installations) figure toujours dans la liste.

    - Les colonnes **téléphone professionnel** et **adresse de messagerie** ne s’affichent pas dans cette vue de la liste.

      La configuration de déploiement de la **mise à niveau** modifie l’instance de liste **Employees** existante sur le site SharePoint. Si vous avez utilisé la configuration de déploiement **par défaut** au lieu de la configuration de la **mise à niveau** , vous rencontrerez un conflit de déploiement. Visual Studio peut résoudre le conflit en remplaçant la liste **Employees** , et l’élément pour Andy, le gestionnaire d’installations, serait supprimé.

## <a name="clean-up-the-development-computer"></a>Nettoyer l’ordinateur de développement
 Une fois que vous avez terminé le test de l’étape de déploiement de la mise à niveau, supprimez l’instance de liste et la définition de liste du site SharePoint, puis supprimez l’extension d’étape de déploiement de Visual Studio.

#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Pour supprimer l’instance de liste du site SharePoint

1. Ouvrez la liste **employés** sur le site SharePoint, si la liste n’est pas déjà ouverte.

2. Dans le ruban sur le site SharePoint, choisissez l’onglet **outils de liste** , puis choisissez l’onglet **liste** .

3. Dans le groupe **paramètres** , choisissez l’élément **paramètres de liste** .

4. Sous **autorisations et gestion**, choisissez la commande **supprimer cette liste** , choisissez **OK** pour confirmer que vous souhaitez envoyer la liste à la corbeille, puis fermez le navigateur Web.

#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Pour supprimer la définition de liste du site SharePoint

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **générer** > **retirer**.

     Visual Studio rétracte la définition de liste à partir du site SharePoint.

#### <a name="to-uninstall-the-extension"></a>Pour désinstaller l'extension

1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **outils** > **extensions et mises à jour**.

     La boîte de dialogue **Extensions et mises à jour** s’ouvre.

2. Dans la liste des extensions, choisissez **mettre à niveau l’étape de déploiement pour les projets SharePoint**, puis choisissez la commande de **désinstallation** .

3. Dans la boîte de dialogue qui s’affiche, choisissez **Oui** pour confirmer que vous souhaitez désinstaller l’extension, puis choisissez **redémarrer maintenant** pour terminer la désinstallation.

4. Fermez les deux instances de Visual Studio (l’instance expérimentale et l’instance de Visual Studio dans laquelle la solution UpgradeDeploymentStep est ouverte).

## <a name="see-also"></a>Voir aussi
- [Étendre le déploiement et l’empaquetage SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
