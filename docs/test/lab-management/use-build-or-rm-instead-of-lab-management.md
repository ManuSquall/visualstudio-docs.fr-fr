---
title: "Utiliser Build ou Release Management pour les tests automatisés | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: automated testing, lab management, test lab
ms.assetid: F34B0D19-B430-4C01-B402-62A861007E71
caps.latest.revision: "56"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: d103e74c0f6cf40bfd0e6dc26dd5777c6fe11f2f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="use-build-and-release-management-instead-of-lab-management-for-automated-testing"></a>Utiliser Build ou Release Management au lieu de Lab Management pour les tests automatisés

Si vous utilisez Microsoft Test Manager (MTM) et Lab Management pour les tests automatisés ou pour l’automatisation du cycle générer-déployer-tester, cette rubrique vous explique comment atteindre les mêmes objectifs en utilisant les fonctionnalités de [Build &amp; mise en production](https://www.visualstudio.com/team-services/continuous-integration/) de Team Foundation Server (TFS) et de Visual Studio Team Services :

* [Automatisation du cycle générer-déployer-tester](#bdtautomation)

* [Gestion des environnements SCVMM en libre-service](#managescvmm)

Build et Release Management ne prennent pas charge la création en libre-service d’environnements SCVMM isolés du réseau, et il n’est pas prévu de fournir cette prise en charge dans le futur. Il existe cependant quelques [alternatives suggérées](#isolatedenvir).

<a name="bdtautomation"></a>
## <a name="build-deploy-test-automation"></a>Automatisation du cycle générer-déployer-tester

MTM et Lab Management se basent sur une définition de build XAML pour automatiser la génération, le déploiement et le test de vos applications.
Pour atteindre cet objectif, la build XAML s’appuie sur différentes constructions créées dans MTM, comme un environnement lab, des suites de test et des paramètres de test, ainsi que sur différents composants de l’infrastructure, comme un contrôleur de build, des agents de build, un contrôleur de test et des agents de test. Vous pouvez réaliser la même chose avec moins d’étapes en utilisant Build ou Release Management dans TFS et Team Services.

| Étapes | Avec une build XAML | Avec Build ou Release Management |
|-------|----------------------|-----------------|
| Identifiez les machines sur lesquelles déployer la build et exécutez les tests. | Créez un environnement lab standard dans MTM avec ces machines. | N/A |
| Identifiez les tests à exécuter. | Créez une suite de tests dans MTM, créez des cas de test et associez une automatisation à chaque cas de test. Créez des paramètres de test dans MTM en identifiant le rôle des machines dans l’environnement lab dans lequel les tests doivent être exécutés. | Créez de la même façon une suite de tests automatisés dans MTM si vous prévoyez de gérer vos tests via des plans de test. Vous pouvez aussi ignorer cette étape si vous voulez exécuter des tests directement à partir des fichiers binaires de test produits par vos générations. Il n’est pas nécessaire de créer des paramètres de test dans les deux cas. |
| Automatisez le déploiement et les tests. | Créez une définition de build XAML en utilisant LabDefaultTemplate.*.xaml. Spécifiez la build, les suites de tests et l’environnement lab dans la définition de build. | Créez une [définition de build ou une définition de version](https://www.visualstudio.com/team-services/continuous-integration/) avec un même environnement. Exécutez le même script de déploiement (à partir de la définition de build XAML) en utilisant la tâche de ligne de commande, et exécutez les tests automatisés en utilisant les tâches Déploiement de l’agent de test et Exécuter les tests fonctionnels. Spécifiez la liste des machines et leurs informations d’identification comme entrées pour ces tâches. |

Voici quelques-uns des avantages de l’utilisation de Build ou Release Management pour ce scénario :

* Vous n’avez pas besoin d’un contrôleur de build ni d’un contrôleur de test.
* L’agent de test est installé via une tâche dans le cadre de la génération ou de la mise en production.
* Il est facile de personnaliser les étapes de déploiement. Vous n’êtes plus limité à l’utilisation d’un seul script. Vous pouvez également tirer parti des nombreuses tâches qui sont disponibles dans le produit ainsi que dans Visual Studio Marketplace.
* Vous n’avez pas à gérer des suites de tests. Vous pouvez exécuter des tests directement à partir des fichiers binaires.
* Vous obtenez des rapports intégrés plus riches pour les tests exécutés dans chaque build ou chaque version mise en production.
* Vous pouvez suivre les ressources (version, build, éléments de travail, validations) qui sont actuellement déployées et testées dans chaque environnement.
* Vous pouvez personnaliser et étendre l’automatisation pour déployer facilement sur plusieurs environnements de test, et même en production.
* Vous pouvez planifier l’automatisation de façon à ce qu’elle soit déclenchée chaque fois qu’un archivage ou une validation se produit, ou chaque jour à un moment donné.

<a name="managescvmm"></a>
## <a name="self-service-management-of-scvmm-environments"></a>Gestion des environnements SCVMM en libre-service

Le [Centre lab de Microsoft Test Manager](https://msdn.microsoft.com/library/dd997438.aspx) prend en charge la possibilité de gérer une bibliothèque de modèles d’environnement et d’approvisionner des environnements à la demande en utilisant un [serveur SCVMM](https://technet.microsoft.com/system-center-docs/vmm/vmm).

Les fonctionnalités d’approvisionnement en libre-service du Centre lab ont deux objectifs distincts :

* Fournir un moyen plus simple de gérer l’infrastructure. La gestion des modèles de machine virtuelle et d’environnement, ainsi que la création automatique de réseaux privés pour isoler les clones d’environnements les uns des autres, sont des exemples de gestion de l’infrastructure.

* Fournir un moyen plus simple pour les équipes de consommer les machines virtuelles dans leurs activités de test et de déploiement. Le fait de rendre accessible les environnements lab via le même modèle de sécurité de projet d’équipe et l’utilisation intégrée de ces machines virtuelles dans les scénarios de test sont des exemples de consommation facilitée.

Cependant, en raison de l’évolution des systèmes de gestion des clouds publics et privés de plus en plus riches, comme [Microsoft Azure](https://azure.microsoft.com/) et [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/), aucune évolution des fonctions de gestion d’infrastructure n’est présente dans TFS 2017 et ultérieur. Au lieu de cela, c’est la consommation facilitée de ressources gérées via ces infrastructures cloud qui reste en tête des priorités.

Le tableau suivant récapitule les activités standard que vous aviez l’habitude d’effectuer dans le Centre lab, et comment vous pouvez les réaliser via SCVMM ou Azure (s’il s’agit d’activités de gestion d’infrastructure), ou via TFS et Team Services (s’il s’agit d’activités de test ou de déploiement) :

| Étapes | Avec le Centre lab | Avec Build ou Release Management |
|-------|----------------------|-----------------|
| Gérez une bibliothèque de modèles d’environnement. | Créez un environnement lab. Installez les logiciels nécessaires sur les machines virtuelles. Préparez le système et stockez l’environnement sous forme de modèle dans une bibliothèque. | Utilisez la console d’administration SCVMM directement pour créer et gérer des modèles de machine virtuelle ou des modèles de service. Quand vous utilisez Azure, sélectionnez une des [modèles Azure Resource Manager prédéfinis](https://azure.microsoft.com/documentation/templates/) dans la [Place de marché Azure](https://azure.microsoft.com/marketplace/) ou dans les [modèles de démarrage rapide Azure](https://azure.microsoft.com/documentation/templates/). |
| Créez un environnement lab. | Sélectionnez un modèle d’environnement dans la bibliothèque et déployez-le. Spécifiez les paramètres nécessaires pour personnaliser les configurations de machine virtuelle. | Utilisez la console d’administration SCVMM directement pour créer des machines virtuelles ou des instances de service à partir des modèles. Utilisez le portail Azure directement pour créer des ressources. Vous pouvez aussi créer une définition de version avec un environnement. Utilisez les tâches Azure ou des tâches de l’[extension d’intégration de SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) pour créer des machines virtuelles. La création d’une nouvelle version de cette définition équivaut à créer un nouvel environnement dans le Centre lab. |
| Connectez-vous aux machines. | Ouvrez l’environnement lab dans la visionneuse d’environnement. | Utilisez la console d’administration SCVMM directement pour vous connecter aux machines virtuelles. Vous pouvez aussi utiliser l’adresse IP ou les noms DNS des machines virtuelles pour ouvrir des sessions Bureau à distance. |
| Prenez un point de contrôle d’un environnement ou restaurez un environnement à un point de contrôle correct. | Ouvrez l’environnement lab dans la visionneuse d’environnement. Choisissez entre prendre un point de contrôle et restaurer à un point de contrôle antérieur. | Utilisez la console d’administration SCVMM directement pour effectuer ces opérations sur les machines virtuelles. Pour effectuer ces étapes dans le cadre d’une automatisation plus vaste, vous pouvez aussi inclure les tâches du point de contrôle à partir de l’[extension d’intégration de SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) dans le cadre de l’environnement dans une définition de version. |

<a name="isolatedenvir"></a>
## <a name="self-service-creation-of-network-isolated-environments"></a>Création en libre-service d’un environnement isolé du réseau

Un environnement lab isolé du réseau est un groupe de machines virtuelles SCVMM qui peut être cloné en toute sécurité sans provoquer de conflits réseau. Ceci a été effectué dans MTM à l’aide d’une série d’instructions qui ont utilisé un ensemble de cartes réseau pour configurer les machines virtuelles dans un réseau privé, et un autre ensemble de cartes réseau pour configurer les machines virtuelles dans un réseau public.

Avec l’évolution des systèmes de gestion des clouds publics et privés de plus en plus riches, comme [Microsoft Azure](https://azure.microsoft.com/) et [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/), vous pouvez vous appuyer davantage directement sur les outils de gestion cloud pour des fonctionnalités similaires. Il n’existe aucun moyen équivalent pour atteindre cet objectif dans Build et Release Management.

Il est conseillé de prendre en compte les alternatives suivantes si vous avez besoin d’isolement réseau :

* Une des raisons de l’utilisation de l’isolement réseau a été la facilité de configuration de plusieurs clones. Comme chaque clone est une réplique exacte de l’original, les noms et les paramètres de configuration des ordinateurs sont conservés en l’état, ce qui facilite la configuration de nouveaux environnements. Cependant, ce même avantage provoque des problèmes plus tard dans le cycle de vie (par exemple en production), car la façon dont les applications sont déployées au final n’est pas la même. **Au lieu de cela**, vous pouvez envisager de configurer de nouveaux environnements de la même façon que vous configurez l’environnement de production et d’éviter d’utiliser l’isolement réseau.

* Utilisez une infrastructure de cloud public comme [Microsoft Azure](https://azure.microsoft.com/) pour les tests dont vous avez besoin. Vous pouvez facilement utiliser des [modèles Azure Resource Manager](https://azure.microsoft.com/documentation/templates/) de la [Place de marché Azure](https://azure.microsoft.com/marketplace/) ou des [modèles de démarrage rapide Azure](https://azure.microsoft.com/documentation/templates/) pour configurer des groupes de machines virtuelles qui sont connectées via un réseau privé et qui sont exposées au réseau public seulement via un proxy ou une « jumpbox ».
