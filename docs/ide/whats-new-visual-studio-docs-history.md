---
title: 'Documentation Visual Studio : historique des nouveautés '
titleSuffix: ''
description: Historique des nouveautés de la documentation Visual Studio
ms.date: 09/30/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 6d0b60c548e4e5d42a10e82754d045073f016f8b
ms.sourcegitcommit: ea3c985a23851b424127f2205f617446b6536578
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91621748"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Historique des nouveautés de la documentation Visual Studio

Bienvenue dans l’historique des nouveautés de Visual Studio docs. Cette rubrique contient les modifications majeures apportées aux documents antérieurs au 2020 septembre (à compter du 1er juillet 2020). Pour obtenir les dernières nouveautés, consultez [documentation de Visual Studio : nouveautés de la documentation](whats-new-visual-studio-docs.md).

## <a name="august-2020"></a>Août 2020
### <a name="azure"></a>Azure

**Nouveaux Articles**

- [Ajoutez Azure application Insights à l’aide](../azure/azure-app-insights-add-connected-service.md) des services connectés à Visual Studio services connectés pour VS 2019 16,7
- [Ajouter le cache Azure pour les éléments ReDim à l’aide](../azure/azure-cache-for-redis-add-connected-service.md) des services connectés à Visual Studio services connectés pour VS 2019 16,7
- [Ajoutez des Azure Cosmos dB à votre application à l’aide](../azure/azure-cosmosdb-add-connected-service.md) des services connectés à Visual Studio services connectés pour VS 2019 16,7
- [Ajouter Azure signalr à l’aide](../azure/azure-signalr-add-connected-service.md) des services connectés à Visual Studio services connectés pour VS 2019 16,7
- [Ajouter une connexion aux services connectés à Azure SQL Database](../azure/azure-sql-database-add-connected-service.md) pour VS 2019 16,7

**Articles mis à jour**

- [Ajout de stockage Azure à l’aide des services connectés de Visual Studio](../azure/vs-azure-tools-connected-services-storage.md)
  - Services connectés pour VS 2019 16,7
  - Article sur les services connectés Azure Storage : mise à jour des types de projet et d’interface utilisateur pris en charge

### <a name="code-quality"></a>Qualité du code

**Nouveaux Articles**

- [Ca1310 : spécifiez StringComparison pour l’exactitude](../code-quality/ca1310.md) -ajoutez de la documentation pour ca1310 et mettez à jour la documentation pour CA1307
- [CA1837 : utilisez Environment. ProcessID au lieu de process. GetCurrentProcess (). ID](../code-quality/ca1837.md) -docs pour CA1837
- [CA1838 : éviter `StringBuilder` les paramètres pour P/Invoke](../code-quality/ca1838.md) -ajouter de la documentation pour CA1838
- [CA2008 : ne pas créer de tâches sans passer un TaskScheduler](../code-quality/ca2008.md) -ajouter une documentation pour CA2008
- [CA2249 : envisagez d’utiliser String. Contains à la place de String. IndexOf](../code-quality/ca2249.md) -docs pour CA2249
- [CA2361 : Assurez-vous que la classe générée automatiquement contenant DataSet. ReadXml () n’est pas utilisée avec des données non fiables.](../code-quality/ca2361.md) autres règles de DataSet/DataTable
- [CA2362 : un jeu de données ou un DataTable non sécurisé dans un type sérialisable généré automatiquement peut être vulnérable aux attaques d’exécution de code à distance](../code-quality/ca2362.md) . autres règles de DataSet/DataTable
- [IL3000 : Évitez d’utiliser le chemin d’accès au fichier d’assembly lors de la publication en tant que documentation à fichier unique](../code-quality/il3000.md) à ajouter à IL3000
- [IL3001 : éviter d’accéder au chemin d’accès au fichier d’assembly lors de la publication sous la forme d’un fichier unique](../code-quality/il3001.md) -ajouter des documents pour IL3001

**Updated**

- [Ca1002 : ne pas exposer les listes génériques](../code-quality/ca1002.md) -ajouter la configuration-section de surface de l’API
- [Ca1046 : ne pas surcharger l’opérateur égal à sur les types référence](../code-quality/ca1046.md) -ajouter la configuration-section surface de l’API
- [CA1307 : spécifiez StringComparison pour clarifier](../code-quality/ca1307.md) -ajouter de la documentation pour ca1310 et mettre à jour la documentation pour CA1307
- [CA1700 : ne nommez pas les valeurs enum &#39;réservé&#39;](../code-quality/ca1700.md) -Add configurabilité-API surface
- [CA1707 : les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707.md) -ajouter une configuration-section de surface de l’API
- [CA1822 : marquer les membres comme statiques](../code-quality/ca1822.md) -ajouter une configuration-section surface de l’API
- [Ca2351 : Assurez-vous que l’entrée de DataSet. ReadXml () est approuvée](../code-quality/ca2351.md) -plus de règles de DataSet/DataTable
- [Installer des analyseurs tiers](../code-quality/install-roslyn-analyzers.md) -modification de la structure et des titres pour la documentation de l’analyse du code

### <a name="containers"></a>Conteneurs

**Articles mis à jour**

- [Déployer un conteneur ASP.net dans un registre de conteneurs à l’aide de Visual Studio](../containers/hosting-web-apps-in-docker.md) -mises à jour des outils de conteneur pour l’interface utilisateur de publication de visual studio 16,7
- [Prise en main de Visual Studio Kubernetes Tools](../containers/tutorial-kubernetes-tools.md) -didacticiel Kubernetes : ajouter des étapes de suppression

### <a name="deployment"></a>Déploiement

**Nouveaux Articles**

- [Extension des projets Visual Studio installer et .net core 3,1](../deployment/installer-projects-net-core.md) -création d’une nouvelle page d’aide pour les projets du programme d’installation fonctionnalités .net Core 3,1

**Articles mis à jour**

- [Déployer votre application dans un dossier, IIS, Azure ou une autre](../deployment/deploying-applications-services-and-components-resources.md) mise à jour de destination-déploiement
- [Déploiement dans Visual Studio](../deployment/index.yml) -mises à jour du déploiement

### <a name="extensibility"></a>Extensibilité

**Articles mis à jour**
- Sous- [types de projet](../extensibility/internals/project-subtypes.md) -mettre en retrait les éléments de liste
- [Référence de valeur de couleur pour Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) -AB # 1759333 corriger les en-têtes de colonnes manquantes

### <a name="get-started"></a>Prise en main

**Articles mis à jour**

- [Étape 5 : déployer votre application ASP.net core dans Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) -mises à jour des didacticiels vidéo pour les nouvelles services connectés IU

### <a name="ide"></a>IDE

**Nouveaux Articles**

- [Modifier la touche d’aide F1 dans Visual Studio](./not-in-toc/change-f1-help-key.md) -page d’aide par défaut de refactorisation F1
- [Aide F1 pour l’éditeur de texte](./not-in-toc/default-f1-text-editor.md) -page d’aide F1 par défaut de refactorisation
- [Convertir `typeof` en `nameof` ](./reference/convert-typeof-to-nameof.md) -Convert typeof en refactorisation nameof
- [Simplifier l’expression LINQ](./reference/simplify-linq-expression.md) -simplifier la refactorisation d’expression LINQ

**Articles mis à jour**

- [Personnaliser les dispositions de fenêtres dans Visual Studio](./customizing-window-layouts-in-visual-studio.md) : ajouter des onglets de document monikered verticaux info pour personnaliser la rubrique disposition des fenêtres
- [Guide pratique pour signaler un problème avec Visual Studio ou Visual Studio Installer](./how-to-report-a-problem-with-visual-studio.md)
  - Ajout d’informations supplémentaires à NMI
  - Redid la page de l’ensemble du rapport
- [Aide F1](./not-in-toc/default.md) -page d’aide par défaut de refactorisation F1
- [Récupération automatique, environnement, boîte de dialogue Options](./reference/autorecover-environment-options-dialog-box.md) -ajouter des informations sur les emplacements de fichiers d’enregistrement automatique mis à jour
- [Options, éditeur de texte, de base (Visual Basic), avancé](./reference/options-text-editor-basic-visual-basic.md) -ajout de la documentation de base pour les indicateurs de nom de paramètre Inline
- [Options, éditeur de texte, C#,](./reference/options-text-editor-csharp-advanced.md) documentation de base ajoutée pour les indicateurs de nom de paramètre Inline
- [Conseils et astuces sur les performances de Visual Studio](./visual-studio-performance-tips-and-tricks.md) : ajouter les informations « désactiver le mode carte » et « désactiver le retour automatique à la ligne »
- [Nouveautés de Visual studio 2019](./whats-new-visual-studio-2019.md) -mettre à jour nouveautés dans visual studio 2019 avec 16,7 informations sur la disponibilité générale

### <a name="rtvs"></a>RTVS

**Articles mis à jour**

- [Utiliser des tables SQL Server et R](../rtvs/integrating-sql-server-with-r.md) -corrigées pour inclure des en-têtes de colonnes

## <a name="july-2020"></a>Juillet 2020
### <a name="code-quality"></a>Qualité du code

**Nouveaux Articles**

- [Ca1417 : ne pas utiliser `OutAttribute` sur les paramètres de chaîne pour P/Invoke](../code-quality/ca1417.md) -ajouter de la documentation pour ca1417
- [CA1805 : ne pas initialiser inutilement.](../code-quality/ca1805.md) -Ajouter des documents pour CA1805
- [CA1836 : préférer IsEmpty sur Count quand disponible](../code-quality/ca1836.md) -ajouter de la documentation pour CA1836 (préférer IsEmpty au-dessus du nombre)
- [Ca2016 : transférez le paramètre CancellationToken aux méthodes qui acceptent un](../code-quality/ca2016.md) document ca2016-transférer le paramètre CancellationToken aux méthodes qui en prennent une
- [Ca2350 : Assurez-vous que l’entrée DataTable. ReadXml () est approuvée](../code-quality/ca2350.md) -données de désérialisation du DataSet/DataTable initial
- [Ca2351 : Assurez-vous que l’entrée du DataSet. ReadXml () est approuvée](../code-quality/ca2351.md) -données de désérialisation du DataSet/DataTable initial
- [CA2352 : un jeu de données ou un DataTable non sécurisé dans un type sérialisable peut être vulnérable aux attaques par exécution de code à distance](../code-quality/ca2352.md) -documents de désérialisation de DataSet/DataTable initiaux
- [CA2353 : jeu de données ou DataTable non sécurisés dans le type sérialisable](../code-quality/ca2353.md) -documentation des règles de désérialisation du DataSet/DataTable initial
- [CA2354 : un jeu de données ou un DataTable non sécurisé dans un graphique d’objets désérialisé peut être vulnérable à une attaque d’exécution de code à distance](../code-quality/ca2354.md) -documents de désérialisation de DataSet/DataTable initiaux
- [CA2355 : jeu de données ou DataTable non sécurisés dans le graphique d’objets désérialisés](../code-quality/ca2355.md) -documents de désérialisation de DataSet/DataTable initiaux
- [CA2356 : type de données ou DataSet non sécurisé dans le graphique d’objets désérialisés Web](../code-quality/ca2356.md) -données de désérialisation du DataSet/DataTable initial (docs)

### <a name="containers"></a>Conteneurs

**Nouveaux Articles**

- [Configurer le processus local avec Kubernetes](../containers/configure-local-process-with-kubernetes.md) -local Process with Kubernetes : YAML configuration
- [Utiliser un processus local avec Kubernetes (](../containers/local-process-kubernetes.md) préversion)-migration d’espaces de développement
- [Fonctionnement de Processus local avec Kubernetes](../containers/overview-local-process-kubernetes.md)
  - Processus local pour Kubernetes : ajouter une section de routage
  - Migration d’espaces de développement

### <a name="cross-platform"></a>Multiplateforme

**Articles mis à jour**

- [Journal des modifications (outils Visual Studio pour Unity, Windows)](../cross-platform/change-log-visual-studio-tools-for-unity.md) -Bosselage VSTU journal des modifications sur 4.7.1.0
- [Journal des modifications (outils Visual Studio pour Unity, Mac)](../cross-platform/change-log-visual-studio-tools-for-unity-mac.md) -Bosselage VSTUM journal des modifications sur 2.7.1.0

### <a name="get-started"></a>Prise en main

**Nouveaux Articles**

- [Didacticiel : étendre une simple console C# application](../get-started/csharp/tutorial-console-part-2.md) -version étendre la première version du didacticiel de trottoir

### <a name="ide"></a>IDE

**Nouveaux Articles**

- [Directives](./developer-community-guidelines.md) de la communauté des développeurs : ajout de directives Devcom
- [Saisie semi-automatique IntelliSense pour les types et les méthodes d’extension inimportés](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>Installer

**Nouveaux Articles**

- [Mettre à jour Visual Studio avec une disposition hors connexion minimale](../install/update-minimal-layout.md) -fonctionnalité de disposition minimale de document
- [Guide Visual Studio Enterprise](../install/visual-studio-enterprise-guide.md) -Guide de l’entreprise

### <a name="javascript"></a>JavaScript

**Nouveaux Articles**

- [Compiler du code machine (Node.js)](../javascript/compile-typescript-code-npm.md) -compiler et générer des générations
- [Compiler du code machine (ASP.net Core)](../javascript/compile-typescript-code-nuget.md) -compiler et générer des générations

### <a name="msbuild"></a>MSBuild

**Nouveaux Articles**

- [Métadonnées d’élément MSBuild courantes](../msbuild/common-msbuild-item-metadata.md) -MSBuild : ajouter une table pour les métadonnées facultatives avec lien et lien ressources
- [Filtres de solution dans MSBuild](../msbuild/solution-filters.md) -filtres de solution MSBuild

### <a name="test"></a>Test

**Nouveaux Articles**

- [Déboguer et analyser des tests unitaires avec l’Explorateur de tests](../test/debug-unit-tests-with-test-explorer.md) -travail des performances de l’Explorateur de tests

**Articles mis à jour**

- [Configurer des tests unitaires à l’aide d’un fichier *. RunSettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - Mises à jour de la configuration des tests unitaires à l’aide d’un fichier RunSettings
  - La description de l’option de responsabilité a été modifiée et un exemple a été ajouté.