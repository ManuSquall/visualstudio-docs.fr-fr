---
title: Application Lifecycle Management (ALM) avec les applications Xamarin | Microsoft Docs
ms.date: 08/21/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- xamarin
ms.openlocfilehash: e4dea73bc3d3c1e7db77544b24be1525fca0a202
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282352"
---
# <a name="devops-with-xamarin-apps"></a>DevOps avec les applications Xamarin

Xamarin vous permet de générer des applications mobiles multiplateformes ciblant Android, iOS et Windows à l’aide de C#, .NET et Visual Studio. Xamarin autorise le partage d’une grande partie du code entre les plateformes. Seul un petit pourcentage du code doit être spécifique à chaque plateforme. Pour plus d’informations sur Xamarin, consultez [Visual Studio et Xamarin](../cross-platform/visual-studio-and-xamarin.md).

Le développement d'applications pour des plateformes modernes implique de nombreuses activités qui vont bien au-delà de la simple écriture de code. Ces activités, appelées DevOps (développement + opérations), couvrent le cycle de vie complet de l’application et incluent la planification et le suivi du travail, la conception et l’implémentation du code, la gestion d’un dépôt de code source, l’exécution des builds, la gestion des intégrations continues et des déploiements continus, les tests (notamment les tests unitaires et les tests d’IU), l’exécution de différentes formes de diagnostic dans les environnements de développement et de production, ainsi que la surveillance en temps réel des performances des applications et des comportements des utilisateurs via la télémétrie et l’analyse.

Visual Studio, en combinaison avec Azure DevOps Services et Team Foundation Server, offre différentes fonctionnalités DevOps. Bon nombre d'entre elles sont entièrement applicables aux projets multiplateformes. Cela est particulièrement vrai en ce qui concerne les applications Xamarin, car elles font appel à du code C# et .NET, sur lequel certains outils DevOps sont basés. D'autres outils nécessitent une intégration étroite avec les environnements de génération et d'exécution. Étant donné que les applications Xamarin s'exécutent sur des plateformes non-Windows et qu'elles utilisent l'implémentation Mono de .NET, Xamarin fournit des outils spécialisés pour répondre à certains besoins.

Les tableaux suivants identifient les fonctionnalités DevOps de Visual Studio qui donnent de bons résultats avec un projet Xamarin, et celles qui présentent des limites. Pour plus d'informations sur les fonctionnalités, cliquez sur les liens correspondants.

## <a name="agile-tools"></a>Outils agiles

Lien de référence : **[À propos des outils agiles et de la gestion de projet agile](/azure/devops/boards/backlogs/overview?view=vsts)**

Commentaire général : toutes les fonctionnalités de planification et de suivi sont indépendantes du type de projet et des langages de codage.

|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|
|-------------|----------------------------|-------------------------|
|Gérer les backlogs et les sprints|Oui||
|Suivi du travail|Oui||
|Collaboration dans la salle d'équipe|Oui||
|Tableaux kanban|Oui||
|Créer des rapports sur la progression et la visualiser|Oui||

## <a name="modeling"></a>Modélisation

Lien de référence : **[Analyser et modéliser l’architecture](../modeling/analyze-and-model-your-architecture.md)**

Les fonctionnalités de conception sont indépendantes du langage de codage ou fonctionnent avec les langages .NET tels que C#. Voir [Rôles de l’architecture et des diagrammes de structure dans le développement logiciel](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) pour connaître les aspects liés au code.

|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|
|-------------|----------------------------|-------------------------|
|Diagrammes de séquence|Oui||
|Graphiques de dépendance|Oui||
|Hiérarchie d'appels|Oui||
|Concepteur de classes|Oui||
|Navigateur de l'architecture|Oui||
|Diagrammes UML (cas d'usage, activité, classe, composant, séquence et DSL)|Oui||
|Diagrammes de couche|Oui||
|Validation de couche|Oui||

## <a name="code"></a>Code

|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|
|-------------|----------------------------|-------------------------|
|[Utiliser Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts) ou Azure Repos|Oui||
|[Bien démarrer avec Git dans Azure Repos](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio)|Oui||
|[Améliorer la qualité du code](../test/improve-code-quality.md)|Oui||
|[Rechercher les modifications de code et d’autres historiques](../ide/find-code-changes-and-other-history-with-codelens.md)|Oui|Sauf au-delà des limites spécifiques de la plateforme où l’implémentation n’est résolue qu’au moment de l’exécution.|
|[Utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)|Oui||

## <a name="build"></a>Générer

Lien de référence :  **[Azure Pipelines](/azure/devops/pipelines/index?view=vsts)**

|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|
|-------------|----------------------------|-------------------------|
|Serveur TFS local|Oui|Xamarin doit être installé sur les machines de build. Celles-ci peuvent être liées à un ordinateur OSX afin de générer des applications pour iOS. Consultez [Utiliser TFVC](/azure/devops/repos/tfvc/overview?view=vsts)|
|Serveur de builds local lié à Azure Pipelines|Oui|Pour obtenir des instructions, consultez [Agents de build et de mise en production](/azure/devops/pipelines/agents/agents?view=vsts).|
|Service de contrôleur hébergé d’Azure Pipelines|Oui|Consultez [Générez votre application Xamarin](/azure/devops/pipelines/languages/xamarin?view=vsts&tabs=vsts).|
|Définitions de builds avec des pré-scripts et des post-scripts|Oui||
|Intégration continue, y compris les archivages contrôlés|Oui|Archivages contrôlés pour TFVC uniquement si Git utilise un modèle de requête d'extraction plutôt que des archivages.|

## <a name="test"></a>Tester

|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|
|-------------|----------------------------|-------------------------|
|Planification de tests, création de cas de test et organisation de suites de tests|Oui||
|Test manuel|Oui||
|Gestionnaire de tests (enregistrer et rejouer des tests)|Oui|Appareils Windows et émulateurs Android uniquement à partir de Visual Studio. L’enregistrement est possible pour tous les appareils avec [Xamarin Test Recorder](/appcenter/test-cloud/uitest/).|
|Couverture du code|N/A||
|[Tests unitaires sur votre code](../test/unit-test-your-code.md)|Oui|Pour des cibles Windows et Android, vous pouvez utiliser les outils MSTest intégrés. Pour exécuter des tests unitaires sur Windows, Android et iOS, Xamarin recommande NUnit. Consultez [Utiliser TFVC](/azure/devops/repos/tfvc/overview?view=vsts).|
|[Utiliser l’automatisation de l’interface utilisateur pour tester votre code](../test/use-ui-automation-to-test-your-code.md)|Windows uniquement|L’enregistreur de test d’IU de Visual Studio est réservé à Windows. Pour toutes les plateformes, consultez [Xamarin.UITest](/appcenter/test-cloud/uitest/).|

## <a name="improve-code-quality"></a>Améliorer la qualité du code

Lien de référence : **[Améliorer la qualité du code](../test/improve-code-quality.md)**

|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|
|-------------|----------------------------|-------------------------|
|[Analyser la qualité du code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Oui||
|[Rechercher du code dupliqué à l’aide de la détection de clone de code](https://msdn.microsoft.com/library/hh205279.aspx)|Oui||
|[Mesurer la complexité et la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Oui||
|[Explorateur de performances](../profiling/performance-explorer.md)|Non|Utilisez le [Profileur Xamarin](/xamarin/cross-platform/deploy-test/) par le biais de Xamarin Studio à la place. Notez que Xamarin Profiler est actuellement disponible en version préliminaire et qu'il ne fonctionne pas pour le moment avec les cibles Windows.|
|[Analyser les problèmes de mémoire liés au .NET Framework](https://msdn.microsoft.com/library/dn342825.aspx)|Non|Visual Studio Tools n’a pas de hook au framework Mono pour le profilage.|

## <a name="release-management"></a>Gestion des versions

Lien de référence : **[Générer et mettre en production dans Azure Pipelines et TFS](/azure/devops/pipelines/overview?view=vsts)**

|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|
|-------------|----------------------------|-------------------------|
|Gérer les processus de publication des versions|Oui||
|Déploiement sur des serveurs pour le chargement de version test via des scripts|Oui||
|Télécharger vers le magasin d'applications|Partial|Il existe des extensions qui peuvent automatiser ce processus pour certains magasins d’applications.  Consultez [Extensions pour Azure DevOps Services](https://marketplace.visualstudio.com/VSTS), par exemple [l’extension pour Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Analyser avec HockeyApp

Lien de référence : **[Analyser avec HockeyApp](https://www.hockeyapp.net/features/)**

|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|
|-------------|----------------------------|-------------------------|
|Analyse des incidents, télémétrie et distribution des bêta|Oui||
