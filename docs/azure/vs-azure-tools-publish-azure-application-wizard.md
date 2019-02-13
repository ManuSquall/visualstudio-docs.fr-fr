---
title: Publier un service cloud Azure
description: Découvrez comment configurer les différents paramètres de l’Assistant Publication d’application Azure dans Visual Studio
author: ghogen
manager: jillfra
assetId: 7d8f1ac9-e439-47e0-a183-0642c4ea1920
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 312a7e072ff5dfbe1a462abb68c8a74a42823e82
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907813"
---
# <a name="using-the-visual-studio-publish-azure-application-wizard"></a>Utilisation de l’Assistant Publication d’application Azure dans Visual Studio

Une fois que vous avez développé une application web dans Visual Studio, vous pouvez publier cette application dans un service cloud Azure à l’aide de l’Assistant **Publication d’application Azure**.

> [!Note]
> Cet article concerne le déploiement sur des services cloud, pas sur des sites web. Pour plus d'informations sur le déploiement sur des sites web, consultez [Déploiement d'un site web Azure](https://social.msdn.microsoft.com/Search/windowsazure?query=How%20to%20Deploy%20an%20Azure%20Web%20Site&Refinement=138&ac=4#refinementChanges=117&pageNumber=1&showMore=false).

## <a name="accessing-the-publish-azure-application-wizard"></a>Accès à l’Assistant Publication d’application Azure

Vous pouvez accéder à l’Assistant Publication d’application Azure de deux manières en fonction de votre type de projet Visual Studio.

**Si vous avez un projet de service cloud Azure :**

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis, dans le menu contextuel, sélectionnez **Publier**.

**Si vous avez un projet d’application web qui n’est pas activé pour Azure :**

1. Créez ou ouvrez un projet de service cloud Azure dans Visual Studio.

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis, dans le menu contextuel, sélectionnez **Convertir** > **Convert to Azure Cloud Service Project (Convertir en projet de service cloud Azure)**.

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet Azure récemment connu, puis, dans le menu contextuel, sélectionnez **Publier**.

## <a name="sign-in-page"></a>page de connexion

![page de connexion](./media/vs-azure-tools-publish-azure-application-wizard/sign-in.png)

**Compte** : sélectionnez un compte ou **Ajouter un compte** dans la liste déroulante des comptes.

**Choisir votre abonnement** : choisissez l’abonnement à utiliser pour votre déploiement.

## <a name="settings-page---common-settings-tab"></a>Page Paramètres - Onglet Paramètres communs

![Paramètres courants](./media/vs-azure-tools-publish-azure-application-wizard/settings-common-settings.png)

**Service cloud** : dans la liste déroulante, sélectionnez un service cloud existant ou **&lt;Créer un nouveau&gt;**, puis créez un service cloud. Le centre de données s’affiche entre parenthèses pour chaque service cloud. Il est recommandé que l’emplacement du centre de données du service cloud soit identique à celui du compte de stockage (Paramètres avancés).

**Environnement** : sélectionnez **Production** ou **Intermédiaire**. Choisissez l’environnement intermédiaire si vous souhaitez déployer votre application dans un environnement de test.

**Configuration de build** : sélectionnez **Déboguer** ou **Version finale**.

**Configuration de service** : sélectionnez **Cloud** ou **Local**.

**Activer le Bureau à distance pour tous les rôles** : Sélectionnez cette option si vous souhaitez pouvoir vous connecter à distance au service. Cette option est principalement utilisée pour le dépannage. Pour plus d’informations, consultez la page [Activer la Connexion Bureau à distance pour un rôle dans Azure Cloud Services avec Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

**Activer Web Deploy pour tous les rôles web** : Sélectionnez cette option pour activer le déploiement web du service. Vous devez aussi sélectionner l’option **Activer le Bureau à distance pour tous les rôles** pour utiliser cette fonctionnalité. Pour plus d’informations, consultez [Publication d’un service cloud en utilisant Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

## <a name="settings-page---advanced-settings-tab"></a>Page Paramètres - Onglet Paramètres avancés

![Paramètres avancés](./media/vs-azure-tools-publish-azure-application-wizard/settings-advanced-settings.png)

**Étiquette de déploiement** : acceptez le nom par défaut ou entrez le nom de votre choix. Pour ajouter la date à l'étiquette de déploiement, laissez la case cochée.

**Compte de stockage** : sélectionnez le compte de stockage que vous souhaitez utiliser pour ce déploiement, **&lt;Créer un nouveau&gt; pour créer un compte de stockage. Le centre de données s’affiche entre parenthèses pour chaque compte de stockage. Il est recommandé que l’emplacement du centre de données du compte de stockage soit identique à celui du service cloud (Paramètres avancés).

Le compte de stockage Azure stocke le package pour le déploiement de l'application. Une fois l'application déployée, le package est supprimé du compte de stockage.

**Delete deployment on failure (Supprimer le déploiement en cas d’échec)**  : sélectionnez cette option pour supprimer le déploiement si des erreurs sont détectées pendant la publication. Cette case doit être décochée si vous souhaitez conserver une adresse IP virtuelle constante pour votre service cloud.

**Mise à jour du déploiement** : sélectionnez cette option si vous souhaitez déployer uniquement des composants mis à jour. Ce type de déploiement peut être plus rapide qu'un déploiement complet. Cette case doit être cochée si vous souhaitez conserver une adresse IP virtuelle constante pour votre service cloud.

**Mise à jour du déploiement - Paramètres** : cette boîte de dialogue vous permet de spécifier le mode de mise à jour des rôles. Si vous choisissez **Mise à jour incrémentielle**, les instances de votre application sont mises à jour l’une après l’autre afin que l’application soit toujours disponible. Si vous choisissez **Mise à jour simultanée**, toutes les instances de votre application sont mises à jour en même temps. La mise à jour simultanée est plus rapide, mais votre service risque de ne pas être disponible pendant la durée du processus de mise à jour.

![Paramètres de déploiement](./media/vs-azure-tools-publish-azure-application-wizard/deployment-settings.png)

**Activer IntelliTrace** : spécifiez si vous souhaitez activer IntelliTrace. Avec IntelliTrace, vous pouvez enregistrer des informations de débogage détaillées pour une instance de rôle exécutée dans Azure. Si vous devez identifier la cause d’un problème, utilisez les journaux IntelliTrace pour exécuter pas à pas votre code à partir de Visual Studio comme s’il était exécuté dans Azure. Pour plus d’informations sur l’utilisation d’IntelliTrace, consultez l’article [Débogage d’un service cloud publié avec IntelliTrace et Visual Studio](./vs-azure-tools-intellitrace-debug-published-cloud-services.md).

**Activer le profilage** : spécifiez si vous souhaitez activer le profilage des performances. Le profileur Visual Studio vous permet d’obtenir une analyse approfondie des ressources de calcul nécessaires à l’exécution de votre service cloud. Pour plus d’informations sur l’utilisation du profileur Visual Studio, consultez l’article [Test des performances d’un service cloud](./vs-azure-tools-performance-profiling-cloud-services.md).

**Enable Remote Debugger for all roles (Activer le débogueur distant pour tous les rôles)**  : spécifiez si vous souhaitez activer le débogage distant. Pour plus d’informations sur le débogage des services cloud à l’aide de Visual Studio, consultez l’article [Débogage d’un service cloud ou d’une machine virtuelle Azure dans Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md).

## <a name="diagnostics-settings-page"></a>Page Paramètres de diagnostic

![Paramètres de diagnostic](./media/vs-azure-tools-publish-azure-application-wizard/diagnostic-settings.png)

Diagnostics vous permet de résoudre les problèmes d’un service cloud Azure (ou d’une machine virtuelle Azure). Pour en savoir plus sur les diagnostics, consultez [Configuration de Diagnostics pour les services cloud et les machines virtuelles Azure](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md). Pour plus d’informations sur Application Insights, consultez [Présentation d’Application Insights](/azure/application-insights/app-insights-overview).

## <a name="summary-page"></a>Page de résumé

![Récapitulatif](./media/vs-azure-tools-publish-azure-application-wizard/summary.png)

**Profil cible** : vous pouvez choisir de créer un profil de publication à partir des paramètres que vous avez choisis. Par exemple, vous pouvez créer un profil pour un environnement de test et un autre pour la production. Pour enregistrer ce profil, sélectionnez l’icône **Enregistrer** . L'Assistant crée le profil et l'enregistre dans le projet Visual Studio. Pour modifier le nom du profil, ouvrez la liste **Profil cible**, puis sélectionnez **&lt;Gérer...&gt;**.

   > [!Note]
   > Le profil de publication s'affiche dans l'Explorateur de solutions dans Visual Studio, et les paramètres du profil sont écrits dans un fichier portant l'extension .azurePubxml. Les paramètres sont enregistrés en tant qu'attributs de balises XML.

## <a name="publishing-your-application"></a>Publication de votre application

Une fois que vous avez configuré tous les paramètres de déploiement de votre projet, sélectionnez **Publier** en bas de la boîte de dialogue. Vous pouvez surveiller l'état du processus dans la fenêtre **Sortie** dans Visual Studio.

## <a name="next-steps"></a>Étapes suivantes

- [Migration et publication d’une application web sur un service cloud Azure à partir de Visual Studio](./vs-azure-tools-migrate-publish-web-app-to-cloud-service.md)

- [Publication d’un service cloud à l’aide des outils Azure](./vs-azure-tools-publishing-a-cloud-service.md)

- [Débogage d’un service cloud publié avec IntelliTrace et Visual Studio](./vs-azure-tools-intellitrace-debug-published-cloud-services.md)

- [Test des performances d’un service cloud](./vs-azure-tools-performance-profiling-cloud-services.md)

- [Configuration de Diagnostics pour les services cloud et les machines virtuelles Azure](./vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md)

- [Présentation d’Application Insights](/azure/application-insights/app-insights-overview)