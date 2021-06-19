---
title: Outils d’analyse d’architecture & de modélisation
description: Concevez et modélisez votre application pour vous assurer que votre application répond aux exigences architecturales.
ms.custom: SEO-VS-2020
ms.date: 06/04/2021
ms.topic: overview
helpviewer_keywords:
- diagrams - modeling
- architecture
- code visualization
- application design
- code exploration
- modeling
- application architecture
- architecture [Visual Studio ALM], modeling
- application modeling
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 542b74e7d3bb73847303fa4215651eea7e110e91
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384874"
---
# <a name="analyze-and-model-your-architecture"></a>Analyser et modéliser votre architecture

Assurez-vous que votre application répond aux exigences architecturales en utilisant les outils d’architecture et de modélisation de Visual Studio pour concevoir et modéliser votre application.

1. Comprenez mieux le code de programme existant en Visualisez la structure, le comportement et [les relations du code avec les](visualize-code.md) mappages de code et les diagrammes de dépendance.
    - Consultez l’organisation et les relations du code en créant des **cartes de code**. 
    - Visualisez les dépendances entre les assemblys, les espaces de noms, les classes, les méthodes et ainsi de suite.
    - Recherchez des conflits entre votre code et sa conception en créant des **diagrammes de dépendance** pour valider le code.
    - Consultez la structure de classe et les membres d’un projet spécifique en [créant des diagrammes de classes à partir du code](../ide/class-designer/designing-and-viewing-classes-and-types.md).
    - [Générez du texte à l’aide de modèles T4](../modeling/code-generation-and-t4-text-templates.md) avec des blocs de texte et une logique de contrôle à l’intérieur de modèles pour générer des fichiers textuels. 
    
1. Informez votre équipe de la nécessité de respecter les dépendances architecturales.

1. Créez des modèles à différents niveaux de détails tout au long du cycle de vie de l’application dans le cadre de votre processus de développement.

Voir [scénario : modifier votre conception à l’aide de la visualisation et de la modélisation](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="code-maps"></a>Cartes de code

Les cartes de code sont un type de modèle qui vous permet de voir l’organisation et les relations dans votre code.

Utilisez Maps pour examiner le code de programme afin de mieux comprendre sa structure et ses dépendances, comment le mettre à jour et estimer le coût des modifications proposées.

En savoir plus :
- [Installer les outils de code de l’architecture](install-architecture-tools.md)
- [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)
- [Utiliser des cartes du code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)
- [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="dependency-diagrams"></a>Diagrammes de dépendance

Les diagrammes de dépendance vous permettent de définir la structure d’une application sous la forme d’un ensemble de couches ou de blocs avec des dépendances explicites. La validation dynamique montre les conflits entre les dépendances dans le code et les dépendances décrites dans un diagramme de dépendance.

Utilisez des diagrammes de dépendances pour : 
- Stabiliser la structure de l’application au moyen de nombreuses modifications pendant sa durée de vie.
- Détecter les conflits de dépendance involontaires avant d’archiver les modifications apportées au code.

En savoir plus :
- [Installer les outils de code de l’architecture](install-architecture-tools.md)
- [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)
- [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)
- [Valider du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)

## <a name="domain-specific-language-dsl-models"></a>Modèles de langage spécifique à un domaine (DSL)

Un langage spécifique à un domaine est une notation que vous concevez dans un but spécifique. Dans Visual Studio, il s’agit généralement d’un graphique.

Utilisez le langage spécifique à un domaine pour : 
- Générer ou configurer certaines parties de l’application. Un travail est requis pour développer la notation et les outils. Le résultat est ainsi plus adapté à votre domaine qu’une personnalisation UML.
- Pour les grands projets ou dans les lignes de produits où l’investissement effectué dans le développement du langage spécifique à un domaine et ses outils est amorti par son utilisation dans plusieurs projets.

En savoir plus :
- [SDK de modélisation pour Visual Studio - Langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)


## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Prise en charge d’édition pour les outils d’architecture et de modélisation

Visual Studio est disponible dans plusieurs éditions. Les outils d’architecture et de modélisation ne sont pas tous pris en charge. Le tableau ci-après décrit la disponibilité de chaque outil.

|**Fonctionnalité**|**Édition entreprise**|**Édition professionnel**|**Community Edition**|
|-|-|-|-|
|**Cartes de code**|Oui|Prend uniquement en charge la lecture de cartes de code, le filtrage de cartes de code, l’ajout de nouveaux nœuds génériques et la création d’un graphique orienté à partir d’une sélection.|-|
|**Diagrammes de dépendance**|Oui|Prend uniquement en charge la lecture des diagrammes de dépendance.|Prend uniquement en charge la lecture des diagrammes de dépendance.|
|**Graphiques orientés** (diagrammes dgml)|Oui|Oui|Oui|
|**Clone de code**|Oui|-|-|
