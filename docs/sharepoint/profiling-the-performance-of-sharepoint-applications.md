---
title: Profilage des performances des Applications SharePoint | Documents Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: 61ae02e7-3f37-4230-bae1-54a498c2fae8
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 58e2d02b32a17cf23e95639077c26b6b41dae00f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-the-performance-of-sharepoint-applications"></a>Profilage des performances des applications SharePoint
  Si vous exécutez vos applications SharePoint à variation lente ou inefficace, vous pouvez utiliser les fonctionnalités de profilage dans Visual Studio pour identifier tout code problématique et autres éléments. À l’aide de la fonctionnalité de test de charge, vous pouvez déterminer la façon dont une application SharePoint effectue sous une charge importante, par exemple lorsque de nombreux utilisateurs accèdent à l’application simultanément. En exécutant des tests de performances web, vous pouvez mesurer la façon dont l’application s’exécute sur le web. À l’aide de tests codés de l’interface utilisateur, vous pouvez vérifier si l’application SharePoint, y compris son interface utilisateur, fonctionne correctement. Lorsque vous utilisez ces tests ensemble, ils peuvent vous aider à identifier les problèmes de performances avant de déployer votre application.  
  
## <a name="profiling-tools-overview"></a>Vue d'ensemble des outils de profilage  
 Profilage fait référence au processus d’observation et en enregistrant le comportement des performances de votre application en cours d’exécution. Par le profilage de votre application, vous pouvez découvrir des problèmes tels que les goulots d’étranglement, code inefficace et problèmes d’allocation de mémoire, ce qui les applications s’exécutent lentement ou utiliser trop de mémoire. Par exemple, vous pouvez utiliser le profilage pour identifier des zones réactives dans votre code, qui sont des segments de code qui sont souvent appelées et peuvent ralentir les performances globales de votre application vers le bas. Après avoir identifié les zones réactives, vous pouvez souvent optimiser ou de les éliminer.  
  
 Vous pouvez utiliser plusieurs outils de profilage dans l’environnement de développement intégré (IDE) pour identifier et localiser ces types de problèmes de performances. Ces outils fonctionnent de la même façon pour les projets SharePoint comme d’autres types de projets Visual Studio. L’Assistant Performance des outils de profilage vous guide tout au long de la création d’une session de performance qui utilise les tests que vous spécifiez. Une session de performance est un ensemble de données de configuration qui sont utilisées pour la collecte des informations sur les performances à partir d’une application, ainsi que les résultats d’une ou plusieurs exécutions de profilage. Sessions de performance sont stockées dans votre dossier de projet, et vous pouvez les afficher dans **Explorateur de performances**. Pour plus d’informations, consultez [Understanding Performance Collection Methods](/visualstudio/profiling/understanding-performance-collection-methods) (Fonctionnement des méthodes de collecte des données de performances).  
  
 Une fois que vous créez et exécutez une analyse de profil sur votre application, un rapport fournit des détails sur les performances. Ce rapport peut inclure un graphique d’utilisation du processeur dans le temps, une pile d’appels de fonction hiérarchique ou une arborescence des appels. Le contenu exact du rapport peut varier, selon le type de test que vous exécutez, telles que l’échantillonnage ou instrumentation. Pour plus d’informations, consultez [vue d’ensemble de rapports pour les outils de profilage](http://go.microsoft.com/fwlink/?LinkId=224689).  
  
## <a name="performance-session-process"></a>Processus de session de performance  
 Pour profiler une application, vous démarrez à l’aide de l’Assistant Performance des outils de profilage pour créer une session de performance. Dans la barre de menus, choisissez **analyser**, **lancer l’Assistant Performance**. Que vous terminez l’Assistant, vous entrez les informations requises pour votre session de performance, telles que la méthode de profil et de l’application que vous souhaitez profiler. Pour plus d’informations, consultez [Comment : profiler un Site Web ou une Application de Web à l’aide de l’Assistant Performance](http://go.microsoft.com/fwlink/?LinkId=224692). En guise d’alternative, vous pouvez utiliser les options de ligne de commande pour configurer et exécuter une session de performance. Pour plus d’informations, consultez [à l’aide du profilage outils à partir de la de ligne de commande](http://go.microsoft.com/fwlink/?LinkId=224703). Si vous souhaitez configurer tous les aspects d’une session de performance manuellement, consultez [Comment : créer manuellement des Sessions performances avec les outils de profilage](http://go.microsoft.com/fwlink/?LinkId=224691). Vous pouvez également créer une session de performance à partir d’un test unitaire, dans le **des résultats des tests** fenêtre, ouvrez le menu contextuel pour le test unitaire, puis en choisissant **créer une Session de Performance**.  
  
 Après avoir configuré une session de performance, la configuration de session est enregistrée, le serveur est configuré pour fournir des données de profilage, et l’application s’exécute. Lorsque vous utilisez l’application, les données de performances sont écrites dans un fichier journal. Sessions de performance sont répertoriées dans **Explorateur de performances** sous le **cibles** dossier. Après une session de performance, son état s’affiche dans le **rapports** dossier **Explorateur de performances**. Pour afficher le rapport, ouvrez-le dans **Explorateur de performances**. Pour afficher ou configurer les propriétés d’une session de performance, ouvrez le menu contextuel dans **Explorateur de performances**, puis choisissez **propriétés**. Pour plus d’informations sur les propriétés spécifiques d’une session de performance, consultez [configuration des Sessions de Performance pour les outils de profilage](http://go.microsoft.com/fwlink/?LinkId=224694). Pour plus d’informations sur la façon d’interpréter les résultats d’une session de performance, consultez [analyse des données de profilage outils](http://go.microsoft.com/fwlink/?LinkId=224704).  
  
## <a name="stress-testing"></a>Test de contrainte  
 Vous pouvez analyser les performances de la contrainte de vos applications en créant des tests de charge et tests de performances web dans Visual Studio Ultimate. Lorsque vous créez un test de charge dans Visual Studio, vous spécifiez une combinaison de facteurs, appelée un scénario, pour tester votre application sur. Ces facteurs incluent le modèle de charge, modèle de combinaison de tests, la combinaison de tests, la combinaison de réseaux et la combinaison de navigateurs web. Scénarios de test de charge peuvent inclure des tests unitaires et tests de performances web.  
  
 Figure 1 : Exemple de résultats de test de charge  
  
 ![Vue graphiques de test de charge en cours d’exécution](../sharepoint/media/load-webgraphs.png "vue graphiques de test de charge en cours d’exécution")  
  
 Tests de performances Web simulent la manière dont un utilisateur final peut interagir avec une application SharePoint. Vous pouvez créer des tests de performances web en enregistrant des requêtes HTTP dans une session de navigateur ou à l’aide de la **enregistreur de Test de performances Web**. Les requêtes web apparaissent dans le **éditeur de Test de performances de site Web** après la fin de la session de navigateur. Vous pouvez alors déboguer les résultats dans le **Afficheur de résultats de Test de performances Web**. Vous pouvez générer manuellement des tests de performances de site web à l’aide de la **éditeur de Test de performances de site Web**.  
  
## <a name="testing-user-interfaces"></a>Test des interfaces utilisateur  
 Les tests codés de l’interface utilisateur de votre application SharePoint lecteur automatiquement via son interface utilisateur (IU). Ces tests couvrent les contrôles d’interface utilisateur, tels que des boutons et des menus, pour vérifier qu’ils fonctionnent correctement. Ce type de test est particulièrement utile si la validation ou autre logique est effectuée dans l’interface utilisateur, comme dans une page web. Vous pouvez également utiliser des tests codés d’IU pour automatiser les tests manuels. Vous créez tests codés de l’interface utilisateur pour vos applications SharePoint de la même façon que vous créez des tests pour d’autres types d’applications. Pour plus d’informations, consultez [test d’Applications SharePoint 2010 avec des Tests codés de l’interface utilisateur](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests).  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Procédure pas à pas : profilage d’une application SharePoint](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|Montre comment effectuer une analyse de profil d’échantillonnage sur une application SharePoint.|  
|[Tester les performances de votre application avant publication](https://www.visualstudio.com/docs/test/performance-testing/run-performance-tests-app-before-release)|Décrit comment créer des tests de charge, ce qui vous aident à un test de stress les applications SharePoint.|  
|[Tests unitaires sur votre code](/visualstudio/test/unit-test-your-code)|Explique comment rechercher des erreurs de logique dans votre code à l’aide de tests unitaires.|  
|[Test des applications SharePoint 2010 avec des tests codés de l’interface utilisateur](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests)|Décrit comment tester l’interface utilisateur de vos applications SharePoint.|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération et débogage de solutions SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Test de l’application](/devops-test-docs/test/test-apps-early-and-often)   
 [Améliorer la qualité du code](/visualstudio/test/improve-code-quality)  
  
  