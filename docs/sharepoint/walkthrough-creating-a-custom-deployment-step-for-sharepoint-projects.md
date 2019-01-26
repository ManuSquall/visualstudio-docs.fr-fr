---
title: 'Procédure pas à pas : Création d’une étape de déploiement personnalisée pour les projets SharePoint | Microsoft Docs'
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
ms.openlocfilehash: 41f0160b173c07859480aa4a6242acae573374e5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871297"
---
# <a name="walkthrough-create-a-custom-deployment-step-for-sharepoint-projects"></a>Procédure pas à pas : Créer une étape de déploiement personnalisée pour les projets SharePoint
  Lorsque vous déployez un projet SharePoint, Visual Studio exécute une série d’étapes de déploiement dans un ordre spécifique. Visual Studio inclut de nombreuses étapes de déploiement intégrées, mais vous pouvez également créer les vôtres.  
  
 Dans cette procédure pas à pas, vous allez créer une étape de déploiement personnalisée pour mettre à niveau des solutions sur un serveur qui exécute SharePoint. Visual Studio inclut des étapes de déploiement intégrées pour nombreuses tâches, ces retrait ou ajout de solutions, mais il n’inclut pas une étape de déploiement de solutions de mise à niveau. Par défaut, lorsque vous déployez une solution SharePoint, Visual Studio tout d’abord permet de retirer la solution (si elle est déjà déployée) avant de redéployer la solution entière. Pour plus d’informations sur les étapes de déploiement intégrées, consultez [déployer, publier et mettre à niveau de packages de solution SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 Cette procédure pas à pas décrit les tâches suivantes :  
  
-   Création d’une extension Visual Studio qui exécute deux tâches principales :  
  
    -   L’extension définit une étape de déploiement personnalisée pour mettre à niveau des solutions SharePoint.  
  
    -   L’extension crée une extension de projet qui définit une nouvelle configuration de déploiement, qui est un ensemble d’étapes de déploiement exécutées pour un projet donné. La nouvelle configuration de déploiement inclut l’étape de déploiement personnalisée et plusieurs étapes de déploiement intégrées.  
  
-   Créez deux commandes SharePoint personnalisés qui appelle l’assembly d’extension. Les commandes SharePoint sont des méthodes qui peuvent être appelées par les assemblys d’extension à utiliser des API dans le modèle objet serveur pour SharePoint. Pour plus d’informations, consultez [appeler des modèles d’objet SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Création d’un package d’Extension Visual Studio (VSIX) pour déployer les deux assemblys.  
  
-   Test de la nouvelle étape de déploiement.  
  
## <a name="prerequisites"></a>Prérequis  
 Vous avez besoin des composants suivants sur l’ordinateur de développement pour effectuer cette procédure pas à pas :  
  
- Éditions prises en charge de Windows, SharePoint et Visual Studio.
  
- Le Kit de développement logiciel avec Visual Studio. Cette procédure pas à pas utilise le **projet VSIX** modèle dans le Kit de développement logiciel pour créer un package VSIX pour déployer l’extension. Pour plus d’informations, consultez [étendre les outils SharePoint dans Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
  Connaissance des concepts suivants est utile, mais pas obligatoire, pour suivre la procédure pas à pas :  
  
- Utilisation du modèle d’objet de serveur pour SharePoint. Pour plus d’informations, consultez [à l’aide du modèle d’objet SharePoint Foundation côté serveur](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
- Solutions SharePoint. Pour plus d’informations, consultez [vue d’ensemble des Solutions](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
- Mise à niveau des solutions SharePoint. Pour plus d’informations, consultez [la mise à niveau une Solution](http://go.microsoft.com/fwlink/?LinkId=177802).  
  
## <a name="create-the-projects"></a>Créer les projets
 Pour effectuer cette procédure pas à pas, vous devez créer trois projets :  
  
- Un projet VSIX pour créer le package VSIX pour déployer l’extension.  
  
- Un projet de bibliothèque de classes qui implémente l’extension. Ce projet doit cibler le .NET Framework 4.5.  
  
- Un projet de bibliothèque de classes qui définit les commandes SharePoint personnalisées. Ce projet doit cibler le .NET Framework 3.5.  
  
  Démarrer la procédure pas à pas en créant les projets.  
  
#### <a name="to-create-the-vsix-project"></a>Pour créer le projet VSIX  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, puis choisissez le **extensibilité** nœud.  
  
    > [!NOTE]  
    >  Le **extensibilité** nœud est disponible uniquement si vous installez le SDK Visual Studio. Pour plus d’informations, consultez la section conditions préalables plus haut dans cette rubrique.  
  
4.  En haut de la boîte de dialogue, choisissez **.NET Framework 4.5** dans la liste des versions du .NET Framework.  
  
5.  Choisissez le **projet VSIX** modèle, nommez le projet **UpgradeDeploymentStep**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **UpgradeDeploymentStep** projet **l’Explorateur de solutions**.  
  
#### <a name="to-create-the-extension-project"></a>Pour créer le projet d’extension  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud de solution UpgradeDeploymentStep, choisissez **ajouter**, puis choisissez **nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** ou **Visual Basic** nœuds, puis choisissez le **Windows** nœud.  
  
3.  En haut de la boîte de dialogue, choisissez **.NET Framework 4.5** dans la liste des versions du .NET Framework.  
  
4.  Choisissez le **bibliothèque de classes** modèle de projet, nommez le projet **DeploymentStepExtension**, puis choisissez le **OK** bouton.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ajoute le **DeploymentStepExtension** projet à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprimer le fichier de code Class1 du projet.  
  
#### <a name="to-create-the-sharepoint-command-project"></a>Pour créer le projet de commande SharePoint  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le nœud de solution UpgradeDeploymentStep, choisissez **ajouter**, puis choisissez **nouveau projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue, développez **Visual C#** ou **Visual Basic**, puis choisissez le **Windows** nœud.  
  
3.  En haut de la boîte de dialogue, choisissez **.NET Framework 3.5** dans la liste des versions du .NET Framework.  
  
4.  Choisissez le **bibliothèque de classes** modèle de projet, nommez le projet **SharePointCommands**, puis choisissez le **OK** bouton.  
  
     Visual Studio ajoute le **SharePointCommands** projet à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprimer le fichier de code Class1 du projet.  
  
## <a name="configure-the-projects"></a>Configurer les projets
 Avant d’écrire du code pour créer une étape de déploiement personnalisé, vous devez ajouter les fichiers de code et des références d’assembly, et vous devez configurer les projets.  
  
#### <a name="to-configure-the-deploymentstepextension-project"></a>Pour configurer le projet DeploymentStepExtension
  
1.  Dans le **DeploymentStepExtension** de projet, ajoutez deux fichiers de code qui portent les noms suivants :  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Ouvrez le menu contextuel sur le projet DeploymentStepExtension, puis choisissez **ajouter une référence**.  
  
3.  Sur le **Framework** , sélectionnez la case à cocher pour l’assembly System.ComponentModel.Composition.  
  
4.  Sur le **Extensions** onglet, activez la case à cocher pour l’assembly Microsoft.VisualStudio.SharePoint, puis choisissez le **OK** bouton.  
  
#### <a name="to-configure-the-sharepointcommands-project"></a>Pour configurer le projet SharePointCommands
  
1.  Dans le **SharePointCommands** de projet, ajoutez un fichier de code qui est nommé de commandes.  
  
2.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel sur le **SharePointCommands** nœud de projet, puis choisissez **ajouter une référence**.  
  
3.  Sur le **Extensions** onglet, activez les cases à cocher pour les assemblys suivants, puis cliquez sur le **OK** bouton  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## <a name="define-the-custom-deployment-step"></a>Définir l’étape de déploiement personnalisé
 Créez une classe qui définit l’étape de déploiement de mise à niveau. Pour définir l’étape de déploiement, la classe implémente le <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interface. Implémentez cette interface chaque fois que vous souhaitez définir une étape de déploiement personnalisé.  
  
#### <a name="to-define-the-custom-deployment-step"></a>Pour définir l’étape de déploiement personnalisé  
  
1.  Dans le **DeploymentStepExtension** de projet, ouvrez le fichier de code UpgradeStep, puis collez-y le code suivant.  
  
    > [!NOTE]  
    >  Après avoir ajouté ce code, le projet aura des erreurs de compilation, mais disparaissent lorsque vous ajoutez code dans les étapes ultérieures.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#1)]  
  
## <a name="create-a-deployment-configuration-that-includes-the-custom-deployment-step"></a>Créer une configuration de déploiement qui comprend l’étape de déploiement personnalisé
 Créer une extension de projet pour la nouvelle configuration de déploiement, ce qui inclut plusieurs étapes de déploiement intégrées et la nouvelle étape de déploiement de mise à niveau. En créant cette extension, vous aider les développeurs SharePoint à utiliser l’étape de déploiement de mise à niveau dans les projets SharePoint.  
  
 Pour créer la configuration de déploiement, la classe implémente le <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interface. Implémentez cette interface chaque fois que vous souhaitez créer une extension de projet SharePoint.  
  
#### <a name="to-create-the-deployment-configuration"></a>Pour créer la configuration de déploiement  
  
1.  Dans le **DeploymentStepExtension** de projet, ouvrez le fichier de code DeploymentConfigurationExtension, puis collez-y le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## <a name="create-the-custom-sharepoint-commands"></a>Créer les commandes SharePoint personnalisées
 Créez deux commandes personnalisées qui appellent le modèle d’objet serveur pour SharePoint. Une seule commande détermine si une solution est déjà déployée ; l’autre commande met à niveau une solution.  
  
#### <a name="to-define-the-sharepoint-commands"></a>Pour définir les commandes SharePoint  
  
1.  Dans le **SharePointCommands** de projet, ouvrez le fichier de code de commandes, puis collez-y le code suivant.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#4)]  
  
## <a name="checkpoint"></a>Point de contrôle  
 À ce stade dans la procédure pas à pas, l’intégralité du code pour l’étape de déploiement personnalisés et les commandes SharePoint sont maintenant dans les projets. Les générer pour vous assurer qu’ils erreurs de compilation.  
  
#### <a name="to-build-the-projects"></a>Pour générer les projets  
  
1.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **DeploymentStepExtension** de projet, puis choisissez **Build**.  
  
2.  Ouvrez le menu contextuel pour le **SharePointCommands** de projet, puis choisissez **Build**.  
  
## <a name="create-a-vsix-package-to-deploy-the-extension"></a>Créer un package VSIX pour déployer l’extension
 Pour déployer l’extension, utilisez le projet VSIX dans votre solution pour créer un package VSIX. Tout d’abord, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest dans le projet VSIX. Puis créer le package VSIX en générant la solution.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Pour configurer et créer le package VSIX  
  
1.  Dans **l’Explorateur de solutions**, sous le **UpgradeDeploymentStep** de projet, ouvrez le menu contextuel pour le **source.extension.vsixmanifest** de fichiers, puis choisissez  **Ouvrez**.  
  
     Visual Studio ouvre le fichier dans l’éditeur de manifeste. Le fichier source.extension.vsixmanifest est la base du fichier extension.vsixmanifest qui nécessitent de tous les packages VSIX. Pour plus d’informations sur ce fichier, consultez [VSIX Extension schéma 1.0 référence](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Dans le **Product Name** , entrez **étape de déploiement de mise à niveau pour les projets SharePoint**.  
  
3.  Dans le **auteur** , entrez **Contoso**.  
  
4.  Dans le **Description** , entrez **fournit une étape de déploiement de mise à niveau personnalisé qui peut être utilisée dans les projets SharePoint**.  
  
5.  Dans le **actifs** onglet de l’éditeur, choisissez le **New** bouton.  
  
     Le **ajouter un nouveau composant** boîte de dialogue s’affiche.  
  
6.  Dans le **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à la `MefComponent` élément dans le fichier extension.vsixmanifest. Cet élément spécifie le nom d’un assembly d’extension dans le package VSIX. Pour plus d’informations, consultez [MEFComponent, élément (schéma VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  Dans le **Source** , choisissez **un projet dans la solution actuelle**.  
  
8.  Dans le **projet** , choisissez **DeploymentStepExtension**, puis choisissez le **OK** bouton.  
  
9. Dans l’éditeur de manifeste, choisissez le **New** bouton à nouveau.  
  
     Le **ajouter un nouveau composant** boîte de dialogue s’affiche.  
  
10. Dans le **Type** liste, entrez **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Cet élément spécifie une extension personnalisée que vous souhaitez inclure dans l’extension de Visual Studio. Pour plus d’informations, consultez [Asset, élément (schéma VSX)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. Dans le **Source** , choisissez **un projet dans la solution actuelle**.  
  
12. Dans le **projet** , choisissez **SharePointCommands**, puis choisissez le **OK** bouton.  
  
13. Dans la barre de menus, choisissez **Build** > **générer la Solution**, puis assurez-vous que la solution est compilée sans erreurs.  
  
14. Assurez-vous que le dossier de sortie pour le projet UpgradeDeploymentStep contienne maintenant le fichier UpgradeDeploymentStep.vsix.  
  
     Par défaut, le dossier de sortie est le... dossier \bin\debug sous le dossier qui contient votre fichier projet.  
  
## <a name="prepare-to-test-the-upgrade-deployment-step"></a>Préparer le test de l’étape de déploiement de mise à niveau
 Pour tester l’étape de déploiement de mise à niveau, vous devez tout d’abord déployer un exemple de solution sur le site SharePoint. Commencez par déboguer l’extension dans l’instance expérimentale de Visual Studio. Puis créez une définition de liste et une instance de liste à utiliser pour tester l’étape de déploiement et ensuite les déployer sur le site SharePoint. Ensuite, modifiez la définition de liste et l’instance de liste et les redéployer pour illustrer la façon dont le processus de déploiement par défaut remplace les solutions sur le site SharePoint.  
  
 Plus loin dans cette procédure pas à pas, vous allez modifier la définition de liste et l’instance de liste, puis vous allez mettre à niveau sur le site SharePoint.  
  
#### <a name="to-start-debugging-the-extension"></a>Pour démarrer le débogage de l’extension  
  
1.  Redémarrez Visual Studio en tant qu’administrateur et ouvrez la solution UpgradeDeploymentStep.  
  
2.  Dans le projet DeploymentStepExtension, ouvrez le fichier de code UpgradeStep, puis ajoutez un point d’arrêt à la première ligne de code dans le `CanExecute` et `Execute` méthodes.  
  
3.  Démarrer le débogage en choisissant le **F5** clé ou, dans la barre de menus, choisissez **déboguer** > **démarrer le débogage**.  
  
4.  Visual Studio installe l’extension %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Upgrade étape de déploiement pour SharePoint Projects\1.0 et démarre une instance expérimentale de Visual Studio. Vous allez tester l’étape de déploiement de mise à niveau dans cette instance de Visual Studio.  
  
#### <a name="to-create-a-sharepoint-project-with-a-list-definition-and-a-list-instance"></a>Pour créer un projet SharePoint avec une définition de liste et une instance de liste  
  
1. Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **fichier** > **New** > **projet**.  
  
2. Dans le **nouveau projet** boîte de dialogue, développez le **Visual C#** nœud ou le **Visual Basic** nœud, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
3. En haut de la boîte de dialogue, assurez-vous que **.NET Framework 3.5** apparaît dans la liste des versions du .NET Framework.  
  
    Pour les projets [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] requièrent cette version du .NET Framework.  
  
4. Dans la liste des modèles de projet, choisissez **projet SharePoint 2010**, nommez le projet **DéfinitionListeEmployés**, puis choisissez le **OK** bouton.  
  
5. Dans le **Assistant Personnalisation de SharePoint**, entrez l’URL du site que vous souhaitez utiliser pour le débogage.  
  
6. Sous **quel est le niveau de confiance de cette solution SharePoint**, choisissez le **déployer en tant que solution de batterie** case d’option.  
  
   > [!NOTE]  
   >  L’étape de déploiement de mise à niveau ne prend pas en charge les solutions sandbox.  
  
7. Choisissez le **Terminer** bouton.  
  
    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet DéfinitionListeEmployés.  
  
8. Ouvrez le menu contextuel pour le projet DéfinitionListeEmployés, choisissez **ajouter**, puis choisissez **un nouvel élément**.  
  
9. Dans le **ajouter un nouvel élément - DéfinitionListeEmployés** boîte de dialogue, développez le **SharePoint** nœud, puis choisissez le **2010** nœud.  
  
10. Choisissez le **liste** modèle d’élément, nommez l’élément **liste d’employés**, puis choisissez le **ajouter** bouton.  
  
     L’Assistant de personnalisation de SharePoint s’affiche  
  
11. Sur le **choisir les paramètres de liste** page, vérifiez les paramètres suivants, puis choisissez le **Terminer** bouton :  
  
    1. **Liste des employés** s’affiche dans le **quel nom voulez-vous afficher pour votre liste ?** boîte.  
  
    2. Le **créer une liste personnalisable basée sur :** case d’option est sélectionnée.  
  
    3. **Par défaut (vide)** est choisi dans la **créer une liste personnalisable basée sur :** liste.  
  
       [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée l’élément de liste d’employés avec une colonne de titre et une seule instance vide et ouvre le Concepteur de la liste.  
  
12. Dans le Concepteur de la liste, sur le **colonnes** , choisir le **tapez un nom de colonne nouveau ou existant** de ligne, puis ajoutez les colonnes suivantes dans le **colonne nom d’affichage** liste :  
  
    1.  Prénom  
  
    2.  Société  
  
    3.  Téléphone professionnel  
  
    4.  Courrier électronique  
  
13. Enregistrez tous les fichiers, puis fermez le Concepteur de liste.  
  
14. Dans **l’Explorateur de solutions**, développez le **liste d’employés** nœud, puis développez le **Instance de liste d’employés** nœud enfant.  
  
15. Dans le *Elements.xml* de fichier, remplacez le XML dans ce fichier par défaut par le code XML suivant. Ce code XML remplace le nom de la liste à **employés** et ajoute des informations pour un employé qui a nommé Jim Hance.  
  
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
  
16. Enregistrez et fermez le *Elements.xml* fichier.  
  
17. Ouvrez le menu contextuel pour le projet DéfinitionListeEmployés, puis choisissez **Open** ou **propriétés**.  
  
     Le Concepteur de propriétés s’ouvre.  
  
18. Sur le **SharePoint** onglet, désactivez le **retrait automatique après le débogage** case à cocher, puis enregistrez les propriétés.  
  
#### <a name="to-deploy-the-list-definition-and-list-instance"></a>Pour déployer la définition de liste et l’instance de liste  
  
1.  Dans **l’Explorateur de solutions**, choisissez le **DéfinitionListeEmployés** nœud du projet.  
  
2.  Dans le **propriétés** fenêtre, assurez-vous que le **Configuration de déploiement Active** propriété est définie sur **par défaut**.  
  
3.  Choisissez le **F5** clé ou, dans la barre de menus, choisissez **déboguer** > **démarrer le débogage**.  
  
4.  Vérifiez que le projet correctement généré, que le navigateur web ouvre le site SharePoint, qui le **répertorie** élément dans la barre de lancement rapide inclut la nouvelle **employés** liste et que le  **Employés** liste comprend l’entrée de Jim Hance.  
  
5.  Fermez le navigateur web.  
  
#### <a name="to-modify-the-list-definition-and-list-instance-and-redeploy-them"></a>Pour modifier la définition de liste et l’instance de liste et de les redéployer  
  
1.  Dans le projet DéfinitionListeEmployés, ouvrez le *Elements.xml* fichier qui est un enfant de la **employé liste Instance** élément de projet.  
  
2.  Supprimer le `Data` élément et ses enfants à supprimer de l’entrée de Jim Hance dans la liste.  
  
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
  
3.  Enregistrez et fermez le *Elements.xml* fichier.  
  
4.  Ouvrez le menu contextuel pour le **liste d’employés** l’élément de projet, puis choisissez **Open** ou **propriétés**.  
  
5.  Dans le Concepteur de la liste, choisissez le **vues** onglet.  
  
6.  Dans le **colonnes sélectionnées** , choisissez **des pièces jointes**, puis choisissez le < clé pour déplacer cette colonne pour la **colonnes disponibles** liste.  
  
7.  Répétez l’étape précédente pour déplacer le **téléphone professionnel** colonne à partir de la **colonnes sélectionnées** list à le **colonnes disponibles** liste.  
  
     Cette action supprime ces champs à partir de la vue par défaut de la **employés** liste sur le site SharePoint.  
  
8.  Démarrer le débogage en choisissant le **F5** clé ou, dans la barre de menus, choisissez **déboguer** > **démarrer le débogage**.  
  
9. Vérifiez que le **les conflits de déploiement** boîte de dialogue s’affiche.  
  
     Cette boîte de dialogue s’affiche lorsque Visual Studio essaie de déployer une solution (l’instance de liste) sur un site SharePoint auquel cette solution a déjà été déployée. Cette boîte de dialogue ne s’affiche lorsque vous exécutez l’étape de déploiement de mise à niveau plus loin dans cette procédure pas à pas.  
  
10. Dans le **les conflits de déploiement** boîte de dialogue, sélectionnez le **résoudre automatiquement** case d’option.  
  
     Visual Studio supprime l’instance de liste sur le site SharePoint, déploie l’élément de liste dans le projet, puis ouvre le site SharePoint.  
  
11. Dans le **répertorie** section de la barre de lancement rapide, choisissez le **employés** liste et vérifiez les détails suivants :  
  
    -   Le **des pièces jointes** et **téléphone personnel** colonnes n’apparaissent pas dans cette vue de la liste.  
  
    -   La liste est vide. Lorsque vous avez utilisé le **par défaut** configuration de déploiement pour redéployer la solution, le **employés** liste a été remplacée par la nouvelle liste vide dans votre projet.  
  
## <a name="test-the-deployment-step"></a>L’étape de déploiement de test
 Vous êtes maintenant prêt à tester l’étape de déploiement de mise à niveau. Tout d’abord, ajoutez un élément à l’instance de liste dans SharePoint. Puis modifiez la définition de liste et l’instance de liste, les mettre à niveau sur le site SharePoint et vérifiez que l’étape de déploiement de mise à niveau ne remplace pas le nouvel élément.  
  
#### <a name="to-manually-add-an-item-to-the-list"></a>Pour ajouter manuellement un élément à la liste  
  
1.  Dans le ruban sur le site SharePoint, sous la **outils de liste** , choisir le **éléments** onglet.  
  
2.  Dans le **New** de groupe, choisissez **un nouvel élément**.  
  
     Comme alternative, vous pouvez choisir le **ajouter un nouvel élément** lien dans la liste d’éléments.  
  
3.  Dans le **employés - nouvel élément** fenêtre, dans le **titre** , entrez **responsable des installations**.  
  
4.  Dans le **prénom** , entrez **Andy**.  
  
5.  Dans le **entreprise** , tapez **Contoso**.  
  
6.  Choisissez le **enregistrer** bouton, vérifiez que le nouvel élément apparaît dans la liste, puis fermez le navigateur web.  
  
     Plus loin dans cette procédure pas à pas, vous utiliserez cet élément pour vérifier que l’étape de déploiement de mise à niveau ne remplace le contenu de cette liste.  
  
#### <a name="to-test-the-upgrade-deployment-step"></a>Pour tester l’étape de déploiement de mise à niveau  
  
1. Dans l’instance expérimentale de Visual Studio, dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **DéfinitionListeEmployés** nœud de projet, puis choisissez **propriétés**.  
  
    Le Concepteur/éditeur de propriétés s’ouvre.  
  
2. Sur le **SharePoint** onglet, définissez la **Configuration de déploiement Active** propriété **mise à niveau**.  
  
    Cette configuration de déploiement personnalisé inclut la nouvelle étape de déploiement de mise à niveau.  
  
3. Ouvrez le menu contextuel pour le **liste d’employés** l’élément de projet, puis choisissez **propriétés** ou **Open**.  
  
    Le Concepteur/éditeur de propriétés s’ouvre.  
  
4. Sur le **vues** onglet, choisissez le **messagerie** colonne, puis choisissez le **<** clé pour déplacer cette colonne à partir de la **decolonnessélectionnées**list à le **colonnes disponibles** liste.  
  
    Cette action supprime ces champs à partir de la vue par défaut de la **employés** liste sur le site SharePoint.  
  
5. Démarrer le débogage en choisissant le **F5** clé ou, dans la barre de menus, choisissez **déboguer** > **démarrer le débogage**.  
  
6. Vérifiez que le code dans l’autre instance de Visual Studio s’arrête au point d’arrêt que vous avez défini précédemment dans le `CanExecute` (méthode).  
  
7. Choisissez le **F5** à nouveau la clé ou, dans la barre de menus, choisissez **déboguer** > **continuer**.  
  
8. Vérifiez que le code s’arrête au point d’arrêt que vous avez défini précédemment dans le `Execute` (méthode).  
  
9. Choisissez le **F5** clé ou, dans la barre de menus, choisissez **déboguer** > **continuer** une dernière fois.  
  
     Le navigateur web ouvre le site SharePoint.  
  
10. Dans le **répertorie** section de la zone de lancement rapide, choisissez le **employés** liste et vérifiez les détails suivants :  
  
    - L’élément que vous avez ajouté manuellement précédemment (par Andy, le responsable des installations) est toujours dans la liste.  
  
    - Le **téléphone professionnel** et **adresse de messagerie** colonnes n’apparaissent pas dans cette vue de la liste.  
  
      Le **mise à niveau** modifie de configuration de déploiement existant **employés** instance de liste sur le site SharePoint. Si vous avez utilisé le **par défaut** configuration de déploiement au lieu du **mise à niveau** configuration, vous seriez confronté à un conflit de déploiement. Visual Studio résoudrait le conflit en remplaçant le **employés** liste et l’élément pour Andy, le responsable des installations, seraient supprimés.  
  
## <a name="clean-up-the-development-computer"></a>Nettoyer l’ordinateur de développement
 Une fois que vous avez terminé le test de l’étape de déploiement de mise à niveau, supprimer l’instance de liste et de la définition de liste à partir du site SharePoint et supprimer l’extension d’étape de déploiement de Visual Studio.  
  
#### <a name="to-remove-the-list-instance-from-the-sharepoint-site"></a>Pour supprimer l’instance de liste à partir du site SharePoint  
  
1.  Ouvrez le **employés** liste sur le site SharePoint, si la liste n’est pas déjà ouverte.  
  
2.  Dans le ruban sur le site SharePoint, choisissez le **outils de liste** onglet, puis choisissez le **liste** onglet.  
  
3.  Dans le **paramètres** de groupe, choisissez le **liste paramètres** élément.  
  
4.  Sous **autorisations et gestion**, choisissez le **supprimer cette liste** commande, choisissez **OK** pour confirmer que vous souhaitez envoyer la liste à la Corbeille, puis fermez le web Navigateur.  
  
#### <a name="to-remove-the-list-definition-from-the-sharepoint-site"></a>Pour supprimer la définition de liste à partir du site SharePoint  
  
1.  Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **Build** > **Retract**.  
  
     Visual Studio permet de retirer la définition de liste à partir du site SharePoint.  
  
#### <a name="to-uninstall-the-extension"></a>Pour désinstaller l'extension  
  
1.  Dans l’instance expérimentale de Visual Studio, dans la barre de menus, choisissez **outils** > **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s’ouvre.  
  
2.  Dans la liste des extensions, choisissez **étape de déploiement de mise à niveau pour les projets SharePoint**, puis choisissez le **désinstallation** commande.  
  
3.  Dans la boîte de dialogue qui s’affiche, choisissez **Oui** pour confirmer que vous souhaitez désinstaller l’extension, puis choisissez **redémarrer maintenant** pour terminer la désinstallation.  
  
4.  Fermez les deux instances de Visual Studio (l’instance expérimentale et l’instance de Visual Studio dans laquelle la solution UpgradeDeploymentStep est ouverte).  
  
## <a name="see-also"></a>Voir aussi
 [Étendre le déploiement et empaquetage de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
