---
title: Analyser et modéliser votre architecture
ms.date: 11/04/2016
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1db28867ea47752aa74b7898c44e797c0704594
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544220"
---
# <a name="analyze-and-model-your-architecture"></a>Analyser et modéliser votre architecture

Assurez-vous que votre application répond aux exigences architecturales en utilisant les outils d’architecture et de modélisation de Visual Studio pour concevoir et modéliser votre application.

* Appréhendez le code de programme existant plus facilement en utilisant Visual Studio pour visualiser la structure, le comportement et les relations du code.

* Informez votre équipe de la nécessité de respecter les dépendances architecturales.

* Créez des modèles à différents niveaux de détails tout au long du cycle de vie de l’application dans le cadre de votre processus de développement.

Voir [scénario : modifier votre conception à l’aide de la visualisation et de la modélisation](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="article-reference"></a>Référence de l’article

|Scénario|Articles|
|-|-|
|**Visualiser le code**:<br /><br />-Consultez l’organisation et les relations du code en créant des cartes de code. Visualisez les dépendances entre les assemblys, les espaces de noms, les classes, les méthodes et ainsi de suite.<br />-Consultez la structure de classe et les membres d’un projet spécifique en créant des diagrammes de classes à partir du code.<br />-Recherchez des conflits entre votre code et sa conception en créant des diagrammes de dépendance pour valider le code.|- [Visualiser le code](../modeling/visualize-code.md)<br />- [Utilisation des classes et d’autres types (Concepteur de classes)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />- [Vidéo : comprendre la conception à partir du code avec les cartes de code Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />- [Vidéo : valider vos dépendances d’architecture en temps réel](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Définir l’architecture**:<br /><br />-Définir et appliquer des contraintes sur les dépendances entre les composants de votre code en créant des diagrammes de dépendance.|- [Vidéo : valider les dépendances d’architecture avec Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Valider votre système avec les spécifications et la conception prévue**<br /><br />-Validez les dépendances de code avec des diagrammes de dépendance qui décrivent l’architecture prévue et empêchez les modifications susceptibles d’entrer en conflit avec la conception.|- [Vidéo : valider les dépendances d’architecture avec Visual Studio (Channel 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Personnaliser des modèles et des diagrammes**:<br /><br />-Créez vos propres langages spécifiques à un domaine.|- [Kit de développement logiciel de modélisation pour Visual Studio-langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Générer du texte à l’aide de modèles T4**:<br /><br />-Utilisez des blocs de texte et une logique de contrôle à l’intérieur de modèles pour générer des fichiers texte.<br /> -Génération de modèle T4 avec MSBuild inclus dans Visual Studio|- [Génération de code et modèles de texte T4](../modeling/code-generation-and-t4-text-templates.md)|
|**Partager des modèles, des diagrammes et des cartes de code à l’aide du contrôle de version Team Foundation**:<br /><br />-Placez des cartes de code, des projets et des diagrammes de dépendance sous le contrôle de version Team Foundation afin de pouvoir les partager.| |

Pour connaître les éditions de Visual Studio qui prennent en charge chaque fonctionnalité, consultez la page [prise en charge d’édition pour les outils d’architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-typical-uses"></a>Types de modèles et utilisations classiques

### <a name="code-maps"></a>Cartes de code

Les cartes de code vous aident à voir l’organisation et les relations dans votre code.

**Utilisations courantes :**

- Examiner le code de programme pour mieux comprendre sa structure et ses dépendances, la manière de le mettre à jour, puis estimer le coût des modifications proposées.

**Verr**

- [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)
- [Utiliser des cartes du code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)
- [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagrams"></a>Diagrammes de dépendance

Les diagrammes de dépendance vous permettent de définir la structure d’une application sous la forme d’un ensemble de couches ou de blocs avec des dépendances explicites. La validation dynamique montre les conflits entre les dépendances dans le code et les dépendances décrites dans un diagramme de dépendance.

**Utilisations courantes :**

- Stabiliser la structure de l’application au moyen de nombreuses modifications pendant sa durée de vie.
- Détecter les conflits de dépendance involontaires avant d’archiver les modifications apportées au code.

**Verr**

- [Créer des diagrammes de dépendance à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)
- [Diagrammes de dépendance : référence](../modeling/layer-diagrams-reference.md)
- [Valider du code avec des diagrammes de dépendance](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Langage spécifique à un domaine (DSL)

Un langage spécifique à un domaine est une notation que vous concevez dans un but spécifique. Dans Visual Studio, il s’agit généralement d’un graphique.

**Utilisations courantes :**

- Générer ou configurer certaines parties de l’application. Un travail est requis pour développer la notation et les outils. Le résultat est ainsi plus adapté à votre domaine qu’une personnalisation UML.
- Pour les grands projets ou dans les lignes de produits où l’investissement effectué dans le développement du langage spécifique à un domaine et ses outils est amorti par son utilisation dans plusieurs projets.

**Verr**

- [SDK de modélisation pour Visual Studio - Langages spécifiques à un domaine](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="see-also"></a>Voir aussi

- [Nouveautés de la modélisation dans Visual Studio 2017](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps et Application Lifecycle Management](/azure/devops/user-guide/devops-alm-overview)
