---
title: "Walkthrough: Creating a Custom Deployment Step for SharePoint Projects"
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
  - "SharePoint commands"
  - "SharePoint development in Visual Studio, extending deployment"
ms.assetid: 4ba2d120-06b8-4ef3-84eb-c6c50ced9d82
caps.latest.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 62
---
# Walkthrough: Creating a Custom Deployment Step for SharePoint Projects
  Lorsque vous déployez un projet SharePoint, Visual Studio exécute une série d'étapes de déploiement dans un ordre spécifique.  Visual Studio inclut de nombreuses étapes de déploiement intégrées, mais rien ne vous empêche de créer vos propres étapes de déploiement.  
  
 Dans cette procédure pas \- à \- pas, vous créerez une étape de déploiement personnalisée pour mettre à niveau des solutions sur un serveur SharePoint qui est en cours de exécution.  Visual Studio inclut des étapes de déploiement intégrées pour de nombreuses tâches, ces solutions retrait de ou ajoutantes, mais il n'inclut pas une étape de déploiement de mise à jour de solutions.  Par défaut, lorsque vous déployez une solution SharePoint, Visual Studio retire d'abord la solution \(si elle est déjà déployé\) et redéploie ensuite la solution.  Pour plus d'informations sur les étapes de déploiement intégrées, consultez [Déploiement, publication et mise à niveau de packages de solutions SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
 Cette procédure pas à pas présente les tâches suivantes :  
  
-   Création d'une extension Visual Studio qui exécute deux tâches principales :  
  
    -   L'extension définit une étape de déploiement personnalisée pour mettre à niveau des solutions SharePoint.  
  
    -   L'extension crée une extension de projet qui définit une nouvelle configuration de déploiement, qui est un ensemble d'étapes de déploiement exécutées pour un projet donné.  La nouvelle configuration de déploiement inclut l'étape de déploiement personnalisée et plusieurs étapes de déploiement intégrées.  
  
-   Création de deux commandes SharePoint personnalisées que l'assembly d'extension appelle.  Les commandes SharePoint sont des méthodes susceptibles d'être appelées par des assemblys d'extension pour utiliser des API dans le modèle d'objet serveur pour SharePoint.  Pour plus d’informations, consultez [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
-   Génération d'un package Visual Studio Extension \(VSIX\) pour déployer les deux assemblys.  
  
-   Test de la nouvelle étape de déploiement.  
  
## Composants requis  
 Vous avez besoin des composants suivants sur l'ordinateur de développement pour terminer cette procédure pas à pas :  
  
-   Éditions prises windows, de SharePoint, et Visual Studio.  Pour plus d’informations, consultez [Configuration requise pour développer des solutions SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Le kit de développement Visual Studio.  Cette procédure pas à pas se base sur le modèle **Projet VSIX** dans le Kit de développement logiciel pour créer un package VSIX nécessaire au déploiement de l'extension.  Pour plus d’informations, consultez [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
 Une connaissance des concepts suivants est utile, mais pas obligatoire, pour effectuer cette procédure pas à pas :  
  
-   Utilisation du modèle d'objet serveur pour SharePoint.  Pour plus d'informations, consultez [Utilisation du modèle d'objet serveur SharePoint Foundation \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=177796).  
  
-   Solutions SharePoint.  Pour plus d'informations, consultez [Vue d'ensemble des solutions](http://go.microsoft.com/fwlink/?LinkId=169422).  
  
-   Mise à niveau de solutions SharePoint.  Pour plus d'informations, consultez .  
  
## Création du projet  
 Pour exécuter cette procédure, vous devez créer trois projets :  
  
-   Un projet VSIX pour créer le package VSIX afin de déployer l'extension.  
  
-   Un projet de bibliothèque de classes qui implémente l'extension.  Ce projet doit cibler .NET Framework 4,5.  
  
-   Un projet de bibliothèque de classes qui définit les commandes SharePoint personnalisées.  Ce projet doit cibler le .NET Framework 3.5.  
  
 Démarrez la procédure pas à pas en créant les projets.  
  
#### Pour créer le projet VSIX  
  
1.  Démarrez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
3.  Dans la boîte de dialogue **Nouveau projet** , développez les nœuds **Visual C\#** ou **Visual Basic** , puis sélectionnez le nœud **Extensibilité** .  
  
    > [!NOTE]  
    >  Le nœud **Extensibilité** est disponible uniquement si vous installez le kit de développement Visual Studio.  Pour plus d'informations, consultez la section des composants requis plus haut dans cette rubrique.  
  
4.  En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework.  
  
5.  Sélectionnez le modèle **projet VSIX** , nommez le projet **UpgradeDeploymentStep**, puis choisissez le bouton **OK** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **UpgradeDeploymentStep** à l'**Explorateur de solutions**.  
  
#### Pour créer le projet d'extension  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution UpgradeDeploymentStep, choisissez **Ajouter**, puis choisissez **Nouveau projet**.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, le nœud de la solution s'affiche dans l'**Explorateur de solutions** à condition d'avoir activé la case à cocher **Toujours afficher la solution** dans la [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Dans la boîte de dialogue **Nouveau projet** , développez les nœuds **Visual C\#** ou **Visual Basic** , puis sélectionnez le nœud **Fenêtres** .  
  
3.  En haut de la boîte de dialogue, choisissez **.NET Framework 4,5** dans la liste des versions du .NET Framework.  
  
4.  Choisissez le modèle de projet **Bibliothèque de classes** , nommez le projet **DeploymentStepExtension**, puis choisissez le bouton **OK** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ajoute le projet **DeploymentStepExtension** à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprimez le fichier de code Class1 du projet.  
  
#### Pour créer le projet SharePointCommands  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de solution UpgradeDeploymentStep, choisissez **Ajouter**, puis choisissez **Nouveau projet**.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, le nœud de solution s'affiche seulement dans l'**Explorateur de solutions** si la case à cocher **Toujours afficher la solution** est activée dans la [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
2.  Dans la boîte de dialogue **Nouveau projet** , développez **Visual C\#** ou **Visual Basic**, puis sélectionnez le nœud **Fenêtres** .  
  
3.  En haut de la boîte de dialogue, choisissez **.NET Framework 3.5** dans la liste des versions du .NET Framework.  
  
4.  Choisissez le modèle de projet **Bibliothèque de classes** , nommez le projet **SharePointCommands**, puis choisissez le bouton **OK** .  
  
     Visual Studio ajoute le projet **SharePointCommands** à la solution et ouvre le fichier de code Class1 par défaut.  
  
5.  Supprimez le fichier de code Class1 du projet.  
  
## Configuration des projets  
 Avant d'écrire le code pour créer l'étape de déploiement personnalisée, vous devez ajouter des fichiers de code et des références d'assembly, et vous devez configurer les projets.  
  
#### Pour configurer le projet DeploymentStepExtension  
  
1.  Dans le projet **DeploymentStepExtension** , ajoutez deux fichiers de code portant les noms suivants :  
  
    -   UpgradeStep  
  
    -   DeploymentConfigurationExtension  
  
2.  Ouvrez le menu contextuel du projet DeploymentStepExtension, puis choisissez **Ajouter une référence**.  
  
3.  Sous l'onglet **framework** , activez la case à cocher pour l'assembly System.ComponentModel.Composition.  
  
4.  Sous l'onglet **Extensions** , activez la case à cocher pour l'assembly Microsoft.VisualStudio.SharePoint, puis choisissez le bouton **OK** .  
  
#### Pour configurer le projet SharePointCommands  
  
1.  Dans le projet **SharePointCommands** , ajoutez un fichier de code appelé Commands.  
  
2.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **SharePointCommands** , puis choisissez **Ajouter une référence**.  
  
3.  Sous l'onglet **Extensions** , activez les cases à cocher pour les assemblys suivants, puis cliquez sur le bouton **OK**  
  
    -   Microsoft.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
## Définition de l'étape de déploiement personnalisée  
 Créez une classe qui définit l'étape de déploiement de mise à niveau.  Pour définir l'étape de déploiement, la classe implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>.  Implémentez cette interface chaque fois que vous souhaitez définir une étape de déploiement personnalisée.  
  
#### Pour définir l'étape de déploiement personnalisée  
  
1.  Dans le projet **DeploymentStepExtension** , ouvrez le fichier de code UpgradeStep, puis collez le code suivant dans ce fichier.  
  
    > [!NOTE]  
    >  Après avoir ajouté ce code, le projet comportera des erreurs de compilation, mais ils partiront lorsque vous ajoutez le code dans les étapes ultérieures.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#1)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#1)]  
  
## Création d'une configuration de déploiement qui inclut l'étape de déploiement personnalisée  
 Créez une extension de projet pour la nouvelle configuration de déploiement, qui inclut plusieurs étapes de déploiement intégrées et la nouvelle étape de déploiement de mise à jour.  En créant cette extension, vous aidez les développeurs SharePoint à utiliser l'étape de déploiement de mise à niveau dans les projets sharepoint.  
  
 Pour créer la configuration de déploiement, la classe implémente l'interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Implémentez cette interface chaque fois que vous souhaitez créer une extension de projet SharePoint.  
  
#### Pour créer la configuration de déploiement  
  
1.  Dans le projet **DeploymentStepExtension** , ouvrez le fichier de code DeploymentConfigurationExtension, puis collez le code suivant dans ce fichier.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/deploymentconfigurationextension.cs#2)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/deploymentconfigurationextension.vb#2)]  
  
## Création de commandes SharePoint personnalisées  
 Créez deux commandes personnalisées faisant appel au modèle d'objet serveur pour SharePoint.  L'une des deux commandes a pour objet de déterminer si une solution est déjà déployée et l'autre de mettre à niveau une solution.  
  
#### Pour définir les commandes SharePoint  
  
1.  Dans le projet **SharePointCommands** , ouvrez le fichier de code commands, puis collez le code suivant dans ce fichier.  
  
     [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#4)]
     [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#4)]  
  
## Point de contrôle  
 À ce stade de la procédure pas à pas, les projets comportent le code complet de l'étape de déploiement personnalisée ainsi que les commandes SharePoint.  Générez\- les vous assurer qu'ils compiler sans erreur.  
  
#### Pour générer des projets  
  
1.  Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **DeploymentStepExtension** , puis choisissez **Générer**.  
  
2.  Ouvrez le menu contextuel du projet **SharePointCommands** , puis choisissez **Générer**.  
  
## Création d'un package VSIX pour déployer l'extension  
 Pour déployer l'extension, utilisez le projet VSIX inclus dans votre solution pour créer un package VSIX.  D'abord, configurez le package VSIX en modifiant le fichier source.extension.vsixmanifest du projet VSIX.  Créez le package VSIX lors de la génération de la solution.  
  
#### Pour configurer et créer le package VSIX  
  
1.  Dans **Explorateur de solutions**, sous le projet **UpgradeDeploymentStep** , ouvrez le menu contextuel du fichier **source.extension.vsixmanifest** , puis choisissez **Ouvrir**.  
  
     Visual Studio ouvre le fichier dans l'éditeur de manifeste.  Le fichier source.extension.vsixmanifest est la base du fichier extension.vsixmanifest que tous les packages VSIX ont besoin.  Pour plus d'informations sur ce fichier, consultez [Référence de schéma d'extensions VSIX](http://msdn.microsoft.com/fr-fr/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  Dans la zone **nom de produit** , entrez **Étape de déploiement de mise à niveau des projets sharepoint**.  
  
3.  Dans la zone **Author** , entrez **Contoso**.  
  
4.  Dans la zone **Description** , entrez **Fournit une étape de déploiement de mise à niveau personnalisée qui peut être utilisée dans les projets sharepoint**.  
  
5.  Dans l'onglet **Composants** de l'éditeur, choisissez le bouton **Nouveau** .  
  
     La boîte de dialogue **ajoutez le nouveau ressource** s'affiche.  
  
6.  Dans la liste **Type** , choisissez **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Cette valeur correspond à l'élément `MefComponent` dans le fichier extension.vsixmanifest.  Cet élément spécifie le nom d'un assembly d'extension dans le package VSIX.  Pour plus d’informations, consultez [NIB: MEFComponent Element \(VSX Schema\)](http://msdn.microsoft.com/fr-fr/8a813141-8b73-44c9-b80b-ca85bbac9551).  
  
7.  Dans la liste **Source** , choisissez **un projet dans la solution actuelle**.  
  
8.  Dans la liste **Projet** , choisissez **DeploymentStepExtension**, puis choisissez le bouton **OK** .  
  
9. Dans l'éditeur de manifeste, choisissez le bouton **Nouveau** de nouveau.  
  
     La boîte de dialogue **ajoutez le nouveau ressource** s'affiche.  
  
10. Dans la liste **Type** , entrez **SharePoint.Commands.v4**.  
  
    > [!NOTE]  
    >  Cet élément désigne l'extension personnalisée à inclure à l'extension Visual Studio.  Pour plus d’informations, consultez [Élément de ressource \(schéma VSX\)](http://msdn.microsoft.com/fr-fr/9fcfc098-edc7-484b-9d4c-acd17829d737).  
  
11. Dans la liste **Source** , choisissez **un projet dans la solution actuelle**.  
  
12. Dans la liste **Projet** , choisissez **SharePointCommands**, puis choisissez le bouton **OK** .  
  
13. Dans la barre de menus, sélectionnez **Générer**, **Générer la solution**, puis vérifiez que les compilations de solution sans erreur.  
  
14. Assurez \-vous que le dossier de sortie de la génération pour le projet UpgradeDeploymentStep contient maintenant le fichier d'UpgradeDeploymentStep.vsix.  
  
     Par défaut, le dossier de sortie de la génération est le dossier ..  \\bin\\Debug sous le dossier qui contient votre fichier projet.  
  
## Préparation en vue de tester l'étape de déploiement de mise à niveau  
 Pour tester l'étape de déploiement de mise à niveau, vous devez commencer par déployer un exemple de solution au niveau du site SharePoint.  Commencez par déboguer le projet d'extension dans l'instance expérimentale de Visual Studio.  Créez ensuite une définition de liste et une instance de liste à utiliser pour tester l'étape de déploiement, et déployez ensuite les au site SharePoint.  Ensuite, modifiez la définition de liste et l'instance de liste et redéployez\- les pour montrer comment le processus de déploiement par défaut remplace les solutions sur le site SharePoint.  
  
 À une étape ultérieure de cette procédure, vous modifierez la définition de liste et l'instance de liste, puis vous les améliorerez sur le site SharePoint.  
  
#### Pour démarrer le débogage de l'extension  
  
1.  Redémarrez Visual Studio avec les informations d'identification d'administration, puis ouvrez la solution UpgradeDeploymentStep.  
  
2.  Dans le projet DeploymentStepExtension, ouvrez le fichier de code UpgradeStep, puis ajoutez un point d'arrêt sur la première ligne de code dans les méthodes d' `CanExecute` et d' `Execute` .  
  
3.  Commencez à déboguer en choisissant la touche F5 ou, dans la barre de menus, choisissant **Déboguer**, **Démarrer le débogage**.  
  
4.  Visual Studio installe l'extension sous %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0Exp\\Extensions\\Contoso\\Upgrade Deployment Step for SharePoint Projects\\1.0 and starts an experimental instance of Visual Studio.  Vous allez tester l'étape de déploiement de mise à niveau dans cette instance de Visual Studio.  
  
#### Pour créer un projet SharePoint à une définition de liste et une instance de liste  
  
1.  Dans l'instance expérimentale de Visual Studio, dans le menu, choisissez **Fichier**, **Nouveau**, **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet** , développez le nœud **Visual C\#** ou le nœud **Visual Basic** , développez le nœud **SharePoint** , puis sélectionnez le nœud **2010** .  
  
3.  En haut de la boîte de dialogue, vérifiez que **.NET Framework 3.5** apparaît dans la liste des versions du .NET Framework.  
  
     Les projets pour [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] et [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] requièrent cette version du .NET Framework.  
  
4.  Dans la liste des modèles de projet, choisissez **Projet SharePoint 2010**, nommez le projet **EmployeesListDefinition**, puis choisissez le bouton **OK** .  
  
5.  Dans **Assistant personnalisation de SharePoint**, entrez l'URL du site que vous souhaitez utiliser pour le débogage.  
  
6.  Sous **Ce qui est le niveau de confiance de la solution SharePoint**, sélectionnez la case d'option **Déployer une solution de batterie** .  
  
    > [!NOTE]  
    >  L'étape de déploiement de mise à niveau ne prend pas en charge les solutions bac à sable \(sandbox\).  
  
7.  Choisissez le bouton **Terminer** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée le projet d'EmployeesListDefinition.  
  
8.  Ouvrez le menu contextuel du projet d'EmployeesListDefinition, choisissez **Ajouter**, puis choisissez **Nouvel élément**.  
  
9. Dans la boîte de dialogue **ajoutez le nouvel élément – EmployeesListDefinition** , développez le nœud **SharePoint** , puis sélectionnez le nœud **2010** .  
  
10. Choisissez le modèle d'élément **liste** , nommez l'élément **liste des employés**, puis choisissez le bouton **Ajouter** .  
  
     L'assistant personnalisation de SharePoint s'affiche  
  
11. Dans la page **Choisissez des paramètres de liste** , vérifiez les paramètres suivants, puis choisissez le bouton **Terminer** :  
  
    1.  **liste des employés** apparaît dans la zone **Le nom voulez \-vous afficher pour votre liste ?** .  
  
    2.  La case d'option **Créez une liste personnalisable basée sur :** est sélectionné.  
  
    3.  **Valeur par défaut \(vide\)** est sélectionnez dans la liste **Créez une liste personnalisable basée sur :** .  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] crée l'élément de liste d'employés avec une colonne de titre et un seul l'instance vide et ouvrez le concepteur de liste.  
  
12. Dans le concepteur de liste, sous l'onglet **colonnes** , sélectionnez la ligne **Tapez un nouveau ou existant nom de colonne** , puis ajoutez les colonnes suivantes dans la liste **nom complet de colonne** :  
  
    1.  Prénom  
  
    2.  Société  
  
    3.  Téléphone d'entreprise  
  
    4.  Courrier électronique  
  
13. Enregistrez tous les fichiers, puis fermez le concepteur de liste.  
  
14. Dans **Explorateur de solutions**, développez le nœud **liste des employés** , puis développez le nœud enfant **Instance de liste d'employés** .  
  
15. Dans le fichier Elements.xml, remplacez la valeur par défaut XML dans ce fichier par le code XML suivant.  Ce code XML change le nom de la liste par **Employé** et ajoute des informations pour un employé qui a nommé Julien Hallert.  
  
    ```  
  
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
  
16. Enregistrez et fermez le fichier Elements.xml.  
  
17. Ouvrez le menu contextuel du projet d'EmployeesListDefinition, puis choisissez **Ouvrir** ou **Propriétés**.  
  
     Le concepteur de propriétés s'ouvre.  
  
18. Sous l'onglet **SharePoint** , désactivez la case à cocher **retrait automatique après le débogage** , et enregistrent les propriétés.  
  
#### Pour déployer la définition de liste et l'instance de liste  
  
1.  Dans **Explorateur de solutions**, sélectionnez le nœud de projet **EmployeesListDefinition** .  
  
2.  Dans la fenêtre **Propriétés**, assurez\-vous que la propriété **Configuration de déploiement active** a la valeur **Par défaut**.  
  
3.  Choisissez la touche F5 ou, dans la barre de menus, sélectionnez **Déboguer**, **Démarrer le débogage**.  
  
4.  Vérifiez que le projet est correctement généré, que le navigateur web s'ouvre au site SharePoint, que l'élément **listes** dans la barre de lancement rapide inclut la nouvelle liste **Employé** , et que la liste **Employé** inclut l'entrée à Julien Hallert.  
  
5.  Fermez le navigateur web.  
  
#### Pour modifier la définition de liste et l'instance de liste et les redéployer  
  
1.  Dans le projet d'EmployeesListDefinition, ouvrez le fichier Elements.xml qui est un enfant de l'élément de projet **Instance de liste d'employés** .  
  
2.  Supprimez l'élément `Data` et ses enfants pour supprimer de la liste l'entrée correspondant à Julien Hallert.  
  
     Lorsque vous avez terminé, le fichier doit contenir le code XML suivant.  
  
    ```  
  
    <Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
      <ListInstance Title="Employees"  
                    OnQuickLaunch="TRUE"  
                    TemplateType="10000"  
                    Url="Lists/Employees"  
                    Description="Simple list to test upgrade deployment step">  
      </ListInstance>  
    </Elements>  
    ```  
  
3.  Enregistrez et fermez le fichier Elements.xml.  
  
4.  Ouvrez le menu contextuel pour l'élément de projet **liste des employés** , puis choisissez **Ouvrir** ou **Propriétés**.  
  
5.  Dans le concepteur de liste, choisissez **Affichages** tableau.  
  
6.  Dans la liste **Colonnes sélectionnées** , choisissez **Pièces jointes**, puis choisissez \< clé à déplacer que colonne dans la liste **Colonnes disponibles** .  
  
7.  Répétez l'étape précédente pour déplacer la colonne **Téléphone d'entreprise** de la liste **Colonnes sélectionnées** à la liste **Colonnes disponibles** .  
  
     Cela permet d'éliminer ces champs de la vue par défaut de la liste **Employees** sur le site SharePoint.  
  
8.  Commencez à déboguer en choisissant la touche F5 ou, dans la barre de menus, choisissant **Déboguer**, **Démarrer le débogage**.  
  
9. Assurez\-vous que la boîte de dialogue **Conflits de déploiement** s'ouvre.  
  
     Cette boîte de dialogue apparaît lorsque les tests de Visual Studio déployer une solution \(instance de liste\) à un site SharePoint auquel cette solution a déjà été déployée.  Cette boîte de dialogue ne s'affiche pas lorsque vous exécutez l'étape de déploiement de mise à niveau à une étape ultérieure de cette procédure.  
  
10. Dans la boîte de dialogue **conflits de déploiement** , sélectionnez la case d'option **Résolution automatique** .  
  
     Visual Studio supprime l'instance de liste du site SharePoint, déploie l'élément de liste dans le projet, puis ouvre le site SharePoint.  
  
11. Dans la section **listes** de la barre de lancement rapide, cliquez sur la liste **Employé** , puis vérifiez les informations suivants :  
  
    -   Les colonnes **Pièces jointes** et **téléphone domicile** ne s'affichent pas dans cette vue de la liste.  
  
    -   La liste est vide.  En effet, lorsque vous avez utilisé la configuration de déploiement **Par défaut** pour redéployer la solution, la liste **Employees** a été remplacée par la nouvelle liste vide dans votre projet.  
  
## Test de l'étape de déploiement  
 Vous êtes maintenant prêt à tester l'étape de déploiement de mise à niveau.  Tout d'abord, ajoutez un élément à l'instance de liste dans SharePoint.  Puis remplacez la définition de liste et l'instance de liste, améliorez\- les sur le site SharePoint, et les vérifiez que l'étape de déploiement de mise à niveau ne remplace pas le nouvel élément.  
  
#### Pour ajouter manuellement un élément à la liste  
  
1.  Dans le ruban du site SharePoint, sous l'onglet **répertoriez les outils** , choisissez **éléments** tableau.  
  
2.  Dans le groupe **Nouveau** , choisissez **Nouvel élément**.  
  
     Sinon, vous pouvez choisir le lien **Ajouter un nouvel élément** dans la liste d'éléments lui\-même.  
  
3.  Dans la fenêtre **employés – nouvel élément** , dans la zone **Titre** , entrez **Gestionnaire de fonctionnalités**.  
  
4.  Dans la zone **prénom** , entrez **Andy**.  
  
5.  Dans la zone **société** , tapez **Contoso**.  
  
6.  Choisissez le bouton **Enregistrer** , vérifiez que le nouvel élément s'affiche dans la liste, puis fermez le navigateur web.  
  
     À une étape ultérieure de cette procédure, vous utiliserez cet élément pour vérifier que l'étape de déploiement de mise à niveau ne remplace pas le contenu de cette liste.  
  
#### Pour tester l'étape de déploiement de mise à niveau  
  
1.  Dans l'instance expérimentale de Visual Studio, dans **Explorateur de solutions**, ouvrez le menu contextuel du nœud de projet **EmployeesListDefinition** , puis choisissez **Propriétés**.  
  
     L'éditeur\/concepteur de propriétés s'ouvre.  
  
2.  Sous l'onglet **SharePoint** , affectez à la propriété **configuration de déploiement active** à **mise à jour**.  
  
     Cette configuration de déploiement personnalisée inclut la nouvelle étape de déploiement de mise à jour.  
  
3.  Ouvrez le menu contextuel pour l'élément de projet **liste des employés** , puis choisissez **Propriétés** ou **Ouvrir**.  
  
     L'éditeur\/concepteur de propriétés s'ouvre.  
  
4.  Sous l'onglet **Affichages** , choisissez la colonne **courrier électronique** , puis choisissez la clé **\<** pour déplacer que colonne de la liste **Colonnes sélectionnées** à la liste **Colonnes disponibles** .  
  
     Cela permet d'éliminer ces champs de la vue par défaut de la liste **Employees** sur le site SharePoint.  
  
5.  Commencez à déboguer en choisissant la touche F5 ou, dans la barre de menus, choisissant **Déboguer**, **Démarrer le débogage**.  
  
6.  Assurez\-vous que le code dans l'autre instance de Visual Studio s'immobilise sur le point d'arrêt que vous avez défini précédemment dans la méthode `CanExecute`.  
  
7.  Choisissez la touche F5 à nouveau ou, dans la barre de menus, sélectionnez **Déboguer**, **Continuer**.  
  
8.  Assurez\-vous que le code s'immobilise sur le point d'arrêt défini précédemment dans la méthode `Execute`.  
  
9. Choisissez la touche F5 ou, dans la barre de menus, sélectionnez **Déboguer**, **Continuer** un temps final.  
  
     Le navigateur web s'ouvre le site SharePoint.  
  
10. Dans la section **listes** de la zone de lancement rapide, cliquez sur la liste **Employé** , puis vérifiez les informations suivants :  
  
    -   L'élément que vous manuellement avez ajouté précédemment \(pour Andy, le gestionnaire de fonctions\) est toujours dans la liste.  
  
    -   Les colonnes **Téléphone d'entreprise** et **adresse de messagerie** ne s'affichent pas dans cette vue de la liste.  
  
     La configuration du déploiement **Mettre à niveau** modifie l'instance de liste **Employees** existante sur le site SharePoint.  Si vous aviez utilisé la configuration de déploiement **Par défaut** au lieu de la configuration **Mettre à niveau**, un conflit de déploiement se produirait.  Visual Studio résoudrait le conflit en substituant la liste **Employé** , et l'élément pour Andy, le gestionnaire de fonctionnalités, est supprimé.  
  
## Nettoyage de l'ordinateur de développement  
 Une fois le test de l'étape de déploiement de mise à niveau terminée, supprimez l'instance de liste et la définition de liste du site SharePoint et éliminez l'extension de l'étape de déploiement dans Visual Studio.  
  
#### Pour supprimer l'instance de liste du site SharePoint  
  
1.  Ouvrez la liste **Employé** sur le site SharePoint, si la liste n'est pas déjà ouvert.  
  
2.  Dans le ruban du site SharePoint, sélectionnez l'onglet **répertoriez les outils** , puis choisissez **liste** tableau.  
  
3.  Dans le groupe **Paramètres** , sélectionnez l'élément **Paramètres de liste** .  
  
4.  Sous **autorisations et gestion**, choisissez la commande **supprimez cette liste** , choisissez **OK** pour confirmer que vous souhaitez envoyer à la Corbeille la liste, puis fermez le navigateur web.  
  
#### Pour supprimer le définition de liste du site SharePoint  
  
1.  Dans l'instance expérimentale de Visual Studio, dans le menu, choisissez **Générer**, **Retrait**.  
  
     Visual Studio retire la définition de liste du site SharePoint.  
  
#### Pour désinstaller l'extension  
  
1.  Dans l'instance expérimentale de Visual Studio, dans le menu, choisissez **Outils**, **Extensions et mises à jour**.  
  
     La boîte de dialogue **Extensions et mises à jour** s'ouvre.  
  
2.  Dans la liste d'extensions, choisissez **Étape de déploiement de mise à niveau des projets sharepoint**, puis sélectionnez la commande **Désinstaller** .  
  
3.  Dans la boîte de dialogue qui apparaît, sélectionnez **oui** pour confirmer que vous voulez désinstaller l'extension, puis choisissez **Redémarrez maintenant** pour terminer la désinstallation.  
  
4.  Fermez les deux instances de Visual Studio \(l'instance expérimentale et l'instance de Visual Studio dans laquelle la solution UpgradeDeploymentStep est ouverte\).  
  
## Voir aussi  
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  