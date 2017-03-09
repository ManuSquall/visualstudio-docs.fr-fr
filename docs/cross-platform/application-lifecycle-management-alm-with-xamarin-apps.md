---
title: "Gestion du cycle de vie des applications (ALM) avec des applications Xamarin | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "crdun"
manager: "crdun"
---
# Gestion du cycle de vie des applications (ALM) avec des applications Xamarin
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Xamarin vous permet de créer des applications mobiles interplateformes ciblant Android, iOS et Windows à l’aide de c#, .NET et Visual Studio. Xamarin permet une grande partie du code pour être partagé entre les plateformes, seule une petite portion devant être spécifique à la plateforme. Pour plus d’informations sur Xamarin, consultez [Visual Studio et Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Le développement d'applications pour des plateformes modernes implique de nombreuses activités qui vont bien au-delà de la simple écriture de code. Ces activités, appelées DevOps (développement + opérations), couvrent le cycle de vie complet de l’application et incluent la planification et suivi du travail, la conception et l’implémentation de code, la gestion d’un référentiel de code source, builds, gestion des intégrations continues et les déploiements de test en cours d’exécution (y compris les tests unitaires et des tests d’interface Utilisateur), différentes formes de diagnostics dans les environnements de développement et de production en cours d’exécution et la surveillance des comportements utilisateur et les performances d’application en temps réel via la télémétrie et analytique.  
  
 Visual Studio, Visual Studio Team Services et Team Foundation Server fournissent différentes capacités DevOps, également appelée Application Lifecycle Management ou ALM. Bon nombre d'entre elles sont entièrement applicables aux projets multiplateformes.  
  
 Cela est particulièrement vrai pour les applications Xamarin car ils sont générés avec c# et .NET, autour de quel ALM certains outils sont créés. Autres outils, nécessitent une intégration étroite avec les environnements de génération et d’exécution. Étant donné que les applications Xamarin s'exécutent sur des plateformes non-Windows et qu'elles utilisent l'implémentation Mono de .NET, Xamarin fournit des outils spécialisés pour répondre à certains besoins.  
  
 Le tableau ci-dessous répertorie les fonctionnalités de Visual Studio ALM vous pouvez vous attendre fonctionner avec un projet Xamarin et celles qui présentent des limites. Pour plus d'informations sur les fonctionnalités, cliquez sur les liens correspondants.  
  
## <a name="agile-tools"></a>Outils agiles  
 Lien de référence : **[travail](../Topic/Track%20work%20using%20VSTS%20or%20TFS.md)** (à l’aide de Visual Studio Team Services ou TFS, y compris Team Explorer Everywhere)  
  
 Commentaire général : toutes les fonctionnalités de suivi et de planification sont indépendants du type de projet et les langages de codage.  
  
|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|  
|-------------|----------------------------|-------------------------|  
|Gérer les backlogs et les sprints|Oui||  
|Suivi du travail|Oui||  
|Collaboration dans la salle d'équipe|Oui||  
|Tableaux kanban|Oui||  
|Créer des rapports sur la progression et la visualiser|Oui||  
  
## <a name="modeling"></a>Modélisation  
 Lien de référence : **[l’analyse et l’Architecture de modélisation](../modeling/analyze-and-model-your-architecture.md)**  
  
 Les fonctionnalités de conception sont indépendantes du langage de codage ou fonctionnent avec les langages .NET tels que C#. Consultez [Architecture de rôles et des diagrammes de modélisation dans le développement logiciel](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) pour découvrir les aspects liés au code.  
  
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
|[Utiliser Team Foundation Version Control](../Topic/Use%20Team%20Foundation%20Version%20Control.md) ou Visual Studio Team Services|Oui||  
|[Prise en main de Git dans Team Services](../Topic/Use%20Visual%20Studio%20with%20Git.md)|Oui||  
|[Code analysis/améliorer la qualité du code (références, modifications suggérées, etc.).](../test/improve-code-quality.md)|Oui||  
|[Rechercher les modifications de code et autres historiques](../ide/find-code-changes-and-other-history-with-codelens.md)|Oui|Sauf au-delà des limites spécifiques à la plate-forme où l'implémentation n'est résolue qu'au moment de l'exécution.|  
|[Utilisez des cartes de code à déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)|Oui||  
  
## <a name="build"></a>Build  
 Lien de référence : **[Générer](../Topic/Build%20the%20application.md)**  
  
|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|  
|-------------|----------------------------|-------------------------|  
|Serveur TFS local|Oui|Ordinateurs de build Xamarin doivent être installé et peuvent être liés à un ordinateur OSX pour générer pour iOS. Consultez [Configuration de TFS pour Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (site web Xamarin).|  
|Serveur de builds local lié à Visual Studio Team Services|Oui|Consultez [serveur de builds](../Topic/Deploy%20and%20configure%20a%20build%20server.md) pour obtenir des instructions.|  
|Service de contrôleur hébergé de Visual Studio Team Services|Oui|Consultez [générer votre application Xamarin](https://www.visualstudio.com/en-us/docs/build/apps/mobile/xamarin).|  
|Définitions de builds avec des pré-scripts et des post-scripts|Oui||  
|Intégration continue, y compris les archivages contrôlés|Oui|Archivages contrôlés pour TFVC uniquement si Git utilise un modèle de requête d'extraction plutôt que des archivages.|  
  
## <a name="testing"></a>Test  
 Lien de référence : **[test de l’application](/devops-test-docs/test/test-apps-early-and-often)**  
  
|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|  
|-------------|----------------------------|-------------------------|  
|Planification de tests, création de cas de test et organisation de suites de tests|Oui||  
|Test manuel|Oui||  
|Gestionnaire de tests (enregistrer et rejouer des tests)|Oui|Les appareils Windows et les émulateurs Android uniquement à partir de Visual Studio. Enregistrement de tous les périphériques est possible avec [Xamarin l’enregistreur de Test](https://www.xamarin.com/test-cloud/recorder).|  
|Couverture du code|N/A||  
|[Test unitaire de votre Code.](../test/unit-test-your-code.md)|Oui|Pour des cibles Windows et Android, vous pouvez utiliser les outils MSTest intégrés. Pour exécuter des tests unitaires sur Windows, Android et iOS, Xamarin recommande NUnit. Consultez [Configuration de TFS pour Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (site web Xamarin).|  
|[Utilisation d’UI Automation pour tester votre Code](../test/use-ui-automation-to-test-your-code.md)|Windows uniquement|Enregistreur de test de l’interface Utilisateur de Visual Studio est Windows uniquement. Pour toutes les plateformes, consultez [Xamarin l’enregistreur de Test](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Améliorer la qualité du code  
 Lien de référence : **[améliorer la qualité du Code](../test/improve-code-quality.md)**  
  
|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|  
|-------------|----------------------------|-------------------------|  
|[Analyse de la qualité du Code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Oui||  
|[Recherche du Code dupliqué à l’aide de Code Clone Detection](../Topic/Finding%20Duplicate%20Code%20by%20using%20Code%20Clone%20Detection.md)|Oui||  
|[Mesure de la complexité et la facilité de maintenance du Code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Oui||  
|[Explorateur de performances](../profiling/performance-explorer.md)|Non|Utilisez le [Profileur Xamarin](http://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/) par le biais de Xamarin Studio à la place. Notez que Xamarin Profiler est actuellement disponible en version préliminaire et qu'il ne fonctionne pas pour le moment avec les cibles Windows.|  
|[Analyser les problèmes de mémoire .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|Non|Visual Studio Tools ne possède pas de hook à l'infrastructure Mono pour le profilage.|  
  
## <a name="release-management"></a>Gestion des versions  
 Lien de référence : **[automatiser les déploiements avec Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|  
|-------------|----------------------------|-------------------------|  
|Gérer les processus de publication des versions|Oui||  
|Déploiement sur des serveurs pour le chargement de version test via des scripts|Oui||  
|Télécharger vers le magasin d'applications|Partial|Les extensions sont disponibles qui peuvent automatiser ce processus pour certains magasins d’applications.  Consultez [Extensions pour Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS); par exemple, le [extension pour Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Moniteur avec HockeyApp  
 Lien de référence : **[analyse avec HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Fonctionnalité|Prise en charge par Xamarin|Commentaires supplémentaires|  
|-------------|----------------------------|-------------------------|  
|Bloquer la distribution bêta analytique et télémétrie|Oui||