---
title: À l’aide de Visual Studio Assistant Publication d’Azure Application | Microsoft Docs
description: Découvrez comment configurer les différents paramètres dans le Visual Studio Assistant Publication d’Azure Application
author: ghogen
manager: douge
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: c9c4104d4d07cab7486038a8787ed0c7759abd60
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002024"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Utilisation de l’Assistant Publication d’application Azure de Visual Studio

Une fois que vous développez une application web dans Visual Studio, vous pouvez publier cette application à un service cloud Azure à l’aide de la **publier l’Application Azure** Assistant.

> [!Note]
> Cet article concerne le déploiement de services cloud, pas sur les sites web. Pour plus d’informations sur le déploiement vers des sites web, consultez [comment déployer un Site Web Azure](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>L’accès à l’Assistant Publication d’Application Azure

Vous pouvez accéder à l’Assistant Publication d’Application Azure de deux manières, selon le type de projet Visual Studio que vous avez.

**Si vous avez un projet de service cloud Azure :**

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis, dans le menu contextuel, sélectionnez **publier**.

**Si vous avez un projet d’application web qui n’est pas activé pour Azure :**

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, cliquez sur le projet, puis, dans le menu contextuel, sélectionnez **convertir** > **convertir en projet de Service Cloud Azure**. 

1. Dans **l’Explorateur de solutions**, cliquez sur le projet Azure créé et, dans le menu contextuel, sélectionnez **publier**.

## <a name="sign-in-page"></a>Page de connexion

![Page de connexion](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Compte** - sélectionnez un compte ou **ajouter un compte** dans la liste déroulante de compte.

**Choisissez votre abonnement** -choisir l’abonnement à utiliser pour votre déploiement.

## <a name="settings-page---common-settings-tab"></a>Page paramètres - onglet Paramètres communs

![Paramètres communs](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Service cloud** -à l’aide de la liste déroulante, sélectionnez un cloud existant, service ou sélectionnez  **&lt;créer nouveau >** et créer un service cloud. Le centre de données s’affiche entre parenthèses pour chaque service cloud. Il est recommandé que l’emplacement centre de données pour le service cloud soit identique à celui de l’emplacement du centre de données du compte de stockage (paramètres avancés).

**Environnement** -sélectionnez **Production** ou **intermédiaire**. Choisissez l’environnement intermédiaire si vous souhaitez déployer votre application dans un environnement de test. 

**Configuration de build** -sélectionnez **déboguer** ou **version**.

**Configuration du service** -sélectionnez **Cloud** ou **Local**.

**Activer le Bureau à distance pour tous les rôles** -Sélectionnez cette option si vous souhaitez être en mesure de se connecter à distance au service. Cette option est principalement utilisée pour le dépannage. Pour plus d’informations, consultez [activer une connexion Bureau à distance pour un rôle dans Azure Cloud Services à l’aide de Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Activer Web Deploy pour tous les rôles web** -Sélectionnez cette option pour activer le déploiement web pour le service. Vous devez également sélectionner le **activer le Bureau à distance pour tous les rôles** option pour utiliser cette fonctionnalité. Pour plus d’informations, consultez [publication d’un service cloud à l’aide de Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Page paramètres - onglet Paramètres Avancé

![Paramètres avancés](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Étiquette du déploiement** -acceptez le nom par défaut, ou entrez un nom de votre choix. Pour ajouter la date à l’étiquette de déploiement, laissez la case à cocher. 

**Compte de stockage** -sélectionnez le compte de stockage à utiliser pour ce déploiement, **&lt;créer nouveau > pour créer un compte de stockage. Le centre de données s’affiche entre parenthèses pour chaque compte de stockage. Il est recommandé que l’emplacement du centre de données pour le compte de stockage est identique à l’emplacement du centre de données pour le service cloud (paramètres avancés).

Le compte de stockage Azure stocke le package pour le déploiement d’application. Une fois que l’application est déployée, le package est supprimé du compte de stockage.

**Supprimer le déploiement en cas d’échec** -Sélectionnez cette option pour que le déploiement supprimé si des erreurs se produisent lors de la publication. Cela doit être désactivée si vous souhaitez conserver une adresse IP virtuelle constante pour votre service cloud.

**Mise à jour de déploiement** -Sélectionnez cette option si vous souhaitez déployer uniquement des composants mis à jour. Ce type de déploiement peut être plus rapide qu’un déploiement complet. Cette option doit être activée si vous souhaitez conserver une adresse IP virtuelle constante pour votre service cloud. 

**Mise à jour de déploiement - paramètres** -cette boîte de dialogue est utilisée pour spécifier comment vous souhaitez que les rôles à mettre à jour. Si vous choisissez **mise à jour incrémentielle**, chaque instance de votre application est mise à jour une après l’autre, afin que l’application soit toujours disponible. Si vous choisissez **mise à jour simultanée**, toutes les instances de votre application sont mises à jour en même temps. Mise à jour simultanée est plus rapide, mais votre service ne soient pas disponible pendant le processus de mise à jour.

![Paramètres de déploiement](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**Activer IntelliTrace** -spécifiez si vous souhaitez activer IntelliTrace. Grâce à IntelliTrace, vous pouvez consigner des informations de débogage détaillées pour une instance de rôle lorsqu’il s’exécute dans Azure. Si vous avez besoin rechercher la cause d’un problème, vous pouvez utiliser les journaux IntelliTrace pour parcourir votre code à partir de Visual Studio comme si elle s’exécutait dans Azure. Pour plus d’informations sur l’utilisation d’IntelliTrace, consultez [débogage d’un service cloud publié avec IntelliTrace et Visual Studio](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Activer le profilage** -spécifiez si vous souhaitez activer le profilage des performances. Le profileur Visual Studio permet d’obtenir une analyse approfondie des aspects calculs de la façon dont votre service cloud s’exécute. Pour plus d’informations sur l’utilisation du profileur Visual Studio, consultez [tester les performances d’un service cloud Azure](./vs-azure-tools-performance-profiling-cloud-services.md).

**Activer le débogueur distant pour tous les rôles** -spécifiez si vous souhaitez activer le débogage distant. Pour plus d’informations sur le débogage des services de cloud à l’aide de Visual Studio, consultez [débogage d’un service cloud Azure ou une machine virtuelle dans Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Page Paramètres de diagnostic

![Paramètres de diagnostic](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Diagnostics vous permet de résoudre les problèmes d’un service cloud Azure (ou la machine virtuelle Azure). Pour plus d’informations sur les diagnostics, consultez [configuration des Diagnostics pour Azure Cloud Services et Machines virtuelles](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Pour plus d’informations sur Application Insights, consultez [What ' s Application Insights ?](/azure/application-insights/app-insights-overview.md).

## <a name="summary-page"></a>Page de résumé

![Récapitulatif](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Profil cible** -vous pouvez choisir de créer un profil de publication à partir des paramètres que vous avez choisi. Par exemple, vous pouvez créer un profil pour un environnement de test et un autre pour la production. Pour enregistrer ce profil, choisissez le **enregistrer** icône. L’Assistant crée le profil et l’enregistre dans le projet Visual Studio. Pour modifier le nom du profil, ouvrez le **profil cible** liste, puis choisissez  **&lt;gérer... &gt;**.

   > [!Note]
   > Le profil de publication s’affiche dans l’Explorateur de solutions dans Visual Studio, et les paramètres de profil sont écrits dans un fichier portant l’extension .azurePubxml. Paramètres sont enregistrés en tant qu’attributs des balises XML.

## <a name="publishing-your-application"></a>Publication de votre application

Une fois que vous configurez tous les paramètres de déploiement de votre projet, sélectionnez **publier** en bas de la boîte de dialogue. Vous pouvez surveiller l’état du processus dans le **sortie** fenêtre dans Visual Studio.

## <a name="next-steps"></a>Étapes suivantes

- [Migrer et publier une Application Web à un service cloud Azure à partir de Visual Studio](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Découvrez comment utiliser Visual Studio pour publier un service cloud Azure](./vs-azure-tools-publishing-a-cloud-service.md)

- [Débogage d’un service cloud publié avec IntelliTrace et Visual Studio](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Tester les performances d’un service cloud Azure](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Configuration des Diagnostics pour Azure Cloud Services et Machines virtuelles](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).

- [Nouveautés d’Application Insights ?](/azure/application-insights/app-insights-overview.md)