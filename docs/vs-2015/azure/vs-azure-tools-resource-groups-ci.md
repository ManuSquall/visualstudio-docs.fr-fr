---
title: Intégration continue dans les Services Azure DevOps à l’aide de projets de groupe de ressources Azure | Microsoft Docs
description: Décrit comment configurer l’intégration continue dans les Services Azure DevOps à l’aide de projets de déploiement de groupe de ressources Azure dans Visual Studio.
author: mlearned
manager: douge
ms.assetid: b81c172a-be87-4adc-861e-d20b94be9e38
ms.service: azure-resource-manager
ms.topic: article
ms.workload: azure-vs
ms.date: 08/01/2016
ms.author: mlearned
ms.openlocfilehash: b20a43181ad4d36377e61434b880b491543a6c47
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791603"
---
# <a name="continuous-integration-in-azure-devops-services-using-azure-resource-group-deployment-projects"></a>Intégration continue dans les Services Azure DevOps à l’aide de projets de déploiement de groupe de ressources Azure
Pour déployer un modèle Azure, vous effectuer des tâches dans les différentes étapes : générer, tester, copier sur Azure (également appelé « Intermédiaire ») et déployer le modèle. Il existe deux façons de déployer des modèles dans les Services Azure DevOps. Les deux méthodes fournissent les mêmes résultats, par conséquent, choisissez celle qui convient le mieux à votre flux de travail.

1. Ajouter une étape unique à votre pipeline de build qui exécute le script PowerShell qui est inclus dans le projet de déploiement de groupe de ressources Azure (Deploy-azureresourcegroup.ps1). Le script copie les artefacts et déploie ensuite le modèle.
2. Ajouter que plusieurs Services de DevOps Azure étapes de génération, chacune effectuant une tâche intermédiaire.

Cet article présente les deux options. La première option a l’avantage d’utiliser le même script utilisé par les développeurs dans Visual Studio et de garantir une cohérence tout au long du cycle de vie. La deuxième option est une alternative pratique au script intégré. Les deux procédures supposent que vous disposez déjà d’un projet de déploiement de Visual Studio contrôlé dans les Services Azure DevOps.

## <a name="copy-artifacts-to-azure"></a>Copier des artefacts sur Azure
Quel que soit le scénario, si vous avez tous les artefacts nécessaires au déploiement du modèle, vous devez octroyer un accès d’Azure Resource Manager à. Ces artefacts peuvent inclure des fichiers tels que :

* Modèles imbriqués
* Les scripts de configuration et DSC
* Fichiers binaires d’application

### <a name="nested-templates-and-configuration-scripts"></a>Les modèles imbriqués et les Scripts de Configuration
Lorsque vous utilisez les modèles fournis par Visual Studio (ou généré avec des extraits de code Visual Studio), le script PowerShell ne prépare pas uniquement les artefacts, elle ajuste également l’URI pour les ressources de différents déploiements. Le script, puis copie les artefacts vers un conteneur sécurisé dans Azure, crée un jeton SAP pour ce conteneur, puis transmet ces informations au déploiement du modèle. Consultez [créer un modèle de déploiement](https://msdn.microsoft.com/library/azure/dn790564.aspx) pour en savoir plus sur les modèles imbriqués.  Lorsque vous utilisez des tâches dans les Services Azure DevOps, vous devez sélectionner les tâches appropriées pour votre déploiement de modèle et si nécessaire, transmettre des valeurs de paramètre de l’étape intermédiaire au déploiement du modèle.

## <a name="set-up-continuous-deployment-in-azure-pipelines"></a>Configurer un déploiement continu dans les Pipelines d’Azure
Pour appeler le script PowerShell dans les Pipelines d’Azure, vous devez mettre à jour de votre pipeline de génération. En bref, les étapes sont : 

1. Modifier le pipeline de génération.
2. Configurer l’autorisation Azure dans les Pipelines Azure.
3. Ajouter une étape de build Azure PowerShell qui référence le script PowerShell dans le projet de déploiement de groupe de ressources Azure.
4. Définissez la valeur de la *- ArtifactsStagingDirectory* paramètre fonctionne avec un projet créé dans les Pipelines d’Azure.

### <a name="detailed-walkthrough-for-option-1"></a>Procédure pas à pas détaillées pour l’Option 1
Les procédures suivantes vous guident à travers les étapes nécessaires pour configurer le déploiement continu dans les Services Azure DevOps à l’aide d’une seule tâche qui exécute le script PowerShell dans votre projet. 

1. Modifier votre pipeline de génération de Services de DevOps Azure et ajouter une étape de build Azure PowerShell. Choisissez le pipeline de build sous le **générer des pipelines** catégorie, puis choisissez le **modifier** lien.
   
   ![Modifier le pipeline de build][0]
2. Ajouter un nouveau **Azure PowerShell** étape pour le pipeline de génération de build, puis choisissez le **ajouter une étape de build...** disproportionnée.
   
   ![Ajouter une étape de build][1]
3. Choisissez le **déployer une tâche** catégorie, sélectionnez le **Azure PowerShell** de tâches, puis choisissez son **ajouter** bouton.
   
   ![Ajouter des tâches][2]
4. Choisissez le **Azure PowerShell** étape de génération et renseignez ensuite ses valeurs.
   
   1. Si vous disposez déjà d’un point de terminaison de service Azure ajouté à Azure DevOps Services, sélectionnez l’abonnement dans le **abonnement Azure** zone de liste déroulante, puis passez à la section suivante. 
      
      Si vous n’avez pas un point de terminaison de service Azure dans les Services Azure DevOps, vous devez en ajouter un. Cette sous-section vous accompagne tout au long du processus. Si votre compte Azure utilise un compte Microsoft (tel que Hotmail), vous devez procédez comme suit pour obtenir une authentification de principal du Service.

   2. Choisissez le **gérer** situé en regard du **abonnement Azure** zone de liste déroulante.
      
      ![Gérer les abonnements Azure][3]
   3. Choisissez **Azure** dans le **nouveau point de terminaison de Service** zone de liste déroulante.
      
      ![Nouveau point de terminaison de service][4]
   4. Dans le **ajouter un abonnement Azure** boîte de dialogue, sélectionnez le **principal du Service** option.
      
      ![Option de principal de service][5]
   5. Ajoutez vos informations d’abonnement Azure à le **ajouter un abonnement Azure** boîte de dialogue. Vous devez fournir les éléments suivants :
      
      * Id d’abonnement
      * Nom de l’abonnement
      * Id de principal du service
      * Clé du principal du service
      * Id de locataire
   6. Ajouter un nom de votre choix pour le **abonnement** zone Nom. Cette valeur apparaîtra plus tard dans le **abonnement Azure** liste déroulante, dans les Services Azure DevOps. 

   7. Si vous ne connaissez pas votre ID d’abonnement Azure, vous pouvez utiliser une des commandes suivantes pour la récupérer.
      
      Pour les scripts PowerShell, utilisez :
      
      `Get-AzureRmSubscription`
      
      Pour Azure CLI, utilisez :
      
      `azure account show`
   8. Pour obtenir un ID de locataire, ID de principal du Service et clé du principal du Service, suivez la procédure dans [créer application et Active Directory principal de service à l’aide du portail](/azure/azure-resource-manager/resource-group-create-service-principal-portal) ou [authentifier un principal de service avec Azure Le Gestionnaire de ressources](/azure/azure-resource-manager/resource-group-authenticate-service-principal).
   9. Ajoutez les valeurs d’ID de principal du Service, clé du principal du Service et ID de locataire pour le **ajouter un abonnement Azure** boîte de dialogue zone, puis choisissez le **OK** bouton.
      
      Vous disposez maintenant d’un Principal de Service valide à utiliser pour exécuter le script Azure PowerShell.
5. Modifier le pipeline de génération, puis choisissez le **Azure PowerShell** étape de génération. Sélectionnez l’abonnement dans le **abonnement Azure** zone de liste déroulante. (Si l’abonnement n’apparaît, choisissez le **Actualiser** bouton ensuite le **gérer** lien.) 
   
   ![Configurer la tâche de génération Azure PowerShell][8]
6. Fournir un chemin d’accès au script PowerShell Deploy-azureresourcegroup.ps1. Pour ce faire, cliquez sur le bouton points de suspension (...) à côté du **chemin du Script** , accédez au script PowerShell Deploy-azureresourcegroup.ps1 dans le **Scripts** dossier de votre projet, sélectionnez-le, puis Choisissez le **OK** bouton.    
   
   ![Sélectionnez le chemin d’accès au script][9]
7. Après avoir sélectionné le script, mettez à jour le chemin d’accès au script afin qu’elle est exécutée depuis Build.StagingDirectory (le même répertoire que *ArtifactsLocation* a la valeur). Vous pouvez le faire en ajoutant « $(build.stagingdirectory) / « au début du chemin du script.
   
    ![Modifier le chemin d’accès au script][10]
8. Dans le **Arguments de Script** , entrez les paramètres suivants (dans une seule ligne). Lorsque vous exécutez le script dans Visual Studio, vous pouvez voir comment Visual Studio utilise les paramètres dans le **sortie** fenêtre. Vous pouvez utiliser cela comme point de départ pour définir les valeurs de paramètre dans votre étape de génération.
   
   | Paramètre | Description |
   | --- | --- |
   | -ResourceGroupLocation |La valeur de l’emplacement géographique où le groupe de ressources est localisé, par exemple **eastus** ou **« Est des États-Unis »**. (Ajouter des guillemets simples s’il existe un espace dans le nom). Consultez [régions Azure](https://azure.microsoft.com/regions/) pour plus d’informations. |
   | -ResourceGroupName |Le nom du groupe de ressources utilisé pour ce déploiement. |
   | -UploadArtifacts |Ce paramètre, le cas échéant, spécifie que les artefacts qui doivent être chargés sur Azure à partir du système local. Vous devez uniquement définir ce commutateur si votre déploiement de modèle requiert des artefacts supplémentaires que vous souhaitez effectuer une copie intermédiaire à l’aide du script PowerShell (par exemple, les scripts de configuration ou les modèles imbriqués). |
   | -StorageAccountName |Le nom du compte de stockage utilisé pour les artefacts intermédiaires pour ce déploiement. Ce paramètre est utilisé uniquement si vous mettez en place des artefacts pour le déploiement. Si ce paramètre est fourni, un compte de stockage est créé si le script n’a pas créé une au cours d’un déploiement précédent. Si le paramètre est spécifié, le compte de stockage doit déjà exister. |
   | -StorageAccountResourceGroupName |Le nom du groupe de ressources associé au compte de stockage. Ce paramètre est obligatoire uniquement si vous fournissez une valeur pour le paramètre StorageAccountName. |
   | -TemplateFile |Le chemin d’accès au fichier de modèle dans le projet de déploiement de groupe de ressources Azure. Pour améliorer la flexibilité, utilisez un chemin d’accès pour ce paramètre est relatif à l’emplacement du script PowerShell au lieu d’un chemin d’accès absolu. |
   | -TemplateParametersFile |Le chemin d’accès au fichier de paramètres dans le projet de déploiement de groupe de ressources Azure. Pour améliorer la flexibilité, utilisez un chemin d’accès pour ce paramètre est relatif à l’emplacement du script PowerShell au lieu d’un chemin d’accès absolu. |
   | -ArtifactStagingDirectory |Ce paramètre permet au script PowerShell le dossier à partir duquel les fichiers binaires du projet doivent être copiés. Cette valeur remplace la valeur par défaut utilisée par le script PowerShell. Pour les Services Azure DevOps d’usage, définissez la valeur sur : - ArtifactStagingDirectory $ (build.stagingdirectory) |
   
   Voici un exemple d’arguments de script (ligne divisée pour une meilleure lisibilité) :
   
   ```    
   -ResourceGroupName 'MyGroup' -ResourceGroupLocation 'eastus' -TemplateFile '..\templates\azuredeploy.json' 
   -TemplateParametersFile '..\templates\azuredeploy.parameters.json' -UploadArtifacts -StorageAccountName 'mystorageacct' 
   –StorageAccountResourceGroupName 'Default-Storage-EastUS' -ArtifactStagingDirectory '$(Build.StagingDirectory)'    
   ```
   
   Lorsque vous avez terminé, le **Arguments de Script** zone devrait ressembler à la liste suivante :
   
   ![Arguments de script][11]
9. Une fois que vous avez ajouté tous les éléments requis à l’étape de build Azure PowerShell, choisissez le **file d’attente** bouton pour générer le projet de build. Le **Build** écran montre la sortie du script PowerShell.

### <a name="detailed-walkthrough-for-option-2"></a>Procédure pas à pas détaillées pour l’Option 2
Les procédures suivantes vous guident à travers les étapes nécessaires pour configurer le déploiement continu dans les Services Azure DevOps à l’aide de tâches intégrées.

1. Modifier votre pipeline de génération de Services de DevOps Azure pour ajouter que deux nouvelles étapes de génération. Choisissez le pipeline de build sous le **définitions de Build** catégorie, puis choisissez le **modifier** lien.
   
   ![Modifier la définition de build][12]
2. Ajouter les nouvelles étapes de build pour le pipeline de build à l’aide de la **ajouter une étape de build...** disproportionnée.
   
   ![Ajouter une étape de build][13]
3. Choisissez le **déployer** catégorie de tâche, sélectionnez le **copie de fichiers Azure** de tâches, puis choisissez son **ajouter** bouton.
   
   ![Ajouter une tâche de copie de fichiers Azure][14]
4. Choisissez le **déploiement de groupe de ressources Azure** de tâches, puis choisissez son **ajouter** bouton, puis **fermer** le **catalogue des tâches**.
   
   ![Ajouter une tâche de déploiement de groupe de ressources Azure][15]
5. Choisissez le **copie de fichiers Azure** de tâches et renseignez ses valeurs.
   
   Si vous disposez déjà d’un point de terminaison de service Azure ajouté à Azure DevOps Services, sélectionnez l’abonnement dans le **abonnement Azure** zone de liste déroulante. Si vous n’avez pas d’un abonnement, consultez [Option 1](#detailed-walkthrough-for-option-1) pour obtenir des instructions sur la configuration dans les Services Azure DevOps.
   
   * Source : entrez **$ (build.stagingdirectory)**
   * Type de connexion Azure : sélectionnez **Azure Resource Manager**
   * Abonnement Azure RM : sélectionnez l’abonnement pour le compte de stockage que vous souhaitez utiliser dans le **abonnement Azure** zone de liste déroulante. Si l’abonnement n’apparaît, choisissez le **Actualiser** bouton ensuite le **gérer** lien.
   * Type de destination : sélectionnez **Blob Azure**
   * Compte de stockage RM : sélectionnez le compte de stockage vous souhaitez utiliser pour le transit des artefacts
   * Nom du conteneur : entrez le nom du conteneur que vous souhaitez utiliser pour la préparation ; Il peut être n’importe quel nom de conteneur valide, mais dédié à ce pipeline de build
   
   Pour les valeurs de sortie :
   
   * Entrez le conteneur de stockage URI - **artifactsLocation**
   * Le jeton SAS du conteneur de stockage - entrez **artifactsLocationSasToken**
   
   ![Configurer la tâche de copie de fichiers Azure][16]
6. Choisissez le **déploiement de groupe de ressources Azure** étape de génération et renseignez ensuite ses valeurs.
   
   * Type de connexion Azure : sélectionnez **Azure Resource Manager**
   * Abonnement Azure RM : sélectionnez l’abonnement pour le déploiement dans le **abonnement Azure** zone de liste déroulante. Il s’agit généralement du même abonnement qu’à l’étape précédente
   * Action : sélectionnez **créer ou groupe de ressources de mise à jour**
   * Groupe de ressources : sélectionnez un groupe de ressources ou entrez le nom d’un nouveau groupe de ressources pour le déploiement
   * Emplacement : sélectionnez l’emplacement du groupe de ressources
   * Modèle : entrez le chemin d’accès et le nom du modèle à déployer ajoutant le préfixe **$ (build.stagingdirectory)**, par exemple : **$(Build.StagingDirectory/DSC-CI/azuredeploy.json)**
   * Paramètres du modèle : entrez le chemin d’accès et le nom des paramètres à utiliser, ajoutant **$ (build.stagingdirectory)**, par exemple : **$(Build.StagingDirectory/DSC-CI/azuredeploy.parameters.json)**
   * Remplacer les paramètres de modèle : entrez ou copiez et collez le code suivant :
     
     ```    
     -_artifactsLocation $(artifactsLocation) -_artifactsLocationSasToken (ConvertTo-SecureString -String "$(artifactsLocationSasToken)" -AsPlainText -Force)
     ```
     ![Configurer la tâche de déploiement de groupe de ressources Azure][17]
7. Une fois que vous avez ajouté tous les éléments requis, enregistrez le pipeline de build et choisissez **nouvelle build en file d’attente** en haut.

## <a name="next-steps"></a>Étapes suivantes
Lecture [présentation d’Azure Resource Manager](/azure-resource-manager/resource-group-overview.md) pour en savoir plus sur Azure Resource Manager et les groupes de ressources Azure.

[0]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough1.png
[1]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough2.png
[2]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough3.png
[3]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough4.png
[4]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough5.png
[5]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough6.png
[8]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough9.png
[9]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough10.png
[10]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough11b.png
[11]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough12.png
[12]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough13.png
[13]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough14.png
[14]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough15.png
[15]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough16.png
[16]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough17.png
[17]: media/vs-azure-tools-resource-groups-ci-in-vsts/walkthrough18.png
