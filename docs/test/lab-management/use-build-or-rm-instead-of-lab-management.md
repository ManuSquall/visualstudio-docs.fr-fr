---
title: Utiliser Azure Pipelines pour les tests automatisés
ms.date: 10/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- automated testing, lab management, test lab
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 7a410601b0d7ab6b6a3901333b062e515555ec2d
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50218659"
---
# <a name="use-azure-test-plans-instead-of-lab-management-for-automated-testing"></a>Utiliser Azure Test Plans au lieu de Lab Management pour les tests automatisés

Si vous utilisez Microsoft Test Manager et Lab Management pour les tests automatisés ou pour l’automatisation du cycle générer-déployer-tester, cette rubrique vous explique comment atteindre les mêmes objectifs en utilisant les fonctionnalités de [build et de mise en production](/azure/devops/pipelines/index?view=vsts) d’Azure Pipelines et Team Foundation Server (TFS).

## <a name="build-deploy-test-automation"></a>Automatisation du cycle générer-déployer-tester

Microsoft Test Manager et Lab Management se basent sur une définition de build XAML pour automatiser la génération, le déploiement et le test de vos applications. Pour atteindre cet objectif, la build XAML s’appuie sur différentes constructions créées dans Microsoft Test Manager, comme un environnement lab, des suites de tests et des paramètres de test, ainsi que sur différents composants d’infrastructure, comme un contrôleur de build, des agents de build, un contrôleur de test et des agents de test. Vous pouvez parvenir au même résultat en moins d’étapes grâce à Azure Pipelines ou TFS.

| Étapes | Avec une build XAML | Dans une build ou une mise en production |
|-------|----------------------|-----------------|
| Identifiez les machines sur lesquelles déployer la build et exécutez les tests. | Créez un environnement lab standard dans Microsoft Test Manager avec ces machines. | N/A |
| Identifiez les tests à exécuter. | Créez une suite de tests dans Microsoft Test Manager, créez des cas de test et associez une automatisation à chaque cas de test. Créez des paramètres de test dans Microsoft Test Manager en identifiant le rôle des machines dans l’environnement lab dans lequel les tests doivent être exécutés. | Créez de la même façon une suite de tests automatisés dans Microsoft Test Manager si vous prévoyez de gérer vos tests via des plans de test. Vous pouvez aussi ignorer cette étape si vous voulez exécuter des tests directement à partir des fichiers binaires de test produits par vos générations. Il n’est pas nécessaire de créer des paramètres de test dans les deux cas. |
| Automatisez le déploiement et les tests. | Créez une définition de build XAML en utilisant LabDefaultTemplate.*.xaml. Spécifiez la build, les suites de tests et l’environnement lab dans la définition de build. | Créez un [pipeline de build ou de mise en production](/azure/devops/pipelines/index?view=vsts) avec un seul environnement. Exécutez le même script de déploiement (à partir de la définition de build XAML) en utilisant la tâche de ligne de commande, et exécutez les tests automatisés en utilisant les tâches Déploiement de l’agent de test et Exécuter les tests fonctionnels. Spécifiez la liste des machines et leurs informations d’identification comme entrées pour ces tâches. |

L’utilisation d’Azure Pipelines ou de TFS dans ce scénario offre les avantages suivants :

* Vous n’avez pas besoin d’un contrôleur de build ni d’un contrôleur de test.
* L’agent de test est installé via une tâche dans le cadre de la génération ou de la mise en production.
* Il est facile de personnaliser les étapes de déploiement. Vous n’êtes plus limité à l’utilisation d’un seul script. Vous pouvez également tirer parti des nombreuses tâches qui sont disponibles dans le produit ainsi que dans Visual Studio Marketplace.
* Vous n’avez pas à gérer des suites de tests. Vous pouvez exécuter des tests directement à partir des fichiers binaires.
* Vous obtenez des rapports intégrés plus riches pour les tests exécutés dans chaque build ou chaque version mise en production.
* Vous pouvez suivre les ressources (version, build, éléments de travail, validations) qui sont actuellement déployées et testées dans chaque environnement.
* Vous pouvez personnaliser et étendre l’automatisation pour déployer facilement sur plusieurs environnements de test, et même en production.
* Vous pouvez planifier l’automatisation de façon à ce qu’elle soit déclenchée chaque fois qu’un archivage ou une validation se produit, ou chaque jour à un moment donné.

## <a name="self-service-management-of-scvmm-environments"></a>Gestion des environnements SCVMM en libre-service

Le [Centre de tests de Microsoft Test Manager](/azure/devops/test/mtm/guidance-mtm-usage?view=vsts) prend en charge la gestion d’une bibliothèque de modèles d’environnements, ainsi que le provisionnement d’environnements à la demande à l’aide d’un [serveur SCVMM](/system-center/vmm/overview?view=sc-vmm-1801).

Les fonctionnalités d’approvisionnement en libre-service du Centre lab ont deux objectifs distincts :

* Fournir un moyen plus simple de gérer l’infrastructure. La gestion des modèles de machine virtuelle et d’environnement, ainsi que la création automatique de réseaux privés pour isoler les clones d’environnements les uns des autres, sont des exemples de gestion de l’infrastructure.

* Fournir un moyen plus simple pour les équipes de consommer les machines virtuelles dans leurs activités de test et de déploiement. Le fait de rendre accessible les environnements lab via le même modèle de sécurité de projet et l’utilisation intégrée de ces machines virtuelles dans les scénarios de test sont des exemples de consommation facilitée.

Cependant, en raison de l’évolution des systèmes de gestion des clouds publics et privés de plus en plus riches, comme [Microsoft Azure](https://azure.microsoft.com/) et [Microsoft Azure Stack](https://azure.microsoft.com/overview/azure-stack/), aucune évolution des fonctions de gestion d’infrastructure n’est présente dans TFS 2017 et ultérieur. Au lieu de cela, c’est la consommation facilitée de ressources gérées via ces infrastructures cloud qui reste en tête des priorités.

Le tableau suivant récapitule les activités standard que vous effectuez dans le Centre lab, et comment vous pouvez les réaliser via SCVMM ou Azure (s’il s’agit d’activités de gestion d’infrastructure), ou via TFS et Azure DevOps Services (s’il s’agit d’activités de test ou de déploiement) :

| Étapes | Avec le Centre lab | Dans une build ou une mise en production |
|-------|-----------------|-----------------------|
| Gérez une bibliothèque de modèles d’environnement. | Créez un environnement lab. Installez les logiciels nécessaires sur les machines virtuelles. Préparez le système et stockez l’environnement sous forme de modèle dans une bibliothèque. | Utilisez la console d’administration SCVMM directement pour créer et gérer des modèles de machine virtuelle ou des modèles de service. Lorsque vous utilisez Azure, sélectionnez l’un des [modèles de démarrage rapide Azure](https://azure.microsoft.com/resources/templates/). |
| Créez un environnement lab. | Sélectionnez un modèle d’environnement dans la bibliothèque et déployez-le. Spécifiez les paramètres nécessaires pour personnaliser les configurations de machine virtuelle. | Utilisez la console d’administration SCVMM directement pour créer des machines virtuelles ou des instances de service à partir des modèles. Utilisez le portail Azure directement pour créer des ressources. Vous pouvez aussi créer une définition de version avec un environnement. Utilisez les tâches Azure ou des tâches de l’[extension d’intégration de SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) pour créer des machines virtuelles. La création d’une nouvelle version de cette définition équivaut à créer un nouvel environnement dans le Centre lab. |
| Connectez-vous aux machines. | Ouvrez l’environnement lab dans la visionneuse d’environnement. | Utilisez la console d’administration SCVMM directement pour vous connecter aux machines virtuelles. Vous pouvez aussi utiliser l’adresse IP ou les noms DNS des machines virtuelles pour ouvrir des sessions Bureau à distance. |
| Prenez un point de contrôle d’un environnement ou restaurez un environnement à un point de contrôle correct. | Ouvrez l’environnement lab dans la visionneuse d’environnement. Choisissez entre prendre un point de contrôle et restaurer à un point de contrôle antérieur. | Utilisez la console d’administration SCVMM directement pour effectuer ces opérations sur les machines virtuelles. Pour effectuer ces étapes dans le cadre d’une automatisation plus vaste, vous pouvez aussi inclure les tâches du point de contrôle à partir de l’[extension d’intégration de SCVMM](https://marketplace.visualstudio.com/items?itemname=ms-vscs-rm.scvmmapp) dans le cadre de l’environnement dans une définition de version. |

## <a name="create-network-isolated-environments"></a>Créer des environnements isolés du réseau

Un environnement lab isolé du réseau est un groupe de machines virtuelles SCVMM qui peut être cloné en toute sécurité sans provoquer de conflits réseau. Ceci a été effectué dans MTM à l’aide d’une série d’instructions qui ont utilisé un ensemble de cartes réseau pour configurer les machines virtuelles dans un réseau privé, et un autre ensemble de cartes réseau pour configurer les machines virtuelles dans un réseau public.

Cependant, vous pouvez utiliser Azure Pipelines et TFS, conjointement avec la tâche de génération et de déploiement SCVMM, pour gérer des environnements SCVMM, provisionner des réseaux virtuels isolés et implémenter des scénarios de génération-déploiement-test. Par exemple, vous pouvez utiliser la tâche pour :

* Créer, restaurer et supprimer des points de contrôle
* Créer des machines virtuelles à l’aide d’un modèle
* Démarrer et arrêter des machines virtuelles
* Exécuter des scripts PowerShell personnalisés pour SCVMM

Pour plus d’informations, consultez [Créer un environnement isolé du réseau virtuel pour les scénarios de génération-déploiement-test](/azure/devops/pipelines/targets/create-virtual-network?view=vsts).
