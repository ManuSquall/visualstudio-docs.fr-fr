---
title: Profilage des performances des applications SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2037842e57b6152990144d9ea652936e65517e13
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90739952"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>Profiler les performances des applications SharePoint

Si vos applications SharePoint s’exécutent lentement ou de manière inefficace, vous pouvez utiliser les fonctionnalités de profilage dans Visual Studio pour identifier le code problématique et d’autres éléments. À l’aide de la fonctionnalité de test de charge, vous pouvez déterminer comment une application SharePoint s’exécute en cas de stress, par exemple quand de nombreux utilisateurs accèdent simultanément à l’application. En exécutant des tests de performances de site Web, vous pouvez mesurer la manière dont l’application s’exécute sur le Web. À l’aide de tests codés de l’interface utilisateur, vous pouvez vérifier si l’ensemble de l’application SharePoint, y compris son interface utilisateur, fonctionne correctement. Lorsque vous utilisez ces tests ensemble, ils peuvent vous aider à identifier les problèmes de performances avant de déployer votre application.

## <a name="profile-tools-overview"></a>Vue d’ensemble des outils de profil

Le profilage fait référence au processus d’observation et d’enregistrement du comportement de performances de votre application lors de son exécution. En profilant votre application, vous pouvez découvrir des problèmes tels que des goulots d’étranglement, du code inefficace et des problèmes d’allocation de mémoire, ce qui entraîne un ralentissement de l’exécution des applications ou une utilisation trop importante de la mémoire. Par exemple, vous pouvez utiliser le profilage pour identifier les zones réactives dans votre code, qui sont des segments de code fréquemment appelés et qui peuvent ralentir les performances globales de votre application. Une fois que vous avez identifié les zones réactives, vous pouvez souvent les optimiser ou les éliminer.

Vous pouvez utiliser plusieurs outils de profilage dans l’environnement de développement intégré (IDE) pour identifier et localiser ces types de problèmes de performances. Ces outils fonctionnent de la même façon pour les projets SharePoint que pour d’autres types de projets Visual Studio. L’Assistant Outils de profilage performance vous guide tout au long de la création d’une session de performance qui utilise les tests que vous spécifiez. Une session de performance est un ensemble de données de configuration qui est utilisé pour collecter des informations sur les performances d’une application, ainsi que les résultats d’une ou de plusieurs exécutions de profilage. Les sessions de performance sont stockées dans le dossier de votre projet et vous pouvez les afficher dans **Explorateur de performances**. Pour plus d’informations, consultez [Understanding Performance Collection Methods](../profiling/understanding-performance-collection-methods.md) (Fonctionnement des méthodes de collecte des données de performances).

Une fois que vous avez créé et exécuté une analyse de profil sur votre application, un rapport fournit des détails sur ses performances. Ce rapport peut inclure des éléments tels qu’un graphique de l’utilisation de l’UC dans le temps, une pile d’appels de fonction hiérarchique ou une arborescence des appels. Le contenu exact du rapport peut varier en fonction du type de test que vous exécutez, par exemple l’échantillonnage ou l’instrumentation. Pour plus d’informations, consultez [outils de profilage vue d’ensemble des rapports](../profiling/performance-report-overview.md).

## <a name="performance-session-process"></a>Processus de session de performance

Pour profiler une application, vous devez commencer par utiliser l’Assistant Outils de profilage performance pour créer une session de performance. Dans la barre de menus, choisissez **analyser**, **lancer l’Assistant Performance**. À l’issue de l’Assistant, vous entrez les informations requises pour votre session de performance, telles que la méthode de profil que vous souhaitez et l’application que vous souhaitez profiler. Pour plus d’informations, consultez [Comment : profiler un site Web ou une application Web à l’aide de l’Assistant Performance](../profiling/how-to-collect-performance-data-for-a-web-site.md). Vous pouvez également utiliser les options de ligne de commande pour configurer et exécuter une session de performance. Pour plus d’informations, consultez [utilisation de l’outils de profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md). Si vous souhaitez configurer manuellement chaque aspect d’une session de performance, consultez [procédure : créer manuellement des sessions de performance avec le outils de profilage](../profiling/how-to-manually-create-performance-sessions.md). Vous pouvez également créer une session de performance à partir d’un test unitaire en utilisant, dans la fenêtre **résultats des tests** , en ouvrant le menu contextuel du test unitaire, puis en choisissant **créer une session de performance**.

Une fois que vous avez configuré une session de performance, la configuration de session est enregistrée, le serveur est configuré pour fournir les données de profilage et l’application s’exécute. Lorsque vous utilisez l’application, les données de performances sont écrites dans un fichier journal. Les sessions de performance sont répertoriées dans **Explorateur de performances** sous le dossier **cibles** . Après la fin d’une session de performance, son rapport s’affiche dans le dossier **rapports** de **Explorateur de performances**. Pour afficher le rapport, ouvrez-le dans **Explorateur de performances**. Pour afficher ou configurer les propriétés d’une session de performance, ouvrez le menu contextuel dans **Explorateur de performances**, puis choisissez **Propriétés**. Pour plus d’informations sur les propriétés spécifiques d’une session de performance, consultez [Configuration des sessions de performance pour outils de profilage](../profiling/configuring-performance-sessions.md). Pour plus d’informations sur la façon d’interpréter les résultats d’une session de performance, consultez [analyse des données de outils de profilage](../profiling/analyzing-performance-tools-data.md).

## <a name="stress-test"></a>Test de stress

Vous pouvez analyser les performances de stress de vos applications en créant des tests de charge et des tests de performances de site Web dans Visual Studio. Lorsque vous créez un test de charge dans Visual Studio, vous spécifiez une combinaison de facteurs, appelée scénario, pour tester votre application. Ces facteurs incluent le modèle de charge, le modèle de combinaison de tests, la combinaison de tests, la combinaison de réseaux et la combinaison de navigateurs Web. Les scénarios de test de charge peuvent inclure des tests unitaires et des tests de performances de site Web.

Figure 1 : exemple de résultats de test de charge

![Exécution de la vue des graphiques du test de charge](../sharepoint/media/load-webgraphs.png "Exécution de la vue des graphiques du test de charge")

Les tests de performances de site Web simulent la manière dont un utilisateur final peut interagir avec une application SharePoint. Vous pouvez créer des tests de performances de site Web en enregistrant des requêtes HTTP dans une session de navigateur ou à l’aide de l' **enregistreur de test de performances de site Web**. Les requêtes Web s’affichent dans la **éditeur de test de performances Web** une fois la session de navigateur terminée. Vous pouvez ensuite déboguer les résultats dans la **visionneuse de résultats des tests performances de site Web**. Vous pouvez également générer manuellement des tests de performances de site Web à l’aide de l' **éditeur de test de performances Web**.

## <a name="test-user-interfaces"></a>Interfaces utilisateur de test

Les tests codés de l’interface utilisateur pilotent automatiquement votre application SharePoint via son interface utilisateur (IU). Ces tests couvrent les contrôles d’interface utilisateur, tels que les boutons et les menus, pour vérifier qu’ils fonctionnent correctement. Ce type de test est particulièrement utile si la validation ou une autre logique est effectuée dans l’interface utilisateur, par exemple dans une page Web. Vous pouvez également utiliser des tests codés de l’interface utilisateur pour automatiser les tests manuels. Vous créez des tests codés de l’interface utilisateur pour vos applications SharePoint de la même façon que vous créez des tests pour d’autres types d’applications. Pour plus d’informations, consultez [test des applications SharePoint 2010 avec des tests codés de l’interface utilisateur](../vs-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests.md?view=vs-2015).

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Procédure pas à pas : profilage d’une application SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Montre comment effectuer une analyse de profil d’échantillonnage sur une application SharePoint.|
|[Tester les performances de votre application avant publication](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts)|Décrit comment créer des tests de charge, qui vous aident à effectuer des tests de contrainte sur les applications SharePoint.|
|[Tests unitaires sur votre code](../test/unit-test-your-code.md)|Décrit comment rechercher des erreurs de logique dans votre code à l’aide de tests unitaires.|
|[Test des applications SharePoint 2010 avec des tests codés de l’interface utilisateur](../vs-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests.md?view=vs-2015)|Décrit comment tester l’interface utilisateur de vos applications SharePoint.|

## <a name="see-also"></a>Voir aussi

- [Générer et déboguer des solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Améliorer la qualité du code](../test/improve-code-quality.md)