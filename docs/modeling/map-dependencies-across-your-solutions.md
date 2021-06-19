---
title: Visualiser les dépendances avec les cartes de code
description: Découvrez comment les cartes de code vous aident à voir comment le code s’ajuste sans lire les fichiers et les lignes de code.
ms.custom: SEO-VS-2020
ms.date: 05/16/2021
ms.topic: how-to
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d33e3d882d25045802f2c015c88b87b970d9d04e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390435"
---
# <a name="map-dependencies-with-code-maps"></a>Mapper des dépendances avec des cartes de code

Dans cet article, vous allez apprendre à visualiser les dépendances dans votre code avec des cartes de code.

## <a name="what-are-code-maps"></a>Que sont les cartes de code ?

Dans Visual Studio, les cartes de code vous aident à voir plus rapidement comment votre code de programme s’ajuste sans lire les fichiers et les lignes de code.  Avec ces mappages, vous pouvez voir l’organisation et les relations dans votre code, y compris sa structure et ses dépendances, comment la mettre à jour et estimer le coût des modifications proposées.

![Afficher les dépendances avec des cartes de code dans Visual Studio](../modeling/media/codemapsmainintro.png)

Vous pouvez mapper les dépendances de code dans les langages suivants :

- Visual C# ou Visual Basic dans une solution ou des assemblys (*.dll* ou *.exe*)

- Code C ou C++ natif ou managé dans des projets Visual C++, des fichiers d’en-tête (*. h* ou `#include` ) ou des fichiers binaires

- projets et assemblys X++ créés à partir de modules .NET pour Microsoft Dynamics AX.

> [!NOTE]
> Pour les projets autres que C# ou Visual Basic, il existe moins d’options pour démarrer une carte de code ou ajouter des éléments à une carte de code existante. Par exemple, vous ne pouvez pas cliquer avec le bouton droit sur un objet dans l’éditeur de texte d’un projet C++ et l’ajouter à une carte de code. Toutefois, vous pouvez glisser-déplacer des éléments de code individuels ou des fichiers à partir de **Explorateur de solutions**, **affichage de classes** et l' **Explorateur d’objets**.

## <a name="prerequisites"></a>Prérequis

Pour créer une carte de code dans Visual Studio, commencez par [installer les composants de la **carte de code** et de la **validation de dépendances en direct**](install-architecture-tools.md)

Pour créer et modifier des cartes de code, vous avez besoin de l' **édition Visual Studio Enterprise**. Toutefois, dans les éditions Visual Studio Community et Professional, vous pouvez ouvrir des diagrammes qui ont été générés dans l’édition Enterprise, mais vous ne pouvez pas les modifier.

> [!NOTE]
> Avant de partager des cartes créées dans Visual Studio Enterprise avec d’autres utilisateurs de Visual Studio Professional, assurez-vous que tous les éléments de la carte (tels que les éléments masqués, les groupes développés et les liens entre les groupes) sont visibles.

## <a name="add-a-code-map"></a>Ajouter une carte de code

Vous pouvez créer une carte de code vide et y faire glisser des éléments, notamment des références d’assembly, des fichiers et des dossiers, ou vous pouvez générer une carte de code pour tout ou partie de votre solution.

Pour ajouter une carte de code vide :

1. Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel du nœud racine de votre solution. Choisissez **Ajouter**  >  **un nouvel élément**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , sous **installé**, choisissez la catégorie **général** .

3. Choisissez le modèle **document de graphique orienté (. dgml)** , puis sélectionnez **Ajouter**.

   > [!TIP]
   > Ce modèle peut ne pas apparaître dans l’ordre alphabétique, donc faites défiler jusqu’au bas de la liste de modèles si vous ne le voyez pas.

   Une carte vide apparaît dans le dossier **éléments de solution** de votre solution.

De même, vous pouvez créer un nouveau fichier de mappage de code sans l’ajouter à votre solution en sélectionnant **architecture**  >  **nouvelle carte de code** ou **fichier**  >  **nouveau**  >  **fichier**.

En savoir plus :
- [Partager des cartes de code](share-code-maps.md)
- [Créer des cartes de code pour C++](code-maps-for-cpp.md)
- [Améliorer les performances de la carte de code](code-maps-performance.md)

## <a name="generate-a-code-map-for-your-solution"></a>Générer une carte de code pour votre solution

Pour afficher toutes les dépendances dans votre solution :

1. Dans la barre de menus, choisissez **architecture**  >  **générer une carte du code pour la solution**. Si votre code n’a pas changé depuis la dernière fois que vous l’avez créé, vous pouvez sélectionner **architecture**  >  **générer une carte du code pour la solution sans génération à** la place.

   ![Générer une commande de carte du code](../modeling/media/codemapsarchitecturemenu.png)

   Un mappage est généré qui affiche les assemblys de niveau supérieur et les liens agrégés entre eux. Plus le lien global est large, plus il représente de dépendances.

2. Utilisez le bouton **Légende** dans la barre d’outils de la carte de code pour afficher ou masquer la liste des icônes de type de projet (comme Projet de test, Projet web et Projet de téléphone), les éléments de code (comme Classes, Méthodes et Propriétés) et les types de relations (comme Hérite de, Implémente et Appelle).

   ![Graphique de dépendance de niveau supérieur des assemblys](../modeling/media/dependencygraph_toplevelassemblies.png)

   Cet exemple de solution contient des dossiers de solution (**Tests** et **Composants**), des projets de test, des projets web et des assemblys. Par défaut, toutes les relations d’imbrication apparaissent sous forme de *groupes* que vous pouvez développer et réduire. Le groupe **Externes** contient les éléments qui ne font pas partie de votre solution, notamment les dépendances de plateforme. Les assemblys externes affichent uniquement les éléments utilisés. Par défaut, les types de base du système sont masqués pour ne pas trop encombrer la carte.

3. Pour descendre dans la hiérarchie de la carte, développez les groupes qui représentent des projets et des assemblys. Pour développer tout, appuyez sur **Ctrl+A** pour sélectionner tous les nœuds. Ensuite, choisissez **Groupe**, puis **Développer** dans le menu contextuel.

   ![Développement de tous les groupes dans une carte du code](../modeling/media/codemapsexpandallgroups.png)

4. Ceci peut toutefois ne pas s’avérer très utile pour une solution de grande taille. En fait, pour les solutions complexes, les limitations de mémoire peuvent vous empêcher de développer tous les groupes. Pour visualiser l’intérieur d’un nœud individuel, développez-le. Déplacez le pointeur de la souris au-dessus du nœud, puis cliquez sur le chevron (flèche bas) quand il apparaît.

   ![Développement d’un nœud dans une carte du code](../modeling/media/dependencygraph_containment.png)

   Ou utilisez le clavier en sélectionnant l’élément, puis en appuyant sur la touche plus ( **+** ). Pour explorer des niveaux plus profonds de code, procédez de même pour les espaces de noms, les types et les membres.

   > [!TIP]
   > Pour plus d’informations sur l’utilisation des cartes de code à l’aide de la souris, du clavier et de la fonction tactile, consultez [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md).

5. Pour simplifier la carte et cibler des parties individuelles, choisissez **Filtres** dans la barre d’outils de la carte de code et sélectionnez uniquement les types de nœuds et de liens qui vous intéressent. Par exemple, vous pouvez masquer tous les conteneurs Dossier Solution et Assembly.

   ![Simplifier la carte en filtrant les conteneurs](../modeling/media/codemapsfilterfoldersassemblies.png)

   Vous pouvez également simplifier la carte en masquant ou en supprimant des groupes et des éléments individuels de la carte, sans affecter le code de la solution sous-jacent.

6. Pour visualiser les relations entre les éléments, sélectionnez-les dans la carte. Les couleurs des liens indiquent les types de relations, comme le montre le volet **Légende** .

   ![Afficher les dépendances entre vos solutions](../modeling/media/codemapsmainintro.png)

   Dans cet exemple, les liens violets correspondent aux appels, les liens en pointillés aux références et les liens bleu clair à l’accès aux champs. Les liens verts peuvent représenter l’héritage ou correspondre à des *liens globaux* qui indiquent plusieurs types de relations (ou *catégories*).

   > [!TIP]
   > Si vous voyez un lien vert, il ne signifie peut-être pas qu’il existe simplement une relation d’héritage. Il peut également exister des appels de méthode, mais ceux-ci sont masqués par la relation d’héritage. Pour afficher des types de liens spécifiques, utilisez les cases à cocher dans le volet **filtres** pour masquer les types qui ne vous intéressent pas.

7. Pour obtenir plus d’informations sur un élément ou un lien, déplacez le pointeur sur celui-ci jusqu’à ce qu’une info-bulle apparaisse. Celle-ci donne des détails sur un élément de code ou les catégories représentées par un lien.

   ![Afficher les catégories d'une relation](../modeling/media/codemapsshowlinkcatgories.png)

8. Pour examiner les éléments et les dépendances représentés par un lien global, sélectionnez d’abord le lien, puis ouvrez son menu contextuel. Choisissez **Afficher les liens de contribution** (ou **Afficher les liens de contribution sur des nouvelles cartes de code**). Cette opération développe les groupes aux deux extrémités du lien et affiche uniquement les éléments et les dépendances qui participent au lien.

9. Pour vous concentrer sur des parties spécifiques de la carte, vous pouvez continuer à supprimer les éléments qui ne vous intéressent pas. Par exemple, pour analyser l’affichage des classes et des membres, filtrez simplement tous les nœuds d’espace de noms dans le volet **Filtres** .

   ![Exploration au niveau des classes et membres](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Pour simplifier une carte de solution complexe, vous pouvez aussi générer une nouvelle carte contenant une sélection d’éléments à partir d’une carte existante. Maintenez la **touche Ctrl** enfoncée tout en sélectionnant les éléments sur lesquels vous souhaitez vous concentrer, ouvrez le menu contextuel, puis choisissez **nouveau graphique à partir de la sélection**.

    ![Afficher les éléments sélectionnés dans une nouvelle carte du code](../modeling/media/codemapsshowonnewmap.png)

11. Le contexte est reporté sur la nouvelle carte. Masquez les dossiers de solution et tout autre conteneur que vous ne souhaitez pas voir à l’aide du volet **filtres** .

    ![Filtrer les conteneurs pour simplifier l'affichage](../modeling/media/codemapsexpandnewgroups.png)

12. Développez les groupes et sélectionnez les éléments dans la carte pour afficher les relations.

    ![Sélectionner des éléments pour afficher les relations](../modeling/media/codemapsviewnewrelationships.png)

Voir aussi :

- [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md)
- [Personnaliser des cartes de code en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Rechercher des problèmes potentiels dans votre code en [exécutant un analyseur](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-dependencies"></a>Afficher les dépendances

Supposons que vous ayez une révision du code à effectuer dans certains fichiers avec des modifications en attente. Pour visualiser les dépendances dans ces modifications, vous pouvez créer une carte de code à partir de ces fichiers.

   ![Afficher les dépendances spécifiques dans une carte du code](../modeling/media/codemapsspecificdependenciesintro.png)

1. Dans **Explorateur de solutions**, sélectionnez les projets, références d’assembly, dossiers, fichiers, types ou membres que vous souhaitez mapper.

   ![Sélectionner les éléments à mapper](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Dans la barre d’outils **Explorateur de solutions** , choisissez **afficher sur la carte de code** ![ créer un graphique à partir des nœuds sélectionnés ](../modeling/media/createnewgraphfromselectedbutton.gif) . Ou bien, ouvrez le menu contextuel d’un ou d’un groupe d’éléments et choisissez **afficher sur la carte de code**.

   Vous pouvez également faire glisser des éléments depuis **Explorateur de solutions**, **affichage de classes** ou l' **Explorateur d’objets**, dans une carte de code [nouvelle](#add-a-code-map) ou existante. Pour inclure la hiérarchie parente de vos éléments, appuyez sur la touche **CTRL** et maintenez-la enfoncée pendant que vous faites glisser des éléments ou utilisez le bouton **inclure les parents** dans la barre d’outils de la carte de code pour spécifier l’action par défaut. Vous pouvez également faire glisser des fichiers d’assembly en dehors de Visual Studio, par exemple à partir de l' **Explorateur Windows**.

   > [!NOTE]
   > Lorsque vous ajoutez des éléments à partir d’un projet partagé entre plusieurs applications, comme Windows Phone ou Microsoft Store, ces éléments apparaissent sur la carte avec le projet d’application actif. Si vous modifiez le contexte vers un autre projet d’application et ajoutez des éléments à partir du projet partagé, ces éléments apparaissent alors avec le projet d’application qui vient d’être activé. Les opérations que vous effectuez avec un élément de la carte s’appliquent uniquement aux éléments qui partagent le même contexte.

3. La carte montre les éléments sélectionnés au sein des assemblys conteneurs.

   ![Éléments sélectionnés affichés sous forme de groupes dans la carte](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Pour explorer des éléments, développez-les. Déplacez le pointeur de la souris au-dessus d’un élément, puis cliquez sur l’icône en forme de chevron (flèche bas) quand elle apparaît.

   ![Développer un nœud dans une carte de code](../modeling/media/dependencygraph_containment.png)

   Pour développer tous les éléments, sélectionnez-les à l’aide de la **touche Ctrl** + **A**, puis ouvrez le menu contextuel de la carte et choisissez **groupe**  >  **développer**. Toutefois, cette option n’est pas disponible si le développement de tous les groupes crée une carte inutilisable ou entraîne des problèmes de mémoire.

5. Continuez à développer les éléments qui vous intéressent, juste jusqu’au niveau de la classe et du membre, si nécessaire.

   ![Développer les groupes au niveau de la classe et du membre](../modeling/media/codemapsexpandtoclassandmember.png)

   Pour afficher les membres qui figurent dans le code, mais qui n’apparaissent pas sur la carte, cliquez sur l’icône récupérer à l’icône des **enfants** récupérer les ![ enfants ](../modeling/media/dependencygraph_deletednodesicon.png) dans le coin supérieur gauche d’un groupe.

6. Pour afficher d’autres d’éléments associés à ceux présents sur la carte, sélectionnez un élément et choisissez **Afficher les éléments associés** dans la barre d’outils de la carte de code, puis sélectionnez le type d’éléments associés à ajouter à la carte. Vous pouvez également sélectionner un ou plusieurs éléments, ouvrir le menu contextuel, puis choisir l’option **Afficher** pour le type d’éléments associés à ajouter à la carte. Exemple :

    Pour un **assembly**, choisissez :

    |Option|Description|
    |-|-|
    |**Afficher les assemblys qui sont référencés par cela**|Ajoutez les assemblys que cet assembly référence. Les assemblys externes apparaissent dans le groupe **Externes** .|
    |**Afficher les assemblys qui référencent cela**|Ajoutez les assemblys de la solution qui référencent cet assembly.|

    Pour un **espace de noms**, choisissez **Afficher l’assembly conteneur** s’il n’est pas visible.

    Pour une **classe** ou une **interface**, choisissez :

    |Option|Description|
    |-|-|
    |**Afficher les types de base**|Pour une classe, ajoutez la classe de base et les interfaces implémentées.<br /><br /> Pour une interface, ajoutez des interfaces de base.|
    |**Afficher les types dérivés**|Pour une classe, ajoutez des classes dérivées.<br /><br /> Pour une interface, ajoutez les interfaces dérivées et les structures et classes d’implémentation.|
    |**Afficher les types qui sont référencés par cela**|Ajoutez toutes les classes, avec leurs membres, que cette classe utilise.|
    |**Afficher les types qui référencent cela**|Ajoutez toutes les classes, avec leurs membres, qui utilisent cette classe.|
    |**Afficher l’espace de noms contenant**|Ajoutez l’espace de noms parent.|
    |**Afficher l’espace de noms contenant et l’assembly conteneur**|Ajoutez la hiérarchie de conteneurs parents.|
    |**Afficher tous les types de base**|Ajoutez la hiérarchie de classe de base ou d’interface de manière récursive.|
    |**Afficher tous les types dérivés**|Pour une classe, ajoutez toutes les classes dérivées de manière récursive.<br /><br /> Pour une interface, ajoutez toutes les interfaces dérivées et les structures et classes d’implémentation de manière récursive.|

     Pour une **méthode**, choisissez :

    |Option|Description|
    |-|-|
    |**Afficher les méthodes qui sont appelées par cela**|Ajoutez les méthodes que cette méthode appelle.|
    |**Afficher les champs qui sont référencés par cela**|Ajoutez les champs que cette méthode référence.|
    |**Afficher le type conteneur**|Ajoutez le type de parent.|
    |**Afficher le type conteneur, l’espace de noms contenant et l’assembly conteneur**|Ajoutez la hiérarchie de conteneurs parents.|
    |**Afficher les méthodes remplacées**|Pour une méthode qui remplace d’autres méthodes ou implémente la méthode d’une interface, ajoutez toutes les méthodes abstraites ou virtuelles dans les classes de base qui sont substituées et, le cas échéant, la méthode de l’interface implémentée.|

     Pour un **champ** ou une **propriété**, choisissez :

    |Option|Description|
    |-|-|
    |**Afficher le type conteneur**|Ajoutez le type de parent.|
    |**Afficher le type conteneur, l’espace de noms contenant et l’assembly conteneur**|Ajoutez la hiérarchie de conteneurs parents.|

    ![Afficher les méthodes appelées par ce membre](../modeling/media/codemapsshowrelatedmethods.png)

7. La carte affiche les relations. Dans cet exemple, la carte affiche les méthodes appelées par la `Find` méthode et leur emplacement dans la solution ou en externe.

   ![Afficher les dépendances spécifiques dans une carte du code](../modeling/media/codemapsspecificdependenciesintro.png)

8. Pour simplifier la carte et cibler des parties individuelles, choisissez **Filtres** dans la barre d’outils de la carte de code et sélectionnez uniquement les types de nœuds et de liens qui vous intéressent. Par exemple, désactivez l’affichage des dossiers solution, des assemblys et des espaces de noms.

   ![Utiliser le volet de filtre pour simplifier l'affichage](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Voir aussi

- [Partager des cartes de code](share-code-maps.md)
- [Créer des cartes de code pour C++](code-maps-for-cpp.md)
- [Améliorer les performances de la carte de code](code-maps-performance.md)
- [Vidéo : comprendre la conception à partir du code avec les cartes de code Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Vidéo : comprendre la conception à partir du code avec les cartes de code Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Utiliser des cartes du code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)
- [Mapper les méthodes sur la pile des appels tout en déboguant](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md)
- [Personnaliser des cartes de code en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
