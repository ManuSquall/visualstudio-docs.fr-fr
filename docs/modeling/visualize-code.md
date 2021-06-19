---
title: Visualiser du code
description: Découvrez comment vous pouvez utiliser les outils de visualisation et de modélisation de Visual Studio pour comprendre le code existant et décrire votre application.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90c180bf9d910227013c2e089001ce5332cd1bd3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388345"
---
# <a name="visualize-code"></a>Visualiser du code

Vous pouvez utiliser les outils de modélisation et de visualisation dans Visual Studio pour aider à comprendre le code existant et à décrire votre application. Cela vous permet de savoir visuellement comment vos changements peuvent affecter le code et vous aide à évaluer le travail et les risques qui résultent de ces modifications. Exemple :

- Pour comprendre les relations dans votre code, mappez visuellement ces relations.

- Pour décrire l’architecture de votre système et garder le code cohérent avec sa conception, créez des diagrammes de dépendance et validez le code par rapport à ces diagrammes.

- Pour décrire les structures de classes, créez des diagrammes de classes.

Ces outils vous aident également à communiquer plus facilement avec les personnes impliquées dans votre projet.

Pour connaître les éditions de Visual Studio qui prennent en charge chaque fonctionnalité, consultez la page [prise en charge d’édition pour les outils d’architecture et de modélisation](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Que voulez-vous faire ?

|Scénario|Articles|
|-|-|
|**Comprendre le code et ses relations :**<br /><br /> Mapper des relations entre des éléments de code spécifiques.<br /><br /> Voir une présentation des relations dans votre code pour l'ensemble de la solution.|- [Mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md)<br />- [Utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Rechercher des problèmes potentiels à l’aide d’analyseurs de carte de code](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Comprendre les structures de classes :**<br /><br /> Visualiser la structure des classes dans un projet en créant des diagrammes de classes à partir du code.|[Guide pratique pour ajouter des diagrammes de classes aux projets (Concepteur de classes)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Décrire la conception système de haut niveau et valider le code par rapport à cette conception :**<br /><br /> Décrivez la conception du système de haut niveau et ses dépendances prévues en créant des diagrammes de dépendance. Valider le code par rapport à cette conception pour s'assurer que les dépendances dans le code demeurent cohérentes avec la conception.|- [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)<br />- [Diagrammes de dépendance : indications](../modeling/layer-diagrams-guidelines.md)<br />- [Valider du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Voir aussi

- [Installer les outils de code de l’architecture](install-architecture-tools.md)
- [Scénario : modifier votre conception à l’aide de la visualisation et de la modélisation](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Architecture d’analyse et de modèle](../modeling/analyze-and-model-your-architecture.md)
- [Modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md)
- [Utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
