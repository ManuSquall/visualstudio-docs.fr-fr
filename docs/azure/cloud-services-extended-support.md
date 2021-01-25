---
title: Utiliser cloud services (prise en charge étendue) (version préliminaire)
description: En savoir plus sur la création et le déploiement d’un service Cloud (prise en charge étendue) à l’aide de Azure Resource Manager avec Visual Studio
author: ghogen
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 01/25/2021
ms.author: ghogen
monikerRange: '>=vs-2019'
ms.openlocfilehash: ff45cf05a6811c02881c26f76193d4c1f5a5e735
ms.sourcegitcommit: 7d34ab111614ae6bde5fb3c2bb91dd79e29a0a78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2021
ms.locfileid: "98750288"
---
# <a name="create-and-deploy-to-cloud-services-extended-support-in-visual-studio-preview"></a>Créer et déployer des services Cloud (prise en charge étendue) dans Visual Studio (version préliminaire)

À compter de [Visual Studio 2019 version 16,9 (actuellement en préversion](https://visualstudio.microsoft.com/vs/preview) ), vous pouvez travailler avec des services Cloud à l’aide de Azure Resource Manager, ce qui simplifie et modernise grandement la maintenance et la gestion des ressources Azure. Cette option est activée par un nouveau service Azure appelé *services Cloud (prise en charge étendue)*. Vous pouvez publier un service Cloud existant dans cloud services (prise en charge étendue). Pour plus d’informations sur ce service Azure, consultez [la documentation services Cloud (support étendu)](/azure/cloud-services-extended-support/overview).

## <a name="publish-to-cloud-services-extended-support"></a>Publier dans cloud services (prise en charge étendue)

Lorsque vous publiez votre projet de service Cloud Azure existant dans cloud services (prise en charge étendue), vous conservez toujours la possibilité de publier sur un service Cloud Azure classique. Dans Visual Studio 2019 version 16,9 Preview 3 et versions ultérieures, les projets de service Cloud classiques disposent d’une version spéciale de la commande **Publish** , **Publish (prise en charge étendue)**. Cette commande s’affiche dans le menu contextuel de **Explorateur de solutions**.

Il existe quelques différences lors de la publication vers les services Cloud (prise en charge étendue). Par exemple, vous n’êtes pas invité à effectuer des publications dans un environnement **intermédiaire** ou de **production**, car ces emplacements de déploiement ne font pas partie du modèle de publication de prise en charge étendue. Au lieu de cela, avec cloud services (prise en charge étendue), vous pouvez configurer plusieurs déploiements et permuter les déploiements dans le Portail Azure. Bien que les outils Visual Studio permettent de définir ce paramètre dans 16,9 Preview 3, la fonctionnalité d’échange n’est pas activée jusqu’à une version ultérieure des services Cloud (prise en charge étendue) et peut entraîner un échec au moment du déploiement pendant la version préliminaire.

Avant de publier un service Cloud Azure classique dans cloud services (prise en charge étendue), vérifiez les comptes de stockage que votre projet utilise et assurez-vous qu’il s’agit de comptes de stockage v1 ou Storage v2. Les types de comptes de stockage classiques échouent avec un message d’erreur au moment du déploiement. Veillez à vérifier le compte de stockage utilisé par les Diagnostics. Pour vérifier le compte de stockage des diagnostics, consultez [configurer les diagnostics pour les services Cloud et les machines virtuelles Azure](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Si votre service utilise un compte de stockage classique, vous pouvez le mettre à niveau. consultez [mise à niveau vers un compte de stockage à usage général v2](/azure/storage/common/storage-account-upgrade?tabs=azure-portal).  Pour obtenir des informations générales sur les types de comptes de stockage, consultez [vue d’ensemble du compte de stockage](/azure/storage/common/storage-account-overview).

### <a name="to-publish-a-classic-azure-cloud-service-project-to-cloud-services-extended-support"></a>Pour publier un projet de service Cloud Azure classique dans cloud services (prise en charge étendue)

1. Cloud services (support étendu) est actuellement en version préliminaire. Inscrivez la fonctionnalité pour votre abonnement comme suit :

   ```azurepowershell-interactive
   Register-AzProviderFeature -FeatureName CloudServices -ProviderNamespace Microsoft.Compute
   ```

1. Cliquez avec le bouton droit sur le nœud du projet dans votre projet Azure Cloud service (Classic), puis choisissez **publier (support étendu)..**.. L' **Assistant Publication** s’ouvre sur le premier écran.

   ![Choisissez publier (prise en charge étendue) dans le menu](./media/cloud-services-extended-support/publish-commands-on-menu.png)

   L’Assistant **publication** s’affiche.

   ![page de connexion](./media/cloud-services-extended-support/publish-step1.png)

1. **Compte** : sélectionnez un compte ou **Ajouter un compte** dans la liste déroulante des comptes.

1. **Choisir votre abonnement** : choisissez l’abonnement à utiliser pour votre déploiement.

1. Choisissez **suivant** pour passer à la page **paramètres** .

   ![Paramètres courants](./media/cloud-services-extended-support/publish-settings.png)

1. **Service Cloud (prise en charge étendue)** : à l’aide de la liste déroulante, sélectionnez un service Cloud existant (prise en charge étendue) ou sélectionnez **créer**, puis créez-en un. Le centre de données s’affiche entre parenthèses pour chaque service Cloud (prise en charge étendue). Il est recommandé que l’emplacement du centre de données pour le service Cloud (support étendu) soit identique à l’emplacement du centre de données pour le compte de stockage.

   Si vous choisissez de créer un nouveau service, vous verrez la boîte de dialogue **créer un service Cloud (support étendu)** . Spécifiez l’emplacement et le groupe de ressources que vous souhaitez utiliser pour le service Cloud (prise en charge étendue).

   ![Créer un service Cloud (prise en charge étendue)](./media/cloud-services-extended-support/extended-support-dialog.png)

1. **Configuration de build** : sélectionnez **Déboguer** ou **Version finale**.

1. **Configuration de service** : sélectionnez **Cloud** ou **Local**.

1. **Compte de stockage** : sélectionnez le compte de stockage à utiliser pour ce déploiement, ou **créez** -en un pour créer un compte de stockage. La région s’affiche entre parenthèses pour chaque compte de stockage. Il est recommandé que l’emplacement du centre de données du compte de stockage soit identique à celui du service cloud (Paramètres avancés).

   Le compte de stockage Azure stocke le package pour le déploiement de l'application.

1. **Coffre de clés** : spécifiez le coffre de clés qui contient les secrets pour ce service Cloud (prise en charge étendue). Cette option est activée si le Bureau à distance est activé ou si des certificats sont ajoutés à la configuration.

1. **Activer le Bureau à distance pour tous les rôles** : Sélectionnez cette option si vous souhaitez pouvoir vous connecter à distance au service. Vous êtes invité à spécifier les informations d’identification.

   ![Paramètres du Bureau à distance](./media/cloud-services-extended-support/remote-desktop-configuration.png)

1. Choisissez **suivant** pour accéder à la page des **paramètres de diagnostic** .

   ![Paramètres de diagnostic](./media/cloud-services-extended-support/diagnostics-settings.png)

   Les diagnostics vous permettent de dépanner un service Cloud Azure (prise en charge étendue). Pour en savoir plus sur les diagnostics, consultez [Configuration de Diagnostics pour les services cloud et les machines virtuelles Azure](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Pour plus d’informations sur Application Insights, consultez [Présentation d’Application Insights](/azure/application-insights/app-insights-overview).

1. Choisissez **suivant** pour passer à la page **Résumé** .

   ![Résumé](./media/cloud-services-extended-support/publish-summary.png)

1. **Profil cible** : vous pouvez choisir de créer un profil de publication à partir des paramètres que vous avez choisis. Par exemple, vous pouvez créer un profil pour un environnement de test et un autre pour la production. Pour enregistrer ce profil, choisissez l'icône **Enregistrer**. L'Assistant crée le profil et l'enregistre dans le projet Visual Studio. Pour modifier le nom du profil, ouvrez la liste **Profil cible**, puis sélectionnez **Gérer...**.

   > [!Note]
   > Le profil de publication s’affiche dans Explorateur de solutions dans Visual Studio, et les paramètres du profil sont écrits dans un fichier avec une extension *. azurePubxml* . Les paramètres sont enregistrés en tant qu'attributs de balises XML.

1. Une fois que vous avez configuré tous les paramètres de déploiement de votre projet, sélectionnez **Publier** en bas de la boîte de dialogue. Vous pouvez surveiller l’état du processus dans la fenêtre sortie du **Journal d’activité Azure** dans Visual Studio. Choisissez le lien **ouvrir dans le portail** pour 

Félicitations ! Vous avez publié votre projet de service de Cloud Computing (support étendu) sur Azure. Pour publier à nouveau avec les mêmes paramètres, vous pouvez réutiliser le profil de publication ou répéter ces étapes pour en créer un nouveau. Le modèle et les paramètres Azure Resource Manager (ARM) qui sont utilisés pour le déploiement sont enregistrés dans le dossier *bin/ \<configuration\> /Publish* .

## <a name="clean-up-azure-resources"></a>Nettoyage des ressources Azure

Pour nettoyer les ressources Azure que vous avez créées en suivant ce didacticiel, accédez au [portail Azure](https://portal.azure.com), choisissez **groupes de ressources**, recherchez et ouvrez le groupe de ressources que vous avez utilisé pour créer le service Cloud (prise en charge étendue), puis choisissez **supprimer le groupe de ressources**.

## <a name="next-steps"></a>Étapes suivantes

Configurez l’intégration continue (CI) à l’aide du bouton **configurer** sur l’écran de **publication** . Pour plus d’informations, consultez [la documentation Azure pipelines](/azure/devops/pipelines/?view=azure-devops&preserve-view=true).
