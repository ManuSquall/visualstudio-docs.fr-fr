---
title: Test des performances d’un service cloud | Microsoft Docs
description: Tester les performances d’un service cloud avec le profileur Visual Studio
author: mikejo5000
manager: douge
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.tgt_pltfrm: multiple
ms.workload: na
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 25b60e5e4072a0523d17082a5c5646e5bb1ade6a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001732"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Test des performances d’un service cloud
## <a name="overview"></a>Vue d'ensemble
Vous pouvez tester les performances d’un service cloud comme suit :

* Utiliser les Diagnostics Azure pour collecter des informations sur les demandes et les connexions et pour consulter les statistiques de site qui montrent comment le service s’effectue à partir d’un point de vue du client. Pour commencer, consultez [configuration des diagnostics pour Azure Cloud Services et Machines virtuelles](http://go.microsoft.com/fwlink/p/?LinkId=623009).
* Utilisez le profileur Visual Studio pour obtenir une analyse approfondie des aspects calculs de la façon dont le service s’exécute. Comme le décrit cette rubrique, vous pouvez utiliser le profileur pour mesurer les performances d’un service exécuté dans Azure. Pour plus d’informations sur l’utilisation du profileur pour mesurer les performances d’un service exécuté localement dans un émulateur de calcul, consultez [test des performances d’un Azure Cloud Service localement à l’émulateur de calcul avec le Visual Studio Profiler](http://go.microsoft.com/fwlink/p/?LinkId=262845).

## <a name="choosing-a-performance-testing-method"></a>Choix d’une méthode de test de performances
### <a name="use-azure-diagnostics-to-collect"></a>Utilisez Azure Diagnostics à collecter :
* Statistiques sur les pages web ou des services, tels que les demandes et les connexions.
* Statistiques sur les rôles, tels que la fréquence à laquelle un rôle est redémarré.
* Ensemble d’informations sur l’utilisation de la mémoire, telles que le pourcentage de temps que le garbage collector prend ou la mémoire définie d’un rôle en cours d’exécution.

### <a name="use-the-visual-studio-profiler-to"></a>Utilisez le profileur Visual Studio pour :
* Identifier les fonctions prenant le plus de temps.
* Mesurer combien de temps prend chaque partie d’un programme intensif.
* Comparer les rapports de performances détaillées pour les deux versions d’un service.
* Analyser l’allocation de mémoire plus en détail que le niveau d’allocations de mémoire individuelles.
* Analyser les problèmes d’accès concurrentiel dans du code multithread.

Lorsque vous utilisez le profileur, vous pouvez collecter des données quand un service cloud s’exécute localement ou dans Azure.

### <a name="collect-profiling-data-locally-to"></a>Collecter les données de profilage localement pour :
* Tester les performances d’une partie d’un service cloud, telles que l’exécution du rôle de travail spécifique, ce qui ne nécessite pas une charge simulée réaliste.
* Tester les performances d’un service cloud de manière isolée, dans des conditions contrôlées.
* Tester les performances d’un service cloud avant de le déployer vers Azure.
* Tester les performances d’un service de cloud privé, sans perturber les déploiements existants.
* Tester les performances du service sans encourir de frais pour l’exécution dans Azure.

### <a name="collect-profiling-data-in-azure-to"></a>Collecter les données de profilage dans Azure pour :
* Tester les performances d’un service cloud sous une charge simulée ou réelle.
* Utilisez la méthode d’instrumentation de la collecte de données de profilage, comme cette rubrique décrit plus loin.
* Tester les performances du service dans le même environnement que lorsque le service s’exécute en production.

Vous simulez généralement une charge dans les conditions de contrainte ou les services de cloud de test sous normal.

## <a name="profiling-a-cloud-service-in-azure"></a>Profilage d’un service cloud dans Azure
Lorsque vous publiez votre service cloud à partir de Visual Studio, vous pouvez le service de profil et spécifier les paramètres de profilage qui vous donnent les informations que vous souhaitez. Une session de profilage est démarrée pour chaque instance d’un rôle. Pour plus d’informations sur la façon de publier votre service depuis Visual Studio, consultez [publication sur un Service Cloud Azure à partir de Visual Studio](https://msdn.microsoft.com/library/azure/ee460772.aspx).

Pour plus d’informations sur le profilage des performances dans Visual Studio, consultez [Guide du débutant en profilage des performances](https://msdn.microsoft.com/library/azure/ms182372.aspx) et [analyse des performances des applications à l’aide des outils de profilage](https://msdn.microsoft.com/library/azure/z9z62c29.aspx).

> [!NOTE]
> Vous pouvez activer IntelliTrace ou le profilage lorsque vous publiez votre service cloud. Vous ne pouvez pas activer les deux.
> 
> 

### <a name="profiler-collection-methods"></a>Méthodes de collecte de Profiler
Vous pouvez utiliser plusieurs méthodes de collecte pour le profilage, en fonction de vos problèmes de performances :

* **Échantillonnage de l’UC** -cette méthode collecte des statistiques d’application qui sont utiles pour l’analyse initiale des problèmes d’utilisation du processeur. Échantillonnage de l’UC est la méthode conseillée pour commencer la plupart des investigations sur les performances. Il existe un faible impact sur l’application que vous profilez lorsque vous collectez des données d’échantillonnage d’UC.
* **Instrumentation** -cette méthode collecte des données de temporisation détaillées qui sont utiles pour une analyse ciblée et pour analyser les problèmes de performances d’entrée/sortie. La méthode d’instrumentation enregistre chaque entrée, sortie et appel de fonction des fonctions dans un module pendant une exécution du profilage. Cette méthode est pratique pour rassembler des informations chronologiques détaillées sur une section de votre code, et pour comprendre l’impact des opérations d’entrée et de sortie sur les performances de l’application. Cette méthode est désactivée pour un ordinateur exécutant un système d’exploitation 32 bits. Cette option est disponible uniquement lorsque vous exécutez le service cloud dans Azure, pas localement dans l’émulateur de calcul.
* **Allocation de mémoire .NET** -cette méthode collecte des données d’allocation de mémoire .NET Framework à l’aide de la méthode de profilage par échantillonnage. Les données collectées incluent le nombre et la taille des objets alloués.
* **Accès concurrentiel** -cette méthode collecte des données de conflit de ressources et les données de l’exécution de processus et thread qui est utiles pour analyser les applications multithread et multiprocessues. La méthode de concurrence collecte des données pour chaque événement qui bloque l’exécution de votre code, comme quand un thread attend que l’accès bloqué à une ressource de l’application soit libéré. Cette méthode est pratique pour l’analyse des applications multithreads.
* Vous pouvez également activer **profilage d’Interaction de couche**, qui fournit des informations supplémentaires sur les temps d’exécution de ADO.NET synchrones appelle dans les fonctions des applications multicouches qui communiquent avec une ou plusieurs bases de données. Vous pouvez collecter des données d’interaction de couche avec n’importe quelle méthode de profilage. Pour plus d’informations sur le profilage d’interaction de couche, consultez [vue Interactions de couche](https://msdn.microsoft.com/library/azure/dd557764.aspx).

## <a name="configuring-profiling-settings"></a>Configuration des paramètres de profilage
L’illustration suivante montre comment configurer vos paramètres de profilage à partir de la boîte de dialogue Publier une Application Azure.

![Configurer des paramètres de profilage](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> Pour activer la **activer le profilage** case à cocher, vous le profileur devez être installé sur l’ordinateur local que vous utilisez pour publier votre service cloud. Par défaut, le profileur est installé lorsque vous installez Visual Studio.
> 
> 

### <a name="to-configure-profiling-settings"></a>Pour configurer les paramètres de profilage
1. Dans l’Explorateur de solutions, ouvrez le menu contextuel pour votre projet Windows Azure, puis choisissez **publier**. Pour obtenir des instructions détaillées sur la façon de publier un service cloud, consultez [publication d’un service cloud à l’aide de Windows Azure tools](http://go.microsoft.com/fwlink/p?LinkId=623012).
2. Dans le **publier l’Application Azure** boîte de dialogue, choisissez le **paramètres avancés** onglet.
3. Pour activer le profilage, sélectionnez le **activer le profilage** case à cocher.
4. Pour configurer vos paramètres de profilage, choisissez le **paramètres** lien hypertexte. La boîte de dialogue Paramètres de profilage s’affiche.
5. À partir de la **quelle méthode de profilage voulez-vous utiliser** cases d’option, choisissez le type de profilage que vous avez besoin.
6. Pour collecter la données de profilage d’interaction de couche, cochez la **activer le profilage d’Interaction de couche** case à cocher.
7. Pour enregistrer les paramètres, choisissez le **OK** bouton.
   
    Lorsque vous publiez cette application, ces paramètres sont utilisés pour créer la session de profilage pour chaque rôle.

## <a name="viewing-profiling-reports"></a>Affichage des rapports de profilage
Une session de profilage est créée pour chaque instance d’un rôle dans votre service cloud. Pour afficher vos rapports de profilage de chaque session à partir de Visual Studio, vous pouvez afficher la fenêtre Explorateur de serveurs et puis choisissez le nœud de calcul Azure pour sélectionner une instance d’un rôle. Vous pouvez ensuite afficher le rapport de profilage comme indiqué dans l’illustration suivante.

![Afficher le rapport de profilage à partir d’Azure](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Pour afficher des rapports de profilage
1. Pour afficher la fenêtre Explorateur de serveurs dans Visual Studio, dans la barre de menus choisissez Affichage, Explorateur de serveurs.
2. Choisissez le nœud de calcul Azure, puis le nœud de déploiement Azure pour le service cloud que vous avez sélectionné au profil quand vous avez publié à partir de Visual Studio.
3. Pour afficher des rapports de profilage pour une instance, choisissez le rôle dans le service, ouvrez le menu contextuel pour une instance spécifique, puis **afficher le rapport de profilage**.
   
    Le rapport, un fichier .vsp, est maintenant téléchargé à partir d’Azure, et l’état du téléchargement apparaît dans le journal d’activité Azure. Le téléchargement terminé, le rapport de profilage s’affiche dans un onglet dans l’éditeur pour Visual Studio nommé <Role name> *<Instance Number>* <identifier>.vsp. Données de synthèse pour le rapport s’affiche.
4. Pour afficher différentes vues du rapport, dans la liste Affichage actuel, choisissez le type de vue que vous souhaitez. Pour plus d’informations, consultez [vues de rapport outils de profilage](https://msdn.microsoft.com/library/azure/bb385755.aspx).

## <a name="next-steps"></a>Étapes suivantes
[Débogage de Services Cloud](https://msdn.microsoft.com/library/azure/ee405479.aspx)

[Publication d’un Service Cloud Azure depuis Visual Studio](https://msdn.microsoft.com/library/azure/ee460772.aspx)

