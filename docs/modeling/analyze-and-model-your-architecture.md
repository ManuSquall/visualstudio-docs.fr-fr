---
title: Analyser et modéliser votre architecture
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22a0547374087927e7fc2d3da89c3fe4f2a5c2b1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="analyze-and-model-your-architecture"></a>Analyser et modéliser votre architecture
Assurez-vous que votre application répond aux impératifs de l’architecture en utilisant Visual Studio architecture et modélisation des outils permettant de concevoir et modéliser votre application.

* Appréhendez le code de programme existant plus facilement en utilisant Visual Studio pour visualiser la structure, le comportement et les relations du code.

* Formez votre équipe le besoin d’en respectant les dépendances architecturales.

* Créez des modèles à différents niveaux de détails tout au long du cycle de vie de l’application dans le cadre de votre processus de développement.

Consultez [scénario : modifier votre conception à l’aide de la visualisation et de modélisation](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="to"></a>À

|||
|-|-|
|**Visualiser du code**:<br /><br /> -Consultez organisation et les relations du code en créant des cartes de code. Visualisez les dépendances entre les assemblys, les espaces de noms, les classes, les méthodes et ainsi de suite.<br />-Voir la structure de classe et les membres d’un projet spécifique en créant des diagrammes de classes à partir de code.<br />-Recherchez des conflits entre votre code et sa conception en créant des diagrammes de dépendance pour valider le code.|-   [Visualiser du code](../modeling/visualize-code.md)<br />-   [Utilisation des Classes et d’autres Types (Concepteur de classes)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Vidéo : Comprendre la conception à partir de code avec des cartes de code Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Vidéo : Valider des dépendances de votre architecture en temps réel](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Définir l’architecture**:<br /><br /> -Permet de définir et appliquer des contraintes sur les dépendances entre les composants de votre code en créant des diagrammes de dépendance.|-   [Vidéo : Valider des dépendances d’architecture avec Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Valider votre système avec les spécifications et la conception prévue**<br /><br /> -Valider les dépendances de code avec des diagrammes de dépendance qui décrivent l’architecture prévue et empêchent les modifications entrent en conflit avec la conception.|-   [Vidéo : Valider des dépendances d’architecture avec Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Partager des modèles, des diagrammes et des cartes de code à l’aide du contrôle de version Team Foundation**:<br /><br /> -Placez cartes de code, des projets et diagrammes deoendency sous contrôle de version Team Foundation pour pouvoir les partager.| |
|**Personnaliser des modèles et des diagrammes**:<br /><br /> -Permet de créer vos propres langages spécifiques à un domaine.|-   [Kit de développement logiciel de modélisation pour Visual Studio - langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Générer du texte à l’aide de modèles T4**:<br /><br /> -Utilisez les blocs de texte et la logique de contrôle à l’intérieur des modèles pour générer des fichiers texte.<br /> -Génération de modèle T4 avec MSBuild inclus dans Visual Studio|-   [Génération de code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md)|

Pour connaître les versions de Visual Studio qui prennent en charge chaque fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="types-of-models-and-their-uses"></a>Types de modèles et leurs utilisations

|**Type de modèle et utilisations courantes**|
|-------------------------------------|
|**Cartes de code**<br /><br /> Les cartes de code vous aident à voir l’organisation et les relations dans votre code.<br /><br /> Utilisations courantes :<br /><br /> -Examiner le code de programme afin de mieux comprendre sa structure et ses dépendances, comment mettre à jour et estimer le coût des modifications proposées.<br /><br /> Consultez :<br /><br /> -   [Mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Rechercher des problèmes potentiels à l’aide des analyseurs de carte de code](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Diagramme de dépendances**<br /><br /> Diagrammes de dépendance vous permettent de définir la structure d’une application en tant qu’ensemble de couches ou de blocs avec des dépendances explicites. Vous pouvez exécuter la validation pour détecter les conflits entre les dépendances dans le code et celles décrites dans un diagramme de dépendance.<br /><br /> Utilisations courantes :<br /><br /> -Stabiliser la structure de l’application par le biais de nombreuses modifications pendant sa durée de vie.<br />-Détection des conflits de dépendance involontaires avant d’archiver les modifications apportées au code.<br /><br /> Consultez :<br /><br /> -   [Créer des diagrammes de dépendance à partir de votre code.](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)<br />-   [Valider le code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)|
|**Langage spécifique à un domaine (DSL)**<br /><br /> Un langage spécifique à un domaine est une notation que vous concevez dans un but spécifique. Dans Visual Studio, il est en général graphique.<br /><br /> Utilisations courantes :<br /><br /> -Générer ou configurer certaines parties de l’application. Un travail est requis pour développer la notation et les outils. Le résultat est ainsi plus adapté à votre domaine qu’une personnalisation UML.<br />-Pour les grands projets ou dans les lignes de produits où l’investissement dans le développement du DSL et ses outils est amorti par son utilisation dans plusieurs projets.<br /><br /> Consultez :<br /><br /> -   [Kit de développement logiciel de modélisation pour Visual Studio - langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Où peut-on obtenir plus d’informations ?

[Visual Studio Visualization and Modeling Forum des outils](http://go.microsoft.com/fwlink/?LinkId=184720)

## <a name="see-also"></a>Voir aussi

- [Nouveautés](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps et Application Lifecycle Management](http://msdn.microsoft.com/Library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
