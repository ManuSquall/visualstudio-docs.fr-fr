---
title: Nouveautés&#39;en matière de conception
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c68db12f8ecea523327250fec1f600639a2f267
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659242"
---
# <a name="whats-new-for-design-in-visual-studio-in-visual-studio-2015"></a>Nouveautés de la conception dans Visual Studio dans Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Cette version de Visual Studio inclut les améliorations suivantes pour vous aider à mieux comprendre et concevoir le code.

 **Cartes de code et graphiques de dépendance**

 Dans Visual Studio Enterprise, quand vous voulez comprendre les dépendances spécifiques dans votre code, vous pouvez les visualiser en créant des cartes de code. Vous pouvez alors parcourir ces relations à l'aide de la carte, laquelle est affichée en regard de votre code. Les cartes de code peuvent aussi vous aider à savoir où vous vous trouvez dans le code pendant que vous travaillez ou déboguez le code. Vous passerez donc moins de temps à lire le code, tout en approfondissant vos connaissances sur sa conception.

 Dans la mise en production finale (RTM), nous avons simplifié l’utilisation des liens et des menus contextuels pour les éléments de code en regroupant les commandes dans des sections en rapport avec la sélection, la modification, la gestion des groupes et la modification de la disposition du contenu des groupes. Notez également que les projets de test sont affichés dans un style différent des autres projets et que nous avons mis à jour les icônes des éléments sur la carte avec des versions plus appropriées.

 ![Afficher les éléments sélectionnés sur une nouvelle carte de code](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Voici quelques autres améliorations qui ont été apportées :

- **Amélioration des diagrammes de haut en bas**. Pour les solutions Visual Studio de taille moyenne à grande, vous pouvez désormais utiliser un menu Architecture simplifié pour obtenir des cartes de code plus utiles pour votre solution. Les assemblys de votre solution sont regroupés par dossier de solution, ce qui vous permet de les voir dans le contexte et de tirer parti de l'effort que vous avez fourni en termes de structuration de la solution. Vous voyez immédiatement les projets et les références d'assemblys, puis les types de liens apparaissent. En outre, les assemblys externes à votre solution sont regroupés de manière plus compacte.

- **Les projets de test ont un style différent et ils peuvent être filtrés**. Vous pouvez désormais identifier plus facilement et plus rapidement les projets de test sur la carte, car ils ont un style différent. Vous pouvez aussi les filtrer pour pouvoir vous concentrer sur le code actif de l'application.

- **Simplification des liens de dépendance externe**. Les liens de dépendance ne représentent plus l'héritage de System.Object, System.ValueType, System.Enum et System.Delegate, ce qui facilite l'identification des dépendances externes dans votre carte de code.

- **L'exploration des liens de dépendance tiennent compte des filtres**. Vous obtenez un diagramme clair et utile qui, lorsqu'il est développé, vous permet de comprendre les contributions associées à un lien de dépendance. Le diagramme est moins encombré et il tient compte des options de filtrage des liens que vous avez sélectionnées.

- **Les éléments de code sont ajoutés à une carte de code avec leur contexte**. Étant donné que les diagrammes sont maintenant affichés avec leur contexte (jusqu'au dossier d'assembly et de solution sur lequel vous pouvez appliquer un filtre, si nécessaire), vous obtenez des diagrammes plus utiles quand vous faites glisser-déplacer des éléments de code à partir de l'Explorateur de solutions, de l'Affichage de classes ou de l'Explorateur d'objets, ou lors de la sélection d'éléments dans l'Explorateur de solutions et du choix de l'option Afficher sur la carte de code.

- **Génération plus rapide de cartes de code réactives**. Les opérations de glisser-déplacer produisent un résultat immédiat et les liens entre les nœuds sont créés beaucoup plus rapidement, sans affecter les opérations ultérieures initiées par l'utilisateur, telles que le développement d'un nœud ou la demande de nœuds supplémentaires. Quand vous créez des cartes de code sans générer la solution, tous les cas extrêmes, par exemple lorsque les assemblys ne sont pas générés, sont désormais traités.

- **Non-obligation de régénérer votre solution.** Fournit de meilleures performances lors de la création et de la modification des diagrammes.

- **Filtrage des groupes et des nœuds d'éléments de code**. Vous pouvez rapidement mettre en ordre vos cartes en affichant ou en masquant des éléments de code en fonction de leur catégorie, ainsi qu'en regroupant les éléments de code par dossier de solution, assembly, espace de noms, dossier de projet et type.

- **Filtrage des relations pour faciliter la lecture des diagrammes**. Le filtrage des liens s'applique désormais également aux liens intergroupes, ce qui rend l'utilisation de la fenêtre de filtre moins gênante qu'elle ne l'était dans les versions précédentes.

- **Création de diagrammes à partir de l'Affichage de classes et de l'Explorateur d'objets**. Glissez-déplacez des fichiers et des assemblys sur une carte nouvelle ou existante à partir des fenêtres Affichage de classes et Explorateur d'objets.

  Consultez [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md).

  **Autres modifications de conception et de modélisation dans cette version :**

- **Diagrammes de couche**. Mettez à jour ces diagrammes à l'aide de l'Affichage de classes et de l'Explorateur d'objets. Pour répondre aux exigences de conception de logiciel, utilisez des diagrammes de couche pour décrire les dépendances souhaitées pour votre logiciel. Assurez la cohérence du code avec cette conception en recherchant le code qui ne respecte pas ces contraintes et en validant le code ultérieur avec cette ligne de base.

- **Diagrammes UML**. Vous ne pouvez plus créer des diagrammes de classes UML et des diagrammes de séquence à partir du code. Pour créer ces diagrammes, vous devez à présent utiliser de nouveaux éléments UML.

- **Navigateur de l'architecture**. Vous ne pouvez plus utiliser le Navigateur de l'architecture pour créer des diagrammes. Mais vous pouvez toujours utiliser l'Explorateur de solutions.

## <a name="VersionSupport"></a>Prise en charge d’édition pour les outils d’architecture et de modélisation

Visual Studio 2015 est disponible dans plusieurs éditions. Les outils d’architecture et de modélisation ne sont pas tous pris en charge. Le tableau ci-après décrit la disponibilité de chaque outil.

|**Fonctionnalité**|**Entreprise**|**Technologiques**|**Community**|**Exprime**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Cartes de code**|Oui|Prend uniquement en charge la lecture et le filtrage de cartes de code, l’ajout de nouveaux nœuds génériques et la création d’un graphique orienté à partir d’une sélection.|-|-|
|**Diagrammes de classes UML**|Oui|-|-|-|
|**Diagrammes de séquence UML**|Oui|-|-|-|
|**Diagrammes de cas d’usage UML**|Oui|-|-|-|
|**Diagrammes d’activités UML**|Oui|-|-|-|
|**Diagrammes de composants UML**|Oui|-|-|-|
|**Diagrammes de couche**|Oui|-|-|-|
|**Graphiques orientés** (diagrammes dgml)|Oui|Oui|-|-|
|**Clone de code**|Oui|-|-|-|