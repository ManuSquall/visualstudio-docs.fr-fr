---
title: Mapper les dépendances dans vos solutions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code exploration, dependency graphs
- dependency graphs, exporting
- code exploration, relationships
- DGML
- graph documents
- code visualization [Visual Studio ALM]
- graph documents, saving
- dependencies, visualizing
- dependency graphs, saving
- Visual Studio Ultimate, code visualization
- code, visualizing
- dependency graphs, creating
- dependency graphs
- graph documents, exporting
- code exploration, visualizing
ms.assetid: e04850a2-17c5-459b-93ec-6c74143b3292
caps.latest.revision: 245
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c9ff6901db602a812c06c6d8cc08ce55ef6d1d7e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952585"
---
# <a name="map-dependencies-across-your-solutions"></a>Mapper les dépendances dans vos solutions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour comprendre les dépendances présentes dans votre code, vous pouvez les visualiser en créant des cartes de code. Vous pouvez ainsi voir comment le code s’ajuste sans avoir à parcourir les fichiers et les lignes de code.  
  
 ![Afficher les dépendances dans vos solutions](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
 **Voici quelques vidéos**:  
  
-   [Comprendre les dépendances existant dans votre code grâce à la virtualisation](http://go.microsoft.com/fwlink/?LinkID=252065)  
  
-   [Visualisation de l’impact d’une modification](http://go.microsoft.com/fwlink/?LinkID=252068)  
  
-   [Présentation du code complexe avec des cartes de code](http://go.microsoft.com/fwlink/?LinkID=259869)  
  
##  <a name="GetStarted"></a> Prise en main des cartes de code  
 **Pour utiliser des cartes de code, il vous l’un des éléments suivants**:  
  
-   Visual Studio Enterprise : Créer des cartes de code à partir de l’éditeur de code, l’Explorateur de solutions, affichage de classes ou Explorateur d’objets.  
  
-   Visual Studio Professional : Ouvrir des cartes de code, effectuer des modifications mineures et parcourir le code.  
  
> [!WARNING]
>  Avant de partager des cartes créées dans Visual Studio Enterprise avec d’autres personnes utilisant Visual Studio Professional, vérifiez que tous les éléments présents sur la carte (comme les éléments masqués, les groupes développés et les liens entre les groupes) sont visibles.  
  
 **Vous pouvez mapper les dépendances de code dans les langages suivants**:  
  
- Visual C# .NET ou Visual Basic .NET dans une solution ou des assemblys (.dll ou .exe)  
  
- Code C ou C++ natif ou managé dans des projets, fichiers d’en-tête (.h ou `#include`) ou des fichiers binaires Visual C++  
  
- projets et assemblys X++ créés à partir de modules .NET pour Microsoft Dynamics AX.  
  
  **Remarque :** Pour les projets autres que C# ou Visual Basic .NET, il existe moins d’options pour démarrer une carte de code ou ajouter des éléments à une carte de code existante. Par exemple, vous ne pouvez pas cliquer avec le bouton droit sur un objet dans l’éditeur de texte d’un projet C++ et l’ajouter à une carte de code. Toutefois, vous pouvez glisser-déplacer des éléments de code individuels ou des fichiers à partir de l’Explorateur de solutions, de l’affichage de classes et de l’Explorateur d’objets.  
  
#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>Pour afficher les dépendances globales dans votre solution  
  
1.  Ouvrez le menu **Architecture** .  
  
2.  Si vous venez juste d’ouvrir la solution et que vous ne l’avez pas encore générée, ou si votre code n’a pas changé depuis la dernière fois qu’il a été généré, choisissez **Générer une carte du code pour la solution**.  
  
3.  Si votre code n’a pas changé depuis la dernière fois qu’il a été généré, choisissez **Générer une carte du code pour la solution sans génération** pour créer plus rapidement la carte.  
  
4.  Consultez[Visualiser les dépendances globales](#SeeOverviewSource) pour comprendre comment utiliser des cartes de code pour afficher les dépendances globales dans votre solution.  
  
#### <a name="to-see-specific-dependencies-within-your-solution"></a>Pour visualiser des dépendances spécifiques dans votre solution  
  
1.  Une fois votre solution chargée, ouvrez l’ **Explorateur de solutions**.  
  
2.  Sélectionnez les projets, références d’assembly, dossiers, fichiers, types ou membres que vous souhaitez afficher sur la carte.  
  
3.  Sur le **l’Explorateur de solutions** barre d’outils, choisissez **afficher sur la carte de Code**![créer nouveau graphique à partir de nœuds bouton sélectionnés](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton "). Ou bien, ouvrez le menu contextuel et choisissez **Afficher sur la carte de code**. Vous pouvez également faire glisser des éléments à partir de l’affichage de classes ou de l’Explorateur d’objets vers une nouvelle carte de code ou une carte existante.  
  
4.  Consultez[Visualiser les dépendances spécifiques](#SeeSpecificSource) pour comprendre comment utiliser des cartes de code pour afficher des dépendances spécifiques au sein de votre solution.  
  
###  <a name="CreateEmptyMap"></a> Pour ajouter une nouvelle carte de code vide à votre solution  
  
1.  Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel du nœud racine de votre solution. Choisissez **Ajouter** , puis **Nouvel élément**.  
  
2.  Sous **Installé**, choisissez **Général**.  
  
3.  Dans le volet droit, choisissez **Document de graphique orienté** , puis **Ajouter**.  
  
     Vous disposez maintenant d’une carte vide qui apparaît dans le dossier **Éléments de solution** de votre solution.  
  
#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>Pour créer une carte de code vide sans l’ajouter à votre solution  
  
1.  Ouvrez le menu **Architecture** , puis choisissez **Nouvelle carte de code**.  
  
     \- ou -  
  
2.  Ouvrez le menu **Fichier** , puis choisissez **Nouveau** et **Fichier**.  
  
3.  Sous **Installé**, choisissez **Général**.  
  
4.  Dans le volet droit, choisissez **Document de graphique orienté** , puis **Ouvrir**.  
  
     Vous disposez maintenant d’une carte vide qui n’apparaît pas dans les dossiers de votre solution.  
  
##  <a name="SeeOverviewSource"></a> Visualiser les dépendances globales  
  
###  <a name="OverviewSource"></a> Visualiser les dépendances dans votre solution  
  
1. Dans le menu **Architecture** , choisissez **Générer une carte du code pour la solution**.  
  
    ![Générer une commande de carte de code](../modeling/media/codemapsarchitecturemenu.png "CodeMapsArchitectureMenu")  
  
    Vous obtenez une carte qui affiche les assemblys de niveau supérieur et les liens globaux qui les relient. Plus le lien global est large, plus il représente de dépendances.  
  
2. Utilisez le bouton **Légende** dans la barre d’outils de la carte de code pour afficher ou masquer la liste des icônes de type de projet (comme Projet de test, Projet web et Projet de téléphone), les éléments de code (comme Classes, Méthodes et Propriétés) et les types de relations (comme Hérite de, Implémente et Appelle).  
  
    ![Haut&#45;graphique de dépendance au niveau des assemblys](../modeling/media/dependencygraph-toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")  
  
    Cet exemple de solution contient des dossiers de solution (**Tests** et **Composants**), des projets de test, des projets web et des assemblys. Par défaut, toutes les relations d’imbrication apparaissent sous forme de *groupes*que vous pouvez développer et réduire. Le groupe **Externes** contient les éléments qui ne font pas partie de votre solution, notamment les dépendances de plateforme. Les assemblys externes affichent uniquement les éléments utilisés. Par défaut, les types de base du système sont masqués pour ne pas trop encombrer la carte.  
  
3. Pour descendre dans la hiérarchie de la carte, développez les groupes qui représentent des projets et des assemblys. Pour développer tout, appuyez sur **Ctrl+A** pour sélectionner tous les nœuds. Ensuite, choisissez **Groupe**, puis **Développer** dans le menu contextuel.  
  
    ![Développement de tous les groupes dans une carte de code](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")  
  
4. Ceci peut toutefois ne pas s’avérer très utile pour une solution de grande taille. En fait, pour les solutions complexes, les limitations de mémoire peuvent vous empêcher de développer tous les groupes. Pour visualiser l’intérieur d’un nœud individuel, développez-le. Déplacez le pointeur de la souris au-dessus du nœud, puis cliquez sur le chevron (flèche bas) quand il apparaît.  
  
    ![Développement d’un nœud dans une carte de code](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")  
  
    Ou bien, sélectionnez l’élément et appuyez sur la touche plus (**+**) du clavier. Pour explorer des niveaux plus profonds de code, procédez de même pour les espaces de noms, les types et les membres.  
  
   > [!TIP]
   >  Pour plus d’informations sur l’utilisation du code est mappé à l’aide de la souris, clavier et tactiles, consultez [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md).  
  
5. Pour simplifier la carte et cibler des parties individuelles, choisissez **Filtres** dans la barre d’outils de la carte de code et sélectionnez uniquement les types de nœuds et de liens qui vous intéressent. Par exemple, vous pouvez masquer tous les conteneurs Dossier Solution et Assembly.  
  
    ![Simplifier la carte en filtrant les conteneurs](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")  
  
    Vous pouvez également simplifier la carte en masquant ou en supprimant des groupes et des éléments individuels de la carte, sans affecter le code de la solution sous-jacent.  
  
6. Pour visualiser les relations entre les éléments, sélectionnez-les dans la carte. Les couleurs des liens indiquent les types de relations, comme le montre le volet **Légende** .  
  
    ![Afficher les dépendances dans vos solutions](../modeling/media/codemapsmainintro.png "CodeMapsMainIntro")  
  
    Dans cet exemple, les liens violets correspondent aux appels, les liens en pointillés aux références et les liens bleu clair à l’accès aux champs. Les liens verts peuvent représenter l’héritage ou correspondre à des *liens globaux* qui indiquent plusieurs types de relations (ou *catégories*).  
  
   > [!TIP]
   >  Si vous voyez un lien vert, il ne signifie peut-être pas qu’il existe simplement une relation d’héritage. Il peut également exister des appels de méthode, mais ceux-ci sont masqués par la relation d’héritage. Pour afficher des types de liens spécifiques, utilisez les cases à cocher dans le volet **Filtres** pour masquer les types qui ne vous intéressent pas.  
  
7. Pour obtenir plus d’informations sur un élément ou un lien, déplacez le pointeur sur celui-ci jusqu’à ce qu’une info-bulle apparaisse. Celle-ci donne des détails sur un élément de code ou les catégories représentées par un lien.  
  
    ![Afficher les catégories d’une relation](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")  
  
8. Pour examiner les éléments et les dépendances représentés par un lien global, sélectionnez d’abord le lien, puis ouvrez son menu contextuel. Choisissez **Afficher les liens de contribution** (ou **Afficher les liens de contribution sur des nouvelles cartes de code**). Cette opération développe les groupes aux deux extrémités du lien et affiche uniquement les éléments et les dépendances qui participent au lien.  
  
9. Pour cibler des parties spécifiques de la carte, continuez à supprimer les éléments qui ne vous intéressent pas. Par exemple, pour analyser l’affichage des classes et des membres, filtrez simplement tous les nœuds d’espace de noms dans le volet **Filtres** .  
  
     ![Parcours de niveau classe et du membre](../modeling/media/dependencygraph-expandedselectedgroups-2012.png "DependencyGraph_ExpandedSelectedGroups_2012")  
  
10. Pour simplifier une carte de solution complexe, vous pouvez aussi générer une nouvelle carte contenant une sélection d’éléments à partir d’une carte existante. Maintenez la touche **Ctrl** enfoncée tout en sélectionnant les éléments qui vous intéressent, ouvrez le menu contextuel, puis choisissez **Nouveau graphique à partir de la sélection**.  
  
     ![Afficher les éléments sélectionnés sur une nouvelle carte de code](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")  
  
11. Le contexte est reporté sur la nouvelle carte. Masquez les dossiers de solution et tout autre conteneur que vous ne souhaitez pas afficher à l’aide du volet **Filtres** .  
  
     ![Filtrer les conteneurs pour simplifier l’affichage](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")  
  
12. Développez les groupes et sélectionnez les éléments dans la carte pour afficher les relations.  
  
     ![Sélectionner les éléments à afficher les relations](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")  
  
    Voir aussi :  
  
-   [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [Personnaliser des cartes de code en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)  
  
-   Pour identifier les problèmes éventuels dans votre code, [exécutez un analyseur](../modeling/find-potential-problems-using-code-map-analyzers.md).  
  
###  <a name="OverviewCompiled"></a> Visualiser les dépendances entre les assemblys ou fichiers binaires  
  
1.  [Créez une carte de code vide](#GetStarted)ou ouvrez une carte de code existante (fichier .dgml).  
  
2.  Faites glisser sur la carte les assemblys ou fichiers binaires à représenter sur la carte à partir d’un emplacement externe à Visual Studio. Par exemple, vous pouvez faire glisser des assemblys ou des fichiers binaires à partir de l’Explorateur Windows ou de l’Explorateur de fichiers.  
  
> [!NOTE]
>  Vous ne pouvez faire glisser des assemblys ou des fichiers binaires à partir de l’Explorateur Windows ou de l’Explorateur de fichiers que si vous exécutez Visual Studio avec le même niveau d’autorisations de contrôle de compte d’utilisateur (UAC). Par exemple, si le contrôle de compte d’utilisateur est activé et que vous exécutez Visual Studio en tant qu’administrateur, l’Explorateur Windows ou l’Explorateur de fichiers bloque l’opération de glissement. Pour contourner ce problème, assurez-vous qu’ils s’exécutent tous les deux avec le même niveau d’autorisation ou désactivez le contrôle de compte d’utilisateur.  
  
##  <a name="SeeSpecificSource"></a> Visualiser les dépendances spécifiques  
 Par exemple, supposons que vous deviez réviser du code dans certains fichiers contenant des modifications en attente. Pour visualiser les dépendances dans ces modifications, vous pouvez créer une carte de code à partir de ces fichiers.  
  
 ![Afficher les dépendances spécifiques sur une carte de code](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
### <a name="see-specific-dependencies-in-your-solution"></a>Visualiser les dépendances spécifiques dans votre solution  
  
1.  Ouvrez l’ **Explorateur de solutions**. Sélectionnez les projets, références d’assembly, dossiers, fichiers, types et membres qui vous intéressent. Pour rechercher les éléments qui ont des dépendances sur les types ou les membres, ouvrez le menu contextuel du type ou du membre depuis l’ **Explorateur de solutions**. Choisissez le type de dépendance, puis sélectionnez les résultats.  
  
2.  Créez une carte de vos éléments et de leurs membres. Sur le **l’Explorateur de solutions** clic de la barre d’outils **afficher sur la carte de Code**![créer nouveau graphique à partir de nœuds bouton sélectionnés](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton").  
  
     ![Sélectionnez les éléments que vous souhaitez mapper](../modeling/media/codemapsselectinsolutionexplorer.png "CodeMapsSelectInSolutionExplorer")  
  
3.  La carte montre les éléments sélectionnés au sein des assemblys conteneurs.  
  
     ![Éléments affichés sous forme de groupes sur la carte sélectionnés](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")  
  
     Vous pouvez également faire glisser des éléments à partir de l’Explorateur de solutions, de l’affichage de classes ou de l’Explorateur d’objets vers une carte de code vide ou existante. Pour créer une carte vide, consultez [Créer une carte de code vide](#GetStarted). Pour inclure la hiérarchie parente de vos éléments, maintenez la touche **Ctrl** enfoncée tout en faisant glisser des éléments ou utilisez le bouton **Inclure les parents** dans la barre d’outils de la carte de code pour spécifier l’action par défaut.  
  
    > [!NOTE]
    >  Lorsque vous ajoutez des éléments à partir d’un projet partagé par plusieurs applications, comme Windows Phone ou Windows Store, ces éléments apparaissent sur la carte avec le projet d’application actif. Si vous modifiez le contexte vers un autre projet d’application et ajoutez des éléments à partir du projet partagé, ces éléments apparaissent alors avec le projet d’application qui vient d’être activé. Les opérations que vous effectuez avec un élément de la carte s’appliquent uniquement aux éléments qui partagent le même contexte.  
  
4.  Pour explorer des éléments, développez-les. Déplacez le pointeur de la souris au-dessus d’un élément, puis cliquez sur l’icône en forme de chevron (flèche bas) quand elle apparaît.  
  
     ![Développement d’un nœud dans une carte de code](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")  
  
     Pour développer tous les éléments, sélectionnez-les en appuyant sur **Ctrl+A**, ouvrez le menu contextuel de la carte, puis choisissez **Groupe**, **Développer**. Toutefois, cette option n’est pas disponible si le développement de tous les groupes crée une carte inutilisable ou entraîne des problèmes de mémoire.  
  
5.  Continuez à développer les éléments qui vous intéressent jusqu’au niveau de la classe et du membre si nécessaire.  
  
     ![Développer les groupes au niveau de la classe et du membre](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")  
  
     Pour afficher les membres qui sont dans le code mais n’apparaissent pas sur la carte, cliquez sur le **récupérer à nouveau les enfants** icône ![récupérer à nouveau une icône d’enfants](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") en haut à gauche d’un groupe.  
  
6.  Pour afficher d’autres d’éléments associés à ceux présents sur la carte, sélectionnez un élément et choisissez **Afficher les éléments associés** dans la barre d’outils de la carte de code, puis sélectionnez le type d’éléments associés à ajouter à la carte. Vous pouvez également sélectionner un ou plusieurs éléments, ouvrir le menu contextuel, puis choisir l’option **Afficher** pour le type d’éléments associés à ajouter à la carte. Exemple :  
  
     Pour un **assembly**, choisissez :  
  
    |||  
    |-|-|  
    |**Afficher les assemblys qui sont référencés par cela**|Ajoutez les assemblys que cet assembly référence. Les assemblys externes apparaissent dans le groupe **Externes** .|  
    |**Afficher les assemblys qui référencent cela**|Ajoutez les assemblys de la solution qui référencent cet assembly.|  
  
     Pour un **espace de noms**, choisissez **Afficher l’assembly conteneur**s’il n’est pas visible.  
  
     Pour une **classe** ou une **interface**, choisissez :  
  
    |||  
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
  
    |||  
    |-|-|  
    |**Afficher les méthodes qui sont appelées par cela**|Ajoutez les méthodes que cette méthode appelle.|  
    |**Afficher les champs qui sont référencés par cela**|Ajoutez les champs que cette méthode référence.|  
    |**Afficher le type conteneur**|Ajoutez le type de parent.|  
    |**Afficher le type conteneur, l’espace de noms contenant et l’assembly conteneur**|Ajoutez la hiérarchie de conteneurs parents.|  
    |**Afficher les méthodes remplacées**|Pour une méthode qui remplace d’autres méthodes ou implémente la méthode d’une interface, ajoutez toutes les méthodes abstraites ou virtuelles dans les classes de base qui sont substituées et, le cas échéant, la méthode de l’interface implémentée.|  
  
     Pour un **champ** ou une **propriété**, choisissez :  
  
    |||  
    |-|-|  
    |**Afficher le type conteneur**|Ajoutez le type de parent.|  
    |**Afficher le type conteneur, l’espace de noms contenant et l’assembly conteneur**|Ajoutez la hiérarchie de conteneurs parents.|  
  
     ![Afficher les méthodes appelées par ce membre](../modeling/media/codemapsshowrelatedmethods.png "CodeMapsShowRelatedMethods")  
  
7.  La carte affiche les relations. Dans cet exemple, les méthodes appelées par la méthode `Find` et leur emplacement dans la solution ou à l’extérieur.  
  
     ![Afficher les dépendances spécifiques sur une carte de code](../modeling/media/codemapsspecificdependenciesintro.png "CodeMapsSpecificDependenciesIntro")  
  
8.  Pour simplifier la carte et cibler des parties individuelles, choisissez **Filtres** dans la barre d’outils de la carte de code et sélectionnez uniquement les types de nœuds et de liens qui vous intéressent. Par exemple, désactivez l’affichage des dossiers solution, des assemblys et des espaces de noms.  
  
     ![Utilisez le volet de filtre pour simplifier l’affichage](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")  
  
##  <a name="SeeSourceHeader"></a> Visualiser les dépendances entre les fichiers sources et les fichiers d’en-tête C et C++  
 Si vous souhaitez créer des cartes plus complètes pour des projets C++, définissez l’option du compilateur d’informations de consultation (**/FR**) sur ces projets. Consultez [/FR, /Fr (Create .Sbr File)](http://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896). Sinon, un message vous invite à définir cette option. Si vous sélectionnez **OK**, l’option est définie uniquement pour la carte active. Vous pouvez choisir de masquer le message pour toutes les cartes ultérieures. Si vous masquez ce message, vous pouvez le faire réapparaître. Affectez à la clé de Registre suivante la valeur `0` ou supprimez-la :  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\NativeProvider : AutoEnableSbr**  
  
 Lorsque vous ouvrez une solution qui contient des projets Visual C++, la mise à jour de la base de données IntelliSense peut prendre un certain temps. Pendant ce temps, il est impossible de créer des cartes de code pour les fichiers d’en-tête (.h ou `#include`) tant que la base de données IntelliSense n’a pas terminé la mise à jour. Vous pouvez surveiller la progression des mises à jour dans la barre d’état de Visual Studio. Pour résoudre les problèmes ou messages qui s’affichent en raison de la désactivation de certains paramètres IntelliSense, consultez [Résoudre les problèmes liés aux cartes dans le code C et C++](#Troubleshooting).  
  
-   Pour visualiser les dépendances entre tous les fichiers sources et fichiers d’en-tête de votre solution, dans le menu **Architecture** , choisissez **Générer le graphique des fichiers Include**.  
  
     ![Graphique de dépendance pour le code natif](../modeling/media/dependencygraphgeneral-nativecode.png "DependencyGraphGeneral_NativeCode")  
  
-   Pour visualiser les dépendances entre le fichier actuellement ouvert et les fichiers sources et fichiers d’en-tête associés, ouvrez soit le fichier source, soit le fichier d’en-tête. Ouvrez le menu contextuel n’importe où dans le fichier. Choisissez **Générer le graphique des fichiers Include**.  
  
     ![Première&#45;graphique de dépendance de niveau pour le fichier .h](../modeling/media/dependencygraph-native-firstlevel.png "DependencyGraph_Native_FirstLevel")  
  
###  <a name="Troubleshooting"></a> Résoudre les problèmes liés aux cartes dans le code C et C++  
 Ces éléments ne sont pas pris en charge pour le code C et C++ :  
  
- Les types de base n’apparaissent pas sur les cartes qui incluent la hiérarchie parente.  
  
- La plupart des éléments de menu **Affichage** ne sont pas disponibles pour le code C et C++.  
  
  Ces problèmes peuvent se produire quand vous créez des cartes de code pour du code C et C++ :  
  
|**Problème**|**Causes possibles**|**Résolution**|  
|---------------|------------------------|--------------------|  
|Échec de la génération de la carte de code.|Aucun projet de la solution n’a été généré correctement.|Corrigez les erreurs de build qui se sont produites, puis régénérez la carte.|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ne répond pas quand vous essayez de générer une carte de code à partir du menu **Architecture** .|Le fichier de base de données du programme (.pdb) peut être endommagé.<br /><br /> Un fichier .pdb stocke des informations de débogage, telles que des informations sur le type, la méthode et le fichier source.|Régénérez la solution puis recommencez.|  
|Certains paramètres de la base de données de navigation IntelliSense sont désactivés.|Certains paramètres IntelliSense peuvent être désactivés dans la boîte de dialogue [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**Options** .|Activez les paramètres.<br /><br /> Consultez [Options, éditeur de texte, C/C++, avancé](../ide/reference/options-text-editor-c-cpp-advanced.md).|  
|Le message **Méthodes inconnues** s’affiche sur un nœud de méthode.<br /><br /> Ce problème se produit car le nom de la méthode ne peut pas être résolu.|Le fichier binaire peut ne pas avoir de table de réadressage de base.|Activez l’option **/FIXED:NO** dans l’éditeur de liens.<br /><br /> Consultez [/FIXED (Fixed Base Address)](http://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).|  
||Le fichier de base de données du programme (.pdb) peut ne pas être généré.<br /><br /> Un fichier .pdb stocke des informations de débogage, telles que des informations sur le type, la méthode et le fichier source.|Activez l’option **/DEBUG** dans l’éditeur de liens.<br /><br /> Consultez [/DEBUG (Generate Debug Info)](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).|  
||Impossible d’ouvrir ou de localiser le fichier .pdb aux emplacements attendus.|Assurez-vous que le fichier .pdb existe dans les emplacements attendus.|  
||Les informations de débogage ont été supprimées du fichier .pdb.|Si l’option **/PDBSTRIPPED** a été utilisée dans l’éditeur de liens, incluez à la place le fichier .pdb complet.<br /><br /> Consultez [/PDBSTRIPPED (Strip Private Symbols)](http://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|  
||L’appelant n’est pas une fonction ; il correspond à un thunk dans le fichier binaire ou à un pointeur dans la section de données.|Lorsque l’appelant est un thunk, essayez d’utiliser `_declspec(dllimport)` pour éviter le thunk.<br /><br /> Consultez :<br /><br /> -   [Règles générales et Limitations](http://msdn.microsoft.com/library/6c48902d-4259-4761-95d4-e421d69aa050)<br />-   [Importation d’appels de fonction à l’aide de __declspec (dllimport)](http://msdn.microsoft.com/library/6b53c616-0c6d-419a-8e2a-d2fff20510b3)<br />-   [dllexport, dllimport](http://msdn.microsoft.com/library/ff95b645-ef55-4e72-b848-df44657b3208)|  
  
##  <a name="RenderMoreQuickly"></a> Accélérer le rendu des cartes de code  
 Quand vous générez une carte pour la première fois, Visual Studio indexe toutes les dépendances qu’il trouve. Ce processus peut prendre un certain temps, en particulier pour les solutions importantes, mais il améliore les performances ultérieures. Si votre code change, Visual Studio réindexe uniquement le code mis à jour. Pour réduire le temps nécessaire au rendu de la carte, considérez les points suivants :  
  
- [Créez uniquement une carte des dépendances qui vous intéressent.](#SeeSpecificSource)  
  
- Avant de générer la carte pour une solution entière, limitez la portée de la solution.  
  
- Désactivez la génération automatique de la solution à l’aide du bouton **Ignorer la build** situé dans la barre d’outils de la carte de code.  
  
- Désactivez l’ajout automatique d’éléments parents à l’aide du bouton **Inclure les parents** situé dans la barre d’outils de la carte de code.  
  
- Modifiez directement le fichier de la carte de code pour supprimer les nœuds et les liens dont vous n’avez pas besoin. La modification de la carte n’affecte pas le code sous-jacent. Consultez [Personnaliser des cartes de code en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).  
  
  ![Boutons Skip Build et inclure les Parents](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")  
  
  Bien que Visual Studio puisse fonctionner avec 1 Go de mémoire, nous recommandons que votre ordinateur ait au moins 2 Go de mémoire pour éviter des délais importants quand Visual Studio crée l’index de code et génère la carte.  
  
  Quand la propriété **Copier dans le répertoire de sortie** d’un élément de projet a la valeur **Toujours copier**, la création de cartes ou l’ajout d’éléments à une carte à partir de l’Explorateur de solutions peut prendre plus de temps. Les problèmes liés aux builds incrémentielles et à Visual Studio peuvent provoquer la régénération du projet à chaque fois. Pour accroître les performances, remplacez la valeur de cette propriété par **Copier si plus récent** ou `PreserveNewest`. Consultez [Incremental Builds](../msbuild/incremental-builds.md).  
  
  La carte terminée présente uniquement les dépendances pour le code correctement généré. Si des erreurs de build se produisent pour certains composants, ces erreurs apparaissent sur la carte. Assurez-vous qu’un composant est réellement généré et qu’il a des dépendances avant de prendre des décisions architecturales basées sur la carte.  
  
##  <a name="SavingExporting"></a> Partager des cartes de code  
  
### <a name="share-the-map-with-other-visual-studio-users"></a>Partager la carte avec d’autres utilisateurs de Visual Studio  
 Utilisez le menu **Fichier** pour enregistrer la carte.  
  
 - ou -  
  
 Pour enregistrer la carte dans le cadre d’un projet spécifique, dans la barre d’outils de la carte, choisissez **Partager**, puis **Déplacer** \<*CodeMapName*>**.dgml vers**, puis choisissez le projet dans lequel vous souhaitez enregistrer la carte.  
  
 ![Déplacer une carte dans un autre projet](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")  
  
 Visual Studio enregistre la carte en tant que fichier .dgml que vous pouvez partager avec d’autres utilisateurs de Visual Studio Enterprise et de Visual Studio Professional.  
  
> [!NOTE]
>  Avant de partager une carte avec les utilisateurs de Visual Studio Professional, veillez à développer tous les groupes, à afficher les nœuds masqués et les liens entre les groupes, et à récupérer les nœuds supprimés que vous souhaitez afficher sur la carte. Sinon, les utilisateurs ne pourront pas afficher ces éléments.  
>   
>  L’erreur suivante peut se produire quand vous enregistrez une carte se trouvant dans un projet de modélisation ou ayant été copiée à partir d’un projet de modélisation vers un autre emplacement :  
>   
>  « Impossible d’enregistrer *fileName* en dehors du répertoire du projet. Les éléments liés ne sont pas pris en charge. »  
>   
>  Visual Studio affiche l’erreur, mais crée quand même la version enregistrée. Pour éviter cette erreur, créez la carte en dehors du projet de modélisation. Vous pouvez ensuite l’enregistrer à l’emplacement que vous souhaitez. Le fait de copier le fichier vers un autre emplacement de la solution, puis de tenter de l’enregistrer, ne fonctionnera pas.  
  
### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>Exporter la carte en tant qu’image pour pouvoir la copier dans d’autres applications, telles que Microsoft Word ou PowerPoint  
  
1.  Dans la barre d’outils de la carte de code, choisissez **Partager**, **Envoyer par courrier électronique en tant qu’image** ou **Copier l’image**.  
  
2.  Collez l’image dans une autre application.  
  
### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>Exporter la carte en tant que fichier XPS pour pouvoir la voir dans des visionneuses XML ou XAML comme Internet Explorer  
  
1.  Dans la barre d’outils de la carte de code, choisissez **Partager**, **Envoyer par courrier électronique en tant que XPS portable** ou **Enregistrer en tant que XPS portable**.  
  
2.  Accédez à l’emplacement auquel enregistrer le fichier.  
  
3.  Nommez la carte de code. Assurez-vous que le **enregistrer en tant que type** zone est définie sur **fichiers XPS (\*.xps)**. Choisissez **Enregistrer**.  
  
## <a name="what-else-can-i-do"></a>Que puis-je faire d’autre ?  
  
-   [Utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)  
  
-   [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
-   [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md)  
  
-   [Personnaliser des cartes de code en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
