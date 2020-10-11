---
title: Utiliser un environnement lab pour DevOps
ms.date: 05/02/2017
ms.topic: how-to
helpviewer_keywords:
- lab environment, test lab
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 1a5958b03b9797882b3df37f4ba99c75ff832d22
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928106"
---
# <a name="use-a-lab-environment-for-your-devops"></a>Utiliser un environnement lab pour votre DevOps

Un environnement lab est une collection d'ordinateurs physiques et virtuels que vous pouvez utiliser pour développer et tester des applications. Un environnement lab peut contenir plusieurs rôles nécessaires pour tester des applications multicouches, telles que les postes de travail, les serveurs web et les serveurs de bases de données. En outre, vous pouvez utiliser un flux de travail de build, de déploiement et de test avec votre environnement lab pour automatiser le processus de build, de déploiement et d'exécution des tests automatisés sur votre application.

* **Utiliser un plan de test pour exécuter des tests automatisés** : vous pouvez exécuter une collection de tests automatisés, appelée un *plan de test*, et en voir la progression.

* **Utiliser un flux de travail générer-déployer-tester** : le flux de travail générer-déployer-tester permet de tester les applications multiniveaux de façon automatisée. Exemple typique d’un tel flux de travail : création d’une build, déploiement des fichiers de build sur les ordinateurs adaptés au sein d’un environnement lab, puis exécution de tests automatisés. De plus, il est possible de programmer l'exécution du workflow à intervalles spécifiques.

* **Collecter des données de diagnostic sur tous les ordinateurs, y compris pendant les tests manuels** : vous pouvez collecter des données de diagnostic sur plusieurs ordinateurs en même temps. Par exemple, au cours d’un même test, vous pouvez collecter des données relatives à IntelliTrace, à l’impact du test et d’autres types de données, sur un serveur web, un serveur de bases de données et un client.

Voici quelques-unes des topologies d’environnements lab les plus courantes :

| Topologie | Description |
|---|---|
|![Topologie serveur uniquement](../media/topology_backend.png)| Cet environnement lab a une *topologie de type serveur*, qui est souvent utilisée pour exécuter des tests manuels sur des applications serveur, et qui permet aux testeurs d’utiliser leurs propres ordinateurs clients pour vérifier la présence de bogues dans l’environnement. Dans une topologie de serveur principal, l'environnement lab comprend uniquement des serveurs. Quand vous utilisez ce type de topologie, vous connectez les serveurs de l'environnement lab à l'aide d'un ordinateur client extérieur à l'environnement.|
|![Environnement lab cloud](../media/topology_cloud.png)| Cet environnement lab fournit des fonctionnalités similaires, ainsi que des fonctionnalités comme la _topologie de type serveur_, mais élimine l’obligation pour les machines physiques ou virtuelles de s’exécuter dans un environnement local, ce qui peut réduire les temps d’installation, simplifier la maintenance et réduire les coûts. La configuration de plusieurs sites web et plusieurs machines virtuelles en même temps qu’une mise en réseau personnalisée est rapide et facile dans un environnement cloud comme Microsoft Azure.|
|![Environnement lab du client serveur](../media/topology_clientserver.png)| Cet environnement lab a une *topologie de type client-serveur*, qui est souvent utilisée pour tester une application comprenant à la fois des composants serveur et client. Dans une topologie de type client/serveur, tous les ordinateurs clients et serveurs utilisés pour tester l'application se trouvent dans l'environnement lab. Cette topologie vous permet de collecter des données de test sur tous les ordinateurs concernés par vos tests.|

:::row:::
    :::column:::
        ![Icône représentant une caméra pour les vidéos](../../install/media/video-icon.png)
    :::column-end:::
    :::column:::
        [Regardez une vidéo](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Managing-lab-environments-for-testing) sur la gestion des environnements lab en vue de tests.
    :::column-end:::
:::row-end:::

## <a name="use-the-cloud-with-azure-pipelines-or-team-foundation-server-build-and-release"></a>Utiliser le cloud avec les fonctionnalités Build et mise en production d’Azure Pipelines ou de Team Foundation Server

Vous pouvez effectuer des tests automatisés et automatiser le cycle générer-déployer-tester en utilisant les fonctionnalités de [build et de mise en production](/azure/devops/pipelines/index?view=vsts&preserve-view=true) de Team Foundation Server (TFS) et d’Azure Test Plans. En voici quelques-uns des avantages :

* Vous n’avez pas besoin d’un contrôleur de build ni d’un contrôleur de test.
* L’agent de test est installé via une tâche dans le cadre de la génération ou de la mise en production.
* Il est facile de personnaliser les étapes de déploiement. Vous n’êtes plus limité à l’utilisation d’un seul script. Vous pouvez également tirer parti des nombreuses tâches qui sont disponibles dans le produit ainsi que dans Visual Studio Marketplace.
* Vous n’avez pas à gérer des suites de tests. Vous pouvez exécuter des tests directement à partir des fichiers binaires.
* Vous obtenez des rapports intégrés plus riches pour les tests exécutés dans chaque build ou chaque version mise en production.
* Vous pouvez suivre les ressources (version, build, éléments de travail, validations) qui sont actuellement déployées et testées dans chaque environnement.
* Vous pouvez personnaliser et étendre l’automatisation pour déployer facilement sur plusieurs environnements de test, et même en production.
* Vous pouvez planifier l’automatisation de façon à ce qu’elle soit déclenchée chaque fois qu’un archivage ou une validation se produit, ou chaque jour à un moment donné.

Pour plus d'informations, consultez [Utiliser Build ou Release Management](use-build-or-rm-instead-of-lab-management.md).

::: moniker range="vs-2017"
## <a name="use-the-visual-studio-lab-management-features-of-microsoft-test-manager"></a>Utiliser les fonctionnalités de Visual Studio Lab Management de Microsoft Test Manager

Vous pouvez créer et gérer des environnements lab avec les fonctionnalités de Visual Studio Lab Management de Microsoft Test Manager quand vous utilisez Visual Studio Enterprise.

Lab Management installe automatiquement des agents de test sur tous les ordinateurs de votre environnement.

Si vous utilisez Lab Management conjointement à System Center Virtual Machine Manager (SCVMM), vous bénéficierez des avantages suivants concernant les environnements lab :

* **Reproduire rapidement des configurations d’ordinateurs** : vous pouvez stocker des collections de machines virtuelles qui sont configurées pour recréer des environnements de production classiques. Vous pourrez ensuite exécuter chaque série de tests sur une nouvelle copie d’un environnement stocké.

* **Reproduire les conditions exactes d’un bogue** : quand une série de tests échoue, vous pouvez stocker une copie de l’état de votre environnement Lab et y accéder à partir des résultats de votre build ou d’un élément de travail.

* **Exécuter simultanément plusieurs copies d’un environnement lab** : il est possible d’exécuter simultanément plusieurs copies d’un environnement lab sans conflits de noms.

### <a name="standard-environments-and-scvmm-environments"></a>Environnements standard et environnements SCVMM

Visual Studio Lab Management permet de créer deux types d’environnements lab : les **environnements standard** et les **environnements SCVMM**. Les fonctionnalités de ces environnements sont toutefois différentes.

**Environnements standard** : ils peuvent comprendre à la fois des machines physiques et des machines virtuelles. Il est aussi possible d'ajouter à un environnement standard des machines virtuelles gérées par des frameworks de virtualisation tiers. En outre, les environnements standard ne nécessitent pas de ressources serveur supplémentaires, telles qu'un serveur SCVMM.

**Environnements SCVMM** : ils peuvent contenir seulement des machines virtuelles gérées par SCVMM. Les machines virtuelles des environnements SCVMM peuvent donc s’exécuter seulement dans un framework de virtualisation Hyper-V. Toutefois, les environnements SCVMM fournissent des fonctionnalités d’automatisation et de gestion qui ne sont pas proposées par les environnements standard, notamment :

- **Instantanés d’environnement** : ils contiennent l’état d’un environnement lab, ce qui vous permet de restaurer rapidement un environnement propre ou d’enregistrer l’état d’un environnement qui a subi des modifications. Vous pouvez également utiliser le flux de travail Création-Déploiement-Test pour automatiser le processus d'enregistrement et de restauration des instantanés d'environnement.

- **Environnements stockés** : vous pouvez stocker une copie d’un environnement SCVMM, puis déployer plusieurs copies de cet environnement.

- **Isolement réseau** : l’isolement réseau vous permet d’exécuter simultanément plusieurs copies identiques d’un environnement SCVMM sans conflits de noms d’ordinateurs.

- **Modèles de machines virtuelles** : un modèle de machine virtuelle est une machine virtuelle dont le nom et les autres identificateurs ont été supprimés. Quand un modèle de machine virtuelle est déployé dans un environnement SCVMM, Microsoft Test Manager génère de nouveaux identificateurs. Cela vous permet de déployer plusieurs copies d'un ordinateur virtuel au sein d'un même environnement ou de plusieurs environnements, et d'exécuter simultanément les ordinateurs virtuels.

- **Machines virtuelles stockées** : il s’agit de machines virtuelles qui sont stockées dans votre bibliothèque de projet et qui ont des identificateurs uniques.

> [!NOTE]
> Lab Management ne prend pas en charge SCVMM 2016.

Pour plus d’informations sur SCVMM, consultez [Virtual Machine Manager](/azure/devops/pipelines/?view=vsts&preserve-view=true).

Les environnements standard et SCVMM prennent en charge une grande partie de ces fonctionnalités. Il existe cependant des différences importantes. Le tableau ci-dessous permet de comparer les fonctionnalités qui sont disponibles pour les environnements standard et les environnements SCVMM.

|Fonctionnalité|Environnement SCVMM|Environnements standard|
|-|------------------------|-|
|Test|||
|Exécuter des tests manuels|Prise en charge|Prise en charge|
|Exécuter des tests codés de l'interface utilisateur et autres tests automatisés|Prise en charge|Prise en charge|
|Signaler des bogues riches à l'aide des adaptateurs de diagnostics|Prise en charge|Prise en charge|
|**Déploiement de build**|||
|Flux de travail Création-Déploiement-Test automatisés|Prise en charge|Prise en charge|
|**Création et gestion d’environnements**|||
|Utiliser des ordinateurs physiques en plus des ordinateurs virtuels|Non prise en charge|Prise en charge|
|Utiliser des ordinateurs virtuels tiers|Non prise en charge|Prise en charge|
|Installer automatiquement des agents de test sur les ordinateurs d'un environnement lab|Prise en charge|Prise en charge|
|Enregistrer et déployer l'état d'un environnement lab à l'aide d'instantanés d'environnement|Prise en charge|Non prise en charge|
|Créer des environnements lab à partir de modèles d'ordinateurs virtuels|Prise en charge|Non prise en charge|
|Démarrage, arrêt et prise d'instantané d'environnement|Prise en charge|Non prise en charge|
|Se connecter à l'environnement à l'aide de la visionneuse d'environnement|Prise en charge|Prise en charge|
|Exécuter simultanément plusieurs copies d'un environnement grâce à l'isolement réseau|Prise en charge|Non prise en charge|

### <a name="lab-management-concepts"></a>Terminologie Lab management

Voici quelques termes supplémentaires avec lesquels vous devez vous familiariser avant d'aller plus loin :

|Terme|Description|
|-|-----------------|
|Centre lab|Section de Microsoft Test Manager dans laquelle vous pouvez créer et gérer des environnements lab.|
|Lab de projets Azure DevOps|Collection d'environnements lab configurés de manière à pouvoir être connectés les uns aux autres et à pouvoir exécuter les machines virtuelles qu'ils contiennent.|
|Bibliothèque de projets Azure DevOps|Archive des machines virtuelles stockées, des modèles et des environnements lab stockés qui ont été importés dans le groupe hôte de votre projet. Vous pouvez utiliser les éléments de la bibliothèque dans les environnements SCVMM. Toutefois, vous ne pouvez pas les ajouter directement à un environnement standard. Les éléments de la bibliothèque ne peuvent pas être exécutés. Vous pouvez toutefois les utiliser pour déployer un nouvel environnement.|
|Environnement déployé|Environnement lab déployé sur votre lab de projet pour que vous puissiez vous y connecter et exécuter ses ordinateurs.|

Pour plus d'informations sur Lab Management, consultez :

* [Planifier votre lab](/previous-versions/ff756575(v=vs.140))
* [Administrer votre lab](/previous-versions/dd936084(v=vs.140))
* [Configuration de Lab Management pour les environnements SCVMM](/previous-versions/dd380687(v=vs.140))
* [Gérer les autorisations](/previous-versions/dd380760(v=vs.140))
* [Modification des configurations Lab Management existantes](/previous-versions/ee704508(v=vs.140))
* [Dépannage](/previous-versions/ee853230(v=vs.140))

Pour plus d’informations sur la configuration des environnements, consultez :

* [Environnements cloud de build et de mise en production](use-build-or-rm-instead-of-lab-management.md)
* [Environnements lab standard](/previous-versions/ee390842(v=vs.140))
* [Environnements (virtuels) SCVMM](/previous-versions/ee943322(v=vs.140))
* [Création et utilisation d’un environnement isolé du réseau](/previous-versions/ee518924(v=vs.140))
::: moniker-end

## <a name="see-also"></a>Voir aussi

* [Installer et configurer des agents de test](../../test/lab-management/install-configure-test-agents.md)
* [Visual Studio Lab Management Guide](/archive/blogs/visualstudioalmrangers/library-of-tooling-and-guidance-solutions-aka-msvsarsolutions)
* [Blog Microsoft DevOps](https://devblogs.microsoft.com/devops/)