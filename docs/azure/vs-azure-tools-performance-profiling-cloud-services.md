---
title: Test des performances d’un service cloud | Microsoft Docs
description: Tester les performances d’un service cloud avec le profileur Visual Studio
author: mikejo5000
manager: jillfra
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.openlocfilehash: fd436a6b7e38c8f76de5d113c326e194e4011155
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2019
ms.locfileid: "58323199"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Test des performances d’un service cloud
## <a name="overview"></a>Vue d'ensemble
Vous pouvez tester les performances d’un service cloud de plusieurs manières :

* Utilisez les diagnostics Azure pour collecter des informations concernant les demandes et les connexions, et pour analyser les statistiques de site qui renseignent sur le fonctionnement du service côté client. Pour la prise en main des diagnostics Azure, consultez [Configuration des diagnostics pour Azure Cloud Services et Azure Virtual Machines](http://go.microsoft.com/fwlink/p/?LinkId=623009).
* Utilisez le profileur Visual Studio pour obtenir une analyse approfondie des ressources de calcul nécessaires à l’exécution du service. Comme l’explique cette rubrique, le profileur permet de mesurer les performances d’un service exécuté dans Azure. Pour plus d’informations sur l’utilisation du profileur pour mesurer les performances pendant l’exécution locale d’un service dans un émulateur de calcul, consultez [Test des performances d’un service cloud local dans l’émulateur de calcul Azure avec le profileur Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=262845).

## <a name="choosing-a-performance-testing-method"></a>Choix d’une méthode de test des performances
### <a name="use-azure-diagnostics-to-collect"></a>Utilisez les diagnostics Azure pour collecter les informations suivantes :
* Statistiques concernant les pages ou services web (par exemple, les demandes et les connexions).
* Statistiques sur les rôles (par exemple, le nombre de fois où un rôle est redémarré).
* Informations générales relatives à l’utilisation de la mémoire (par exemple, le pourcentage de temps que le garbage collector prend ou la mémoire définie pour un rôle en cours d’exécution).

### <a name="use-the-visual-studio-profiler-to"></a>Utilisez le profileur Visual Studio pour effectuer les tâches suivantes :
* Identifier les fonctions prenant le plus de temps.
* Évaluer le temps nécessaire à chaque partie d’un programme utilisant de nombreuses ressources de calcul.
* Comparer des rapports de performances détaillés pour deux versions d’un service.
* Analyser l’allocation de mémoire plus en détail que le niveau des allocations de mémoire individuelles.
* Analyser les problèmes d’accès concurrentiel dans du code multithread.

L’utilisation du profileur vous permet de collecter des données pour un service cloud exécuté localement ou dans Azure.

### <a name="collect-profiling-data-locally-to"></a>Collectez des données de profilage localement pour effectuer les tâches suivantes :
* Tester les performances d’une partie d’un service cloud, telle que l’exécution d’un rôle de travail spécifique, qui ne nécessite pas de charge simulée réaliste.
* Tester les performances d’un service cloud de manière isolée, dans des conditions contrôlées.
* Tester les performances d’un service cloud avant son déploiement dans Azure.
* Tester les performances d’un service cloud en mode privé, sans perturber les déploiements existants.
* Tester les performances du service sans que des frais d’exécution d’Azure vous soient facturés.

### <a name="collect-profiling-data-in-azure-to"></a>Collectez des données de profilage dans Azure pour effectuer les tâches suivantes :
* Tester les performances d’un service cloud sous une charge simulée ou réelle.
* Utiliser la méthode d’instrumentation pour collecter des données de profilage, comme décrit ultérieurement dans cette rubrique.
* Tester les performances du service dans le même environnement que lors de son exécution en production.

Vous simulez généralement une charge pour tester des services cloud dans des conditions de contrainte ou normales.

## <a name="profiling-a-cloud-service-in-azure"></a>Profilage d’un service cloud dans Azure
Quand vous publiez votre service cloud à partir de Visual Studio, profilez le service et spécifiez les paramètres de profilage appropriés pour obtenir les informations dont vous avez besoin. Une session de profilage est démarrée pour chaque instance d’un rôle. Pour plus d’informations sur la publication de votre service à partir de Visual Studio, consultez [Publication d’un service cloud Azure depuis Visual Studio](vs-azure-tools-publishing-a-cloud-service.md).

Pour mieux comprendre le fonctionnement du profilage des performances dans Visual Studio, consultez le [Guide du débutant en profilage des performances](https://msdn.microsoft.com/library/azure/ms182372.aspx) et la rubrique [Analyse des performances de l’application à l’aide des outils de profilage](https://msdn.microsoft.com/library/azure/z9z62c29.aspx).

> [!NOTE]
> Quand vous publiez votre service cloud, activez IntelliTrace ou le profilage. Vous ne pouvez pas activer les deux méthodes.
>
>

### <a name="profiler-collection-methods"></a>Méthodes de collecte des données par le profileur
Vous avez le choix entre plusieurs méthodes de collecte pour le profilage, selon les problèmes de performances rencontrés :

* **Échantillonnage de l’UC** : cette méthode collecte des statistiques de l’application qui sont utiles pour l’analyse initiale des problèmes d’utilisation de l’UC. L’échantillonnage de l’UC est la méthode conseillée pour commencer la plupart des analyses de performances. La collecte des données d’échantillonnage de l’UC a peu d’impact sur l’application.
* **Instrumentation** : cette méthode collecte des données de temporisation détaillées qui sont utiles pour l’analyse ciblée et l’analyse des problèmes de performances des entrées/sorties. La méthode d’instrumentation enregistre chaque entrée, sortie et appel de fonction des fonctions d’un module pendant l’exécution d’un profilage. Cette méthode permet de collecter des informations de temporisation détaillées à propos d’une partie précise de votre code. Elle vous aide à comprendre l’impact des opérations d’entrée et de sortie sur les performances de l’application. Cette méthode est désactivée sur un ordinateur exécutant un système d’exploitation 32 bits. Cette option est disponible uniquement si vous exécutez le service cloud dans Azure, et pas localement dans l’émulateur de calcul.
* **Allocation de mémoire .NET** : cette méthode collecte des données d’allocation de mémoire .NET Framework à l’aide de la méthode de profilage par échantillonnage. Les données collectées incluent le nombre et la taille des objets alloués.
* **Accès concurrentiel** : cette méthode collecte des données sur la contention de ressources, ainsi que des données sur l’exécution des threads et processus qui sont utiles pour analyser les applications multithread et multiprocessus. La méthode d’accès concurrentiel collecte des données pour chaque événement qui bloque l’exécution de votre code, par exemple quand un thread attend la libération d’un verrou d’accès à une ressource d’application. Cette méthode est utile pour l’analyse des applications multithread.
* Vous pouvez également activer le **profilage d’interaction de couche**, qui fournit des informations supplémentaires sur les temps d’exécution des appels ADO.NET synchrones dans les fonctions des applications multicouches qui communiquent avec une ou plusieurs bases de données. Vous pouvez collecter des données d’interaction de couche à l’aide de n’importe quelle méthode de profilage. Pour plus d’informations sur le profilage d’interaction de couche, consultez [Vue Interactions de couche](https://msdn.microsoft.com/library/azure/dd557764.aspx).

## <a name="configuring-profiling-settings"></a>Configuration des paramètres de profilage
L’illustration suivante montre comment configurer vos paramètres de profilage à partir de la boîte de dialogue Publication d’application Azure.

![Configurer les paramètres de profilage](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> Pour cocher la case **Activer le profilage** , le profileur doit être installé sur l'ordinateur local que vous utilisez pour publier votre service cloud. Par défaut, le profileur s’installe lors de l’installation de Visual Studio.
>
>

### <a name="to-configure-profiling-settings"></a>Pour configurer les paramètres de profilage
1. Dans l’Explorateur de solutions, ouvrez le menu contextuel de votre projet Azure, puis choisissez **Publier**. Pour obtenir la procédure détaillée de la publication d’un service cloud, consultez [Publication d’un service cloud à l’aide des outils Azure](http://go.microsoft.com/fwlink/p?LinkId=623012).
2. Dans la boîte de dialogue **Publication d’application Azure**, choisissez l’onglet **Paramètres avancés**.
3. Pour activer le profilage, cochez la case **Activer le profilage** .
4. Pour configurer vos paramètres de profilage, choisissez le lien hypertexte **Paramètres** . La boîte de dialogue Paramètres de profilage s’affiche.
5. À l’aide des cases d’option **Quelle méthode de profilage voulez-vous utiliser ?** , choisissez le type de profilage approprié.
6. Pour collecter les données de profilage d’interaction de couche, cochez la case **Activer le profilage d’interaction de couche** .
7. Pour enregistrer les paramètres, choisissez le bouton **OK** .

    Quand vous publiez cette application, ces paramètres sont utilisés pour créer la session de profilage pour chaque rôle.

## <a name="viewing-profiling-reports"></a>Affichage des rapports de profilage
Une session de profilage est créée pour chaque instance de rôle dans votre service cloud. Pour afficher vos rapports de profilage de chaque session de Visual Studio, affichez la fenêtre Explorateur de serveurs, puis choisissez le nœud de calcul Azure pour sélectionner une instance d’un rôle. Affichez ensuite le rapport de profilage comme indiqué dans l’illustration suivante.

![Afficher un rapport de profilage à partir d’Azure](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Pour afficher des rapports de profilage
1. Pour afficher la fenêtre Explorateur de serveurs dans Visual Studio, dans la barre de menus, choisissez Affichage, Explorateur de serveurs.
2. Choisissez le nœud de calcul Azure, puis choisissez le nœud de déploiement Azure pour le service cloud pour lequel vous avez activé le profilage lors de la publication à partir de Visual Studio.
3. Pour afficher les rapports de profilage d'une instance, choisissez le rôle dans le service, ouvrez le menu contextuel d’une instance spécifique, puis choisissez **Afficher le rapport de profilage**.

    Le rapport, un fichier .vsp, est maintenant téléchargé à partir d’Azure, et l’état du téléchargement apparaît dans le journal des activités Azure. À la fin du téléchargement, le rapport de profilage s’affiche dans un onglet de l’éditeur pour Visual Studio nommé <nom_rôle\>*<numéro_instance\>*<identificateur\>.vsp. Une synthèse du rapport est présentée.
4. Pour afficher différentes vues du rapport, dans la liste Affichage actuel, choisissez le type de vue souhaité. Pour plus d’informations, consultez [Vues des rapports d’outils de profilage](https://msdn.microsoft.com/library/azure/bb385755.aspx).

## <a name="next-steps"></a>Étapes suivantes
[Débogage de Cloud Services](vs-azure-tools-debug-cloud-services-virtual-machines.md)

[Publication d’un service cloud Azure depuis Visual Studio](vs-azure-tools-publishing-a-cloud-service.md)
