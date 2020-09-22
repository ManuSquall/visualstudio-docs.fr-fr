---
title: 'Documentation Visual Studio : historique des nouveautés '
titleSuffix: ''
description: Historique des nouveautés de la documentation Visual Studio
ms.date: 09/01/2020
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
ms.openlocfilehash: 8505f98163c57fe276bcf4c76195fe843300394f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809464"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Historique des nouveautés de la documentation Visual Studio

Bienvenue dans l’historique des nouveautés de Visual Studio docs. Cette rubrique contient les modifications majeures apportées aux documents antérieurs au 2020 août (à compter du 1er juillet 2020). Pour obtenir les dernières nouveautés, consultez [documentation de Visual Studio : nouveautés de la documentation](whats-new-visual-studio-docs.md).

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

### <a name="get-started"></a>Commencer

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