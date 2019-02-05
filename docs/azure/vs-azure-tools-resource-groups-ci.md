---
title: Intégration continue dans Azure DevOps Services à l’aide de projets Groupe de ressources Azure | Microsoft Docs
description: Décrit la configuration de l’intégration continue dans Azure DevOps Services en utilisant des projets de déploiement Groupe de ressources Azure dans Visual Studio.
author: mlearned
manager: jillfra
ms.assetid: b81c172a-be87-4adc-861e-d20b94be9e38
ms.service: azure-resource-manager
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 08/01/2016
ms.author: mlearned
ms.openlocfilehash: bbe4fc4f59527b73b46d95f70541202f87ffab4e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55139740"
---
# <a name="continuous-integration-in-azure-devops-services-using-azure-resource-group-deployment-projects"></a>Intégration continue dans Azure DevOps Services à l’aide de projets de déploiement Groupe de ressources Azure
Pour déployer un modèle Azure, vous devez effectuer les tâches selon différentes phases : Générer, Tester, Copier sur Azure (également appelée « préproduction ») et Déployer le modèle. Il existe deux façons de déployer des modèles dans Azure DevOps Services. Les deux méthodes fournissent les mêmes résultats. Par conséquent, choisissez celle qui convient le mieux à votre flux de travail.

1. Ajoutez une opération unique au pipeline de build qui exécute le script PowerShell inclus dans le projet de déploiement du groupe de ressources Azure (Deploy-AzureResourceGroup.ps1). Le script copie les artefacts et déploie ensuite le modèle.
2. Ajouter plusieurs étapes de build à Azure DevOps, chacune effectuant une tâche intermédiaire.

Cet article présente les deux options. La première option a l’avantage d’utiliser le script utilisé par les développeurs dans Visual Studio et de garantir une cohérence tout au long du cycle de vie. La deuxième option est une alternative pratique au script intégré. Les deux procédures partent du principe que vous disposez déjà d’un projet de déploiement Visual Studio contrôlé dans Azure DevOps Services.

## <a name="copy-artifacts-to-azure"></a>Copier des artefacts sur Azure
Quel que soit le scénario, si vous disposez de tous les artefacts nécessaires au déploiement du modèle, vous devez octroyer un accès à Azure Resource Manager. Ces artefacts peuvent inclure des fichiers tels que :

* des modèles imbriqués
* des scripts de configuration et DSC
* fichiers binaires d’application

### <a name="nested-templates-and-configuration-scripts"></a>Modèles imbriqués et les scripts de configuration
Lorsque vous utilisez les modèles fournis par Visual Studio (ou générés à l’aide d’extraits de code Visual Studio), le script PowerShell ne se contente pas de préparer les artefacts. Elle ajuste également l’URI correspondant aux différentes ressources de déploiement. Le script copie les artefacts vers un conteneur sécurisé dans Azure, crée un jeton SAP pour ce conteneur, puis transmet ces informations au déploiement du modèle. Consultez la section [Créer un modèle de déploiement](https://msdn.microsoft.com/library/azure/dn790564.aspx) pour en savoir plus sur les modèles imbriqués.  Quand vous utilisez des tâches dans Azure DevOps Services, vous devez sélectionner les tâches appropriées pour votre déploiement de modèle et, si nécessaire, transmettre les valeurs de paramètre de l’étape intermédiaire au déploiement du modèle.

## <a name="set-up-continuous-deployment-in-azure-pipelines"></a>Configurer le déploiement continu dans Azure Pipelines
Pour appeler le script PowerShell dans Azure Pipelines, vous devez mettre à jour votre pipeline de build. En bref, les étapes sont :

1. la modification du pipeline de build.
2. la configuration de l’autorisation Azure dans les Azure Pipelines.
3. l’ajout d’une étape de build d’Azure PowerShell faisant référence au script PowerShell dans le projet de déploiement de groupe de ressources Azure.
4. la définition de la valeur du paramètre *-ArtifactsStagingDirectory* pour qu’il fonctionne avec un projet créé dans Azure Pipelines.

### <a name="detailed-walkthrough-for-option-1"></a>Procédure pas à pas pour l’option 1
Les procédures suivantes vous guident lors des étapes nécessaires à la configuration d’un déploiement continu dans Azure DevOps Services à l’aide d’une tâche unique qui exécute le script PowerShell dans votre projet.

1. Modifiez votre pipeline de build de Azure DevOps Services et ajoutez une étape de build Azure PowerShell. Choisissez le pipeline de build sous la catégorie **Pipelines de build**, puis choisissez le lien **Modifier**.

   ![Modifier le pipeline de build](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough1.png)
2. Ajoutez une nouvelle étape **Azure PowerShell** au pipeline de build, puis sélectionnez **Ajouter une étape de build…**. disproportionnée.

   ![Ajouter une étape de génération](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough2.png)
3. Choisissez la catégorie **Déployer une tâche**, sélectionnez la tâche **Azure PowerShell**, puis choisissez son bouton **Ajouter**.

   ![Ajouter des tâches](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough3.png)
4. Choisissez l’étape de build **Azure PowerShell** , puis renseignez ses valeurs.

   1. Si vous disposez déjà d’un point de terminaison de service Azure ajouté à Azure DevOps Services, sélectionnez l’abonnement dans la zone de liste déroulante **Abonnement Azure**, puis passez à la section suivante.

      Si vous n’avez pas de point de terminaison de service Azure dans Azure DevOps Services, vous devez en ajouter un. Cette sous-section vous guide dans la procédure. Si votre compte Azure utilise un compte Microsoft (tel que Hotmail), vous devez procéder comme suit pour obtenir l’authentification d’un principal de service.

   2. Choisissez le lien **Gérer** en regard de la zone de liste déroulante **Abonnement Azure**.

      ![Gérer les abonnements Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough4.png)
   3. Choisissez **Azure** dans la zone de liste déroulante **Nouveau point de terminaison de Service**.

      ![Nouveau point de terminaison de service](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough5.png)
   4. Dans la boîte de dialogue **Ajouter un abonnement Azure**, sélectionnez l’option **Principal du service**.

      ![Option du principal de service](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough6.png)
   5. Ajoutez les informations de votre abonnement Azure à la boîte de dialogue **Ajouter un abonnement Azure** . Vous devez fournir les éléments suivants :

      * ID d’abonnement
      * Nom d'abonnement
      * ID de principal de service
      * Clé de principal de service
      * ID client
   6. Ajout d’un nom de votre choix à la zone de nom **Abonnement** . Cette valeur apparaîtra plus tard dans la liste déroulante **Abonnement Azure** dans Azure DevOps Services.

   7. Si vous ne connaissez pas votre ID d’abonnement Azure, vous pouvez utiliser une des commandes suivantes pour le récupérer.

      Pour les scripts PowerShell, utilisez :

      `Get-AzureRmSubscription`

      Pour l’interface de ligne de commande Azure, consultez :

      `azure account show`
   8. Pour obtenir un ID de principal de service, une clé de principal de service et un ID client, suivez la procédure dans [Création de l’application Active Directory et du principal du service à l’aide du portail](/azure/azure-resource-manager/resource-group-create-service-principal-portal) ou [Authentification d’un principal du service à l’aide d’Azure Resource Manager](/azure/azure-resource-manager/resource-group-authenticate-service-principal).
   9. Ajoutez les valeurs de l’ID de principal du service, de la clé de principal du service et de l’ID de locataire dans la boîte de dialogue **Ajouter un abonnement Azure**, puis choisissez le bouton **OK**.

      Vous disposez désormais d’un Principal de service valide à utiliser pour exécuter le script Azure PowerShell.
5. Modifiez le pipeline de build, puis choisissez l’étape de build **Azure PowerShell**. Sélectionnez l’abonnement dans la zone de liste déroulante **Abonnement Azure** . (Si l’abonnement n’apparaît pas, choisissez le bouton **Actualiser** en regard du lien **gérer**.)

   ![Configurer une tâche de génération Azure PowerShell](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough9.png)
6. Fournissez un chemin d’accès pour le script PowerShell Deploy-azureresourcegroup.ps1. Pour ce faire, cliquez sur les points de suspension (...) en regard de la zone **Chemin du script**, accédez au script Deploy-AzureResourceGroup.ps1 dans le dossier **Scripts** de votre projet, sélectionnez-le, puis cliquez sur le bouton **OK**.

   ![Sélectionner le chemin d’accès au script](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough10.png)
7. Après avoir sélectionné le script, mettez à jour le chemin d’accès au script afin de l’exécuter depuis Build.StagingDirectory (répertoire dans lequel *ArtifactsLocation* est défini). Vous pouvez le faire en ajoutant « $(Build.StagingDirectory)/ » au début du chemin de script.

    ![Modifier le chemin d’accès au script](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough11b.png)
8. Dans la zone **Arguments de script** , saisissez les paramètres suivants (sur une seule ligne). Lorsque vous exécutez le script dans Visual Studio, vous pouvez voir comment Visual Studio utilise les paramètres dans la fenêtre **Sortie** . Vous pouvez l’utiliser comme point de départ pour définir les valeurs de paramètre dans l’étape de build.

   | Paramètre | Description |
   | --- | --- |
   | -ResourceGroupLocation |Valeur de l’emplacement géographique où le groupe de ressources est localisé, par exemple **eastus** ou **« USA Est »**. (Ajouter des guillemets simples si le nom comporte un espace). Consultez les [Régions Azure](https://azure.microsoft.com/regions/) pour plus d’informations. |
   | -ResourceGroupName |Nom du groupe de ressources utilisé pour ce déploiement. |
   | -UploadArtifacts |Ce paramètre, quand il est présent, spécifie que les artefacts doivent être chargés vers Azure à partir du système local. Il vous suffit de définir ce commutateur si le déploiement de votre modèle requiert des artefacts supplémentaires pour les phases intermédiaires de l’utilisation du script PowerShell (tels que les scripts de configuration ou les modèles imbriqués). |
   | -StorageAccountName |Nom du compte de stockage utilisé pour les artefacts intermédiaires pour ce déploiement. Ce paramètre est utilisé uniquement si vous mettez en place des artefacts pour le déploiement. Si ce paramètre est fourni, un compte de stockage est créé si le script n’en a pas créé un au cours d’un déploiement précédent. Si le paramètre est spécifié, le compte de stockage doit déjà exister. |
   | -StorageAccountResourceGroupName |Nom du groupe de ressources contenant le compte de stockage. Ce paramètre est obligatoire uniquement si vous fournissez une valeur pour le paramètre StorageAccountName. |
   | -TemplateFile |Chemin d’accès vers le fichier modèle dans le projet de déploiement de groupe de ressources Azure. Pour améliorer la flexibilité, utilisez un chemin d’accès vers ce paramètre relatif à l’emplacement du script PowerShell au lieu d’un chemin d’accès absolu. |
   | -TemplateParametersFile |Chemin d’accès vers le fichier de paramètre dans le projet de déploiement de groupe de ressources Azure. Pour améliorer la flexibilité, utilisez un chemin d’accès vers ce paramètre relatif à l’emplacement du script PowerShell au lieu d’un chemin d’accès absolu. |
   | -ArtifactStagingDirectory |Ce paramètre indique au script PowerShell le dossier à partir duquel les fichiers binaires du projet doivent être copiés. Cette valeur remplace la valeur par défaut utilisée par le script PowerShell. Pour utiliser Azure DevOps Services, définissez la valeur sur : -ArtifactStagingDirectory$(Build.StagingDirectory) |

   Voici un exemple d’arguments de script (ligne divisée pour une meilleure lisibilité) :

   ```
   -ResourceGroupName 'MyGroup' -ResourceGroupLocation 'eastus' -TemplateFile '..\templates\azuredeploy.json'
   -TemplateParametersFile '..\templates\azuredeploy.parameters.json' -UploadArtifacts -StorageAccountName 'mystorageacct'
   –StorageAccountResourceGroupName 'Default-Storage-EastUS' -ArtifactStagingDirectory '$(Build.StagingDirectory)'
   ```

   Lorsque vous avez terminé, la zone **Arguments de script** ressemble en principe à la liste suivante :

   ![Arguments de script](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough12.png)
9. Une fois que vous avez ajouté tous les éléments requis pour l’étape de build Azure PowerShell, choisissez le bouton **File d’attente** pour générer le projet. L’écran **Build** affiche la sortie du script PowerShell.

### <a name="detailed-walkthrough-for-option-2"></a>Procédure pas à pas pour l’option 2
Les procédures suivantes vous guident lors des étapes nécessaires à la configuration d’un déploiement continu dans Azure DevOps Services à l’aide des tâches intégrées.

1. Modifiez votre pipeline de build Azure DevOps Services pour ajouter deux nouvelles étapes de génération. Choisissez le pipeline de build sous la catégorie **Définitions de build**, puis choisissez le lien **Modifier**.

   ![Modifier la définition de build](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough13.png)
2. Ajoutez les nouvelles étapes de génération au pipeline de build à l’aide du bouton **Ajouter une étape de génération...** disproportionnée.

   ![Ajouter une étape de génération](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough14.png)
3. Choisissez la catégorie de tâche **Déployer**, sélectionnez la tâche **Copie de fichiers Azure**, puis choisissez son bouton **Ajouter**.

   ![Ajouter la tâche Copie de fichiers Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough15.png)
4. Choisissez la tâche **Déploiement de groupes de ressources Azure**, cliquez sur son bouton **Ajouter**, puis **fermez** le **Catalogue de tâches**.

   ![Ajouter une tâche Déploiement de groupes de ressources Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough16.png)
5. Choisissez la tâche **Copie de fichiers Azure** et renseignez ses valeurs.

   Si vous disposez déjà d’un point de terminaison de service Azure ajouté à Azure DevOps Services, sélectionnez l’abonnement dans la zone de liste déroulante **Abonnement Azure**. Si vous n’avez pas d’abonnement, consultez les instructions pour en configurer un dans Azure DevOps Services décrites dans la section [Option 1](#detailed-walkthrough-for-option-1).

   * Source : entrez **$(Build.StagingDirectory)**.
   * Type de connexion Azure : sélectionnez **Azure Resource Manager**.
   * Abonnement Azure RM : sélectionnez l’abonnement pour le compte de stockage que vous souhaitez utiliser dans la zone de liste déroulante **Abonnement Azure**. Si l’abonnement n’apparaît pas, choisissez le bouton **Actualiser** en regard du lien **Gérer**.
   * Type de destination : sélectionnez **Objet blob Azure**.
   * Compte de stockage RM : sélectionnez le compte de stockage que vous souhaitez utiliser pour mettre en place des artefacts.
   * Nom du conteneur : entrez le nom du conteneur que vous souhaitez utiliser pour la préparation. Il peut s’agir d’un nom de conteneur valide quelconque, mais il doit être dédié à ce pipeline de build

   Pour les valeurs de sortie :

   * URI du conteneur de stockage : entrez **artifactsLocation**
   * Jeton SAS du conteneur de stockage : entrez **artifactsLocationSasToken**

   ![Configurer la tâche Copie de fichiers Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough17.png)
6. Choisissez l’étape de génération **Déploiement de groupes de ressources Azure**, puis renseignez ses valeurs.

   * Type de connexion Azure : sélectionnez **Azure Resource Manager**.
   * Abonnement Azure RM : sélectionnez l’abonnement pour le déploiement dans la zone de liste déroulante **Abonnement Azure**. Il s’agit généralement du même abonnement qu’à l’étape précédente.
   * Action : sélectionnez **Créer ou mettre à jour un groupe de ressources**.
   * Groupe de ressources : sélectionnez un groupe de ressources ou entrez le nom d’un nouveau groupe de ressources pour le déploiement.
   * Emplacement : sélectionnez l’emplacement du groupe de ressources.
   * Modèle : entrez le chemin d’accès et le nom du modèle à déployer en ajoutant le préfixe **$(Build.StagingDirectory)**, par exemple : **$(Build.StagingDirectory/DSC-CI/azuredeploy.json)**.
   * Paramètres du modèle : entrez le chemin d’accès et le nom des paramètres à utiliser en ajoutant le préfixe **$(Build.StagingDirectory)**, par exemple : **$(Build.StagingDirectory/DSC-CI/azuredeploy.parameters.json)**.
   * Remplacer les paramètres de modèle : entrez ou copiez et collez le code suivant :

     ```
     -_artifactsLocation $(artifactsLocation) -_artifactsLocationSasToken (ConvertTo-SecureString -String "$(artifactsLocationSasToken)" -AsPlainText -Force)
     ```
     ![Configurer une tâche Déploiement de groupes de ressources Azure](media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough18.png)
7. Une fois que vous avez ajouté tous les éléments requis, enregistrez le pipeline de build et choisissez **Mettre la nouvelle build en file d’attente** en haut.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur Azure Resource Manager et les groupes de ressources Azure, voir l’article [Présentation d’Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) .
