---
title: "Application Lifecycle Management (ALM) avec les applications Unity | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "crdun"
manager: "crdun"
---
# Application Lifecycle Management (ALM) avec les applications Unity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le développement d'applications pour des plateformes modernes implique de nombreuses activités qui vont bien au-delà de la simple écriture de code. Ces activités, appelées DevOps (développement + opérations), couvrent le cycle de vie complet de l’application et incluent la planification et le suivi du travail, la conception et l’implémentation du code, la gestion d’un référentiel de code source, l’exécution des builds, la gestion des intégrations continues et des déploiements en continu, les tests (y compris les tests unitaires et les tests d’interface utilisateur), différentes formes de diagnostics dans les environnements de développement et de production, ainsi que la surveillance en temps réel des performances des applications et des comportements des utilisateurs via la télémétrie et l’analyse.  
  
 Visual Studio, Visual Studio Team Services et Team Foundation Server fournissent différentes capacités DevOps, également appelée Application Lifecycle Management ou ALM. Bon nombre d'entre elles sont appliquent aux projets inter-plateformes, y compris les jeux et les applications graphiques immersives créées avec Unity, surtout lorsque vous utilisez c# comme langage de script. Toutefois, comme Unity possède son propre environnement de développement et son propre moteur d'exécution, plusieurs fonctionnalités ALM ne s'appliquent pas comme elles le feraient pour d'autres types de projets créés dans Visual Studio.  
  
 Le tableau ci-dessous identifie comment les fonctionnalités ALM de Visual Studio s’appliquent ou ne s’appliquent pas lorsque vous travaillez avec Unity. Pour plus d'informations sur les fonctionnalités, cliquez sur les liens correspondants.  
  
## <a name="agile-tools"></a>Outils agiles  
 Lien de référence : **[travail](../Topic/Track%20work%20using%20VSTS%20or%20TFS.md)** (à l’aide de Visual Studio Team Services ou TFS, y compris Team Explorer Everywhere)  
  
 Commentaire général : toutes les fonctionnalités de suivi et de planification sont indépendants du type de projet et les langages de codage.  
  
|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|  
|-------------|--------------------------|-------------------------|  
|Gérer les backlogs et les sprints|Oui||  
|Suivi du travail|Oui||  
|Collaboration dans la salle d'équipe|Oui||  
|Tableaux kanban|Oui||  
|Créer des rapports sur la progression et la visualiser|Oui||  
  
## <a name="modeling"></a>Modélisation  
 Lien de référence : **[l’analyse et l’Architecture de modélisation](../modeling/analyze-and-model-your-architecture.md)**  
  
 Commentaire général : Bien que ces fonctionnalités de conception sont indépendantes du langage de codage ou fonctionnent avec les langages .NET tels que c#, elles fonctionnent sur un modèle d’application traditionnel avec des hiérarchies d’objets et relations de classe. La conception d'un jeu dans Unity implique un modèle entièrement différent, à savoir des relations d'objets graphiques, de sons, de nuanceurs, de scripts, etc. Pour cette raison, les outils de diagramme de modélisation Visual Studio ne sont pas particulièrement pertinents pour l'ensemble d'un projet Unity. Ils peuvent être utilisés pour gérer les relations au sein des scripts C#, mais ce n'est qu'une partie de l'ensemble.  
  
|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|  
|-------------|--------------------------|-------------------------|  
|Diagrammes de séquence|Non||  
|Graphiques de dépendance|Non||  
|Hiérarchie d'appels|Non||  
|Concepteur de classes|Non||  
|Navigateur de l'architecture|Non||  
|Diagrammes UML (cas d'usage, activité, classe, composant, séquence et DSL)|Non||  
|Diagrammes de couche|Non||  
|Validation de couche|Non||  
  
## <a name="code"></a>Code  
  
|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|  
|-------------|--------------------------|-------------------------|  
|[Utiliser Team Foundation Version Control](../Topic/Use%20Team%20Foundation%20Version%20Control.md) ou Visual Studio Team Services|Oui|Projets Unity sont simplement un ensemble de fichiers qui peuvent être placés dans des systèmes de contrôle de version comme n’importe quel autre projet, mais il existe quelques considérations spéciales décrites après ce tableau.|  
|[Prise en main de Git dans Team Services](../Topic/Use%20Visual%20Studio%20with%20Git.md)|Oui|Consultez les notes de la table.|  
|[Code analysis/améliorer la qualité du code (références, modifications suggérées, etc.).](../test/improve-code-quality.md)|Oui||  
|[Rechercher les modifications de code et autres historiques](../ide/find-code-changes-and-other-history-with-codelens.md)|Oui||  
|[Utilisez des cartes de code à déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)|Oui||  
  
 Considérations spéciales pour le contrôle de version avec Unity :  
  
1.  Unity assure le suivi des métadonnées relatives aux ressources de jeu dans une bibliothèque opaque unique qui est masquée par défaut. Pour maintenir la synchronisation des fichiers et des métadonnées, il est nécessaire de rendre visibles les métadonnées et de les stocker dans des segments plus gérables. Pour plus d’informations, reportez-vous à [à l’aide des systèmes de contrôle de Version externe avec Unity](http://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (documentation Unity).  
  
2.  Tous les fichiers et dossiers figurant dans un projet Unity ne sont pas appropriés pour le contrôle de code source, comme cela est également décrit dans le lien ci-dessus. Les dossiers Assets et ProjectSettings doivent être ajoutés, contrairement aux dossiers Library et Temp. Pour obtenir une liste supplémentaire de fichiers générés qui ne passent pas dans le contrôle de code source, consultez la discussion [comment utiliser Git pour le contrôle de code source Unity3D ?](http://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) sur StackOverflow. De leur côté, de nombreux développeurs ont également blogué sur ce sujet.  
  
3.  Les ressources binaires d'un projet Unity, telles que les textures et les fichiers audio, peuvent occuper une grande quantité de stockage. Des systèmes de contrôle de code source tels que Git stockent une copie unique d'un fichier pour chaque modification effectuée, même si la modification affecte uniquement une petite partie du fichier. Cette opération peut provoquer la saturation du référentiel Git. Pour résoudre ce problème, les développeurs Unity choisissent souvent de n'ajouter que les ressources finales à leur référentiel et d'utiliser un autre moyen de conserver un historique de l'utilisation de leurs ressources, telles que OneDrive, DropBox ou git-annex. Cette approche fonctionne, car il n'est généralement pas nécessaire de gérer les versions de telles ressources avec les modifications du code source. Généralement, les développeurs définissent aussi le mode de sérialisation de ressources de l'éditeur du projet sur Forcer le texte pour stocker les fichiers de séquence dans du texte plutôt que dans un format binaire, ce qui permet des fusions dans le contrôle de code source. Pour plus d’informations, consultez [paramètres de l’éditeur](http://docs.unity3d.com/Manual/class-EditorManager.html) (documentation Unity).  
  
## <a name="build"></a>Build  
 Lien de référence : **[Générer](../Topic/Build%20the%20application.md)**  
  
|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|  
|-------------|--------------------------|-------------------------|  
|Serveur TFS local|Possible|Les projets Unity sont créés via l'environnement Unity et non via le système de génération de Visual Studio (la génération dans Visual Studio Tools pour Unity entraîne la compilation des scripts, mais ne produit pas de fichier exécutable). Il est possible de [Unity de projets à partir de la ligne de commande](http://docs.unity3d.com/Manual/CommandLineArguments.html) (documentation Unity), donc il est possible de configurer un processus MSBuild sur un serveur TFS pour exécuter l’unité appropriée des commandes, sous réserve que Unity lui-même soit installé sur cet ordinateur.<br /><br /> Unity propose également [Unity Cloud Build](https://build.cloud.unity3d.com/landing/), qui surveille un référentiel Git ou SVN et exécute des builds périodiques. À l’heure actuelle, il ne fonctionne pas avec Team Foundation Version Control ou Visual Studio Team Services.|  
|Serveur de builds local lié à Visual Studio Team Services|Possible|Étant donné les mêmes conditions que ci-dessus, il est plus possible de diriger des builds déclenchées via Visual Studio Team Services pour utiliser un ordinateur TFS sur site.  Consultez [serveur de builds](../Topic/Deploy%20and%20configure%20a%20build%20server.md) pour obtenir des instructions.|  
|Service de contrôleur hébergé de Visual Studio Team Services|Non|Unity builds ne sont pas pris en charge actuellement.|  
|Définitions de builds avec des pré-scripts et des post-scripts|Oui|Une définition de build personnalisée qui utilise la ligne de commande Unity pour exécuter une build peut également être configurée pour des scripts de pré- ou post-compilation.|  
|Intégration continue, y compris les archivages contrôlés|Oui|Archivages contrôlés pour TFVC uniquement si Git utilise un modèle de requête d'extraction plutôt que des archivages.|  
  
## <a name="testing"></a>Test  
 Lien de référence : **[test de l’application](/devops-test-docs/test/test-apps-early-and-often)**  
  
|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|  
|-------------|--------------------------|-------------------------|  
|Planification de tests, création de cas de test et organisation de suites de tests|Oui||  
|Test manuel|Oui||  
|Gestionnaire de tests (enregistrer et rejouer des tests)|Appareils Windows et émulateurs Android uniquement||  
|Couverture du code|Non applicable|Non applicable car le test unitaire se produit dans Unity et non dans Visual Studio. Voir ci-dessous.|  
|[Test unitaire de votre Code.](../test/unit-test-your-code.md)|Dans Unity, mais pas dans Visual Studio|Unity fournit sa propre unité d’infrastructure de test dans le cadre de [Outils de Test Unity](https://www.assetstore.unity3d.com/en/#!/content/13802) (magasin de ressources Unity). Les résultats des tests unitaires sont signalés dans Unity et ne seront pas visibles dans Visual Studio.|  
|[Utilisation d’UI Automation pour tester votre Code](../test/use-ui-automation-to-test-your-code.md)|Non|Les tests codés de l'interface utilisateur s'appuient sur des contrôles lisibles dans l'interface utilisateur de l'application. Les applications Unity sont graphiques par nature et le contenu n'est donc pas lisible par les outils de test codés de l'interface utilisateur.|  
  
## <a name="improve-code-quality"></a>Améliorer la qualité du code  
 Lien de référence : **[améliorer la qualité du Code](../test/improve-code-quality.md)**  
  
|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|  
|-------------|--------------------------|-------------------------|  
|[Analyse de la qualité du Code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Oui|Peut analyser le code de script c# dans Visual Studio.|  
|[Recherche du Code dupliqué à l’aide de Code Clone Detection](../Topic/Finding%20Duplicate%20Code%20by%20using%20Code%20Clone%20Detection.md)|Oui|Peut analyser le code de script c# dans Visual Studio.|  
|[Mesure de la complexité et la facilité de maintenance du Code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Oui|Peut analyser le code de script c# dans Visual Studio.|  
|[Explorateur de performances](../profiling/performance-explorer.md)|Non|Utilisez le [profileur Unity](http://docs.unity3d.com/Manual/Profiler.html) (site Web Unity).|  
|[Analyser les problèmes de mémoire .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|Non|Visual Studio Tools ne possède pas de raccordements dans l'infrastructure Mono (tels qu'ils sont utilisés par Unity) pour le profilage. Utilisez le [profileur Unity](http://docs.unity3d.com/Manual/Profiler.html) (documentation Unity).|  
  
## <a name="release-management"></a>Gestion des versions  
 Lien de référence : **[automatiser les déploiements avec Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|  
|-------------|--------------------------|-------------------------|  
|Gérer les processus de publication des versions|Oui||  
|Déploiement sur des serveurs pour le chargement de version test via des scripts|Oui||  
|Télécharger vers le magasin d'applications|Partial|Les extensions sont disponibles qui peuvent automatiser ce processus pour certains magasins d’applications.  Consultez [Extensions pour Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS); par exemple, le [extension pour Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Moniteur avec HockeyApp  
 Lien de référence : **[analyse avec HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Fonctionnalité|Prise en charge avec Unity|Commentaires supplémentaires|  
|-------------|--------------------------|-------------------------|  
|Bloquer la distribution bêta analytique et télémétrie|Oui|HockeyApp est particulièrement utile pour gérer la distribution bêta et obtenir des rapports d’incidents.<br /><br /> De télémétrie à partir de scripts c#, il est possible d’utiliser n’importe quelle infrastructure analytique autant qu’il s’exécute sur la version .NET utilisée par Unity. Toutefois, cette solution permet l'analyse seulement dans les scripts de jeu et pas plus profondément dans le moteur Unity. Actuellement il n’existe aucun plug-in pour Application Insights, mais les plug-ins sont disponibles pour d’autres solutions analytique tels que [Unity Analytique](https://www.assetstore.unity3d.com/en/#!/content/28120) et [Google Analytique](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Les services tels que Unity Analytics qui comprennent la nature d'un projet Unity fournissent bien entendu une analyse beaucoup plus explicite que les infrastructures génériques.|