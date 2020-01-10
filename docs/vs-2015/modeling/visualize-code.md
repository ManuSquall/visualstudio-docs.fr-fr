---
title: Visualiser le code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9dcb6edf8ce69d48805c3ad8c3c25ef9cc0ed591
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851343"
---
# <a name="visualize-code"></a>Visualiser du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser les outils de modélisation et de visualisation dans Visual Studio pour aider à comprendre le code existant et à décrire votre application. Cela vous permet de savoir visuellement comment vos changements peuvent affecter le code et vous aide à évaluer le travail et les risques qui résultent de ces modifications. Par exemple :

- Pour comprendre les relations dans votre code, mappez visuellement ces relations.

- Pour décrire l'architecture de votre système et assurer la cohérence du code avec sa conception, créez des diagrammes de couche et validez le code par rapport à ces diagrammes.

- Pour décrire les structures de classes, créez des diagrammes de classes.

- Pour modéliser et communiquer différents aspects du système, dessinez des diagrammes UML (Unified Modeling Language). Par exemple, vous pouvez modéliser les composants, les types, les interactions et les processus d'un système.

  Ces outils vous aident également à communiquer plus facilement avec les personnes impliquées dans votre projet. Par exemple, vous pouvez utiliser des diagrammes de classes UML pour créer un glossaire commun pour discuter du système avec les parties prenantes, les utilisateurs et les membres d'équipe du projet.

  Pour connaître les versions de Visual Studio qui prennent en charge chaque fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

|||
|-|-|
|**Comprendre le code et ses relations :**<br /><br /> Mapper des relations entre des éléments de code spécifiques.<br /><br /> Voir une présentation des relations dans votre code pour l'ensemble de la solution.<br /><br /> **Remarque**: dans cette version de Visual Studio, le terme *carte de code* est utilisé à la place de *graphique de dépendance*.|-   [mapper des dépendances entre vos solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Rechercher des problèmes potentiels à l’aide d’analyseurs de carte de code](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [mapper des méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Comprendre les structures de classes :**<br /><br /> Visualiser la structure des classes dans un projet en créant des diagrammes de classes à partir du code.|[Guide pratique pour ajouter des diagrammes de classes aux projets (Concepteur de classes)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Décrire la conception du système de haut niveau et valider le code par rapport à cette conception :**<br /><br /> Décrire la conception système de haut niveau et ses dépendances prévues en créant des diagrammes de couche. Valider le code par rapport à cette conception pour s'assurer que les dépendances dans le code demeurent cohérentes avec la conception.|-   [créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)<br />[diagrammes de couche -   : référence](../modeling/layer-diagrams-reference.md)<br />[diagrammes de couche -   : indications](../modeling/layer-diagrams-guidelines.md)<br />-   [valider du code avec des diagrammes de couche](../modeling/validate-code-with-layer-diagrams.md)|
|**Communiquez les exigences et l’architecture de l’utilisateur :**<br /><br /> Modéliser les besoins des utilisateurs et l'architecture de votre système logiciel en dessinant les diagrammes UML suivants : activité, composant, classe, séquence et cas d'usage.|-   [créer des modèles pour votre application](../modeling/create-models-for-your-app.md)<br />[Configuration requise pour les utilisateurs du modèle](../modeling/model-user-requirements.md) -   <br />-   [modéliser l’architecture de votre application](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Ressources externes

|**Catégorie**|**Links**|
|------------------|---------------|
|**Forums**|-   [Outils de visualisation et de modélisation Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling (outils DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogs**|[Blog Visual Studio ALM + Team Foundation Server](https://blogs.msdn.com/b/visualstudioalm)|
|**Articles et journaux techniques**|[Forum sur l’architecture MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Voir aussi
 [Scénario : modifier votre conception à l’aide de la visualisation et de la modélisation](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [analyse et modélisation architecture](../modeling/analyze-and-model-your-architecture.md) [créer des modèles pour votre modèle d’application](../modeling/create-models-for-your-app.md) modèle d' [impératifs de l’utilisateur](../modeling/model-user-requirements.md) [l’architecture de votre application](../modeling/model-your-app-s-architecture.md) [utilise des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md)
