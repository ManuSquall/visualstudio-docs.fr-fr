---
title: Structurer votre solution de modélisation
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: a18dbf13929163e6f4a0f3d123fe393a188d0830
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31953084"
---
# <a name="structure-your-modeling-solution"></a>Structurer votre solution de modélisation
Pour utiliser efficacement des modèles dans un projet de développement, les membres de l'équipe doivent pouvoir travailler sur des modèles de différentes parties du projet en même temps. Cette rubrique suggère comment diviser l'application en différentes parties correspondant aux couches d'un diagramme de couche global.

 Pour démarrer rapidement un projet ou un sous-projet, il est utile de disposer d'un modèle de projet qui suit la structure du projet que vous avez choisie. Cette rubrique décrit comment créer et utiliser un tel modèle.

 Cette rubrique part du principe que votre projet est suffisamment grand pour nécessiter la participation de plusieurs membres d'équipe et qu'il peut même comporter plusieurs équipes. Le code et les modèles du projet sont stockés dans un système de contrôle de code source tel que [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Au moins quelques membres de l'équipe utilisent Visual Studio pour développer des modèles et les autres membres de l'équipe peuvent visualiser ces modèles à l'aide d'autres versions de Visual Studio.

 Pour connaître les versions de Visual Studio prend en charge chaque fonctionnalité de l’outil et de modélisation, consultez [prise en charge de la Version pour l’architecture et les outils de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Structure de la solution
 Dans un projet de taille moyenne ou grande, la structure de l'équipe est basée sur celle de l'application. Chaque équipe utilise une solution Visual Studio.

#### <a name="to-divide-an-application-into-layers"></a>Pour diviser une application en couches

1.  Vous devez baser la structure de vos solutions sur la structure de votre application, qu'il s'agisse d'une application web, d'une application de service ou d'une application de bureau. Diverses architectures courantes est décrite dans [Archetypes le Guide d’Architecture de Microsoft Application-Application](http://go.microsoft.com/fwlink/?LinkId=196681).

2.  Créez une solution [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], que nous appellerons la solution Architecture. Nous l'utiliserons pour créer la conception globale du système. Elle contiendra des modèles, mais pas de code.

     Ajoutez un diagramme de dépendance à cette solution. Sur le diagramme de dépendances, dessinez l’architecture choisie pour votre application. Par exemple, le diagramme peut comporter les couches suivantes et les dépendances entre elles : Présentation, Logique métier et Données.

4.  Créer une solution Visual Studio distincte pour chaque couche dans le diagramme d’Architecture de dépendance.

     Vous utiliserez ces solutions pour développer le code des couches.

5.  Créer des modèles qui représenteront les conceptions des couches et les concepts qui sont communes à toutes les couches. Réorganisez les modèles pour qu'ils puissent tous être vus à partir de la solution Architecture et pour que les modèles pertinents puissent être vus à partir de chaque couche.

     Vous pouvez pour cela appliquer l'une des procédures suivantes. La première approche crée un projet de modélisation distinct pour chaque couche, tandis que la seconde crée un projet de modélisation unique partagé entre les couches.

    ###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Pour utiliser un projet de modélisation distinct pour chaque couche

    1.  Créez un projet de modélisation dans chaque solution de couche.

         Ce modèle contient les diagrammes qui décrivent la configuration requise et la conception de cette couche. Il peut également contenir des diagrammes de dépendance qui affichent des couches imbriquées.

         Vous avez maintenant un modèle pour chaque couche, plus un modèle pour l'architecture de l'application. Chaque modèle est contenu dans sa propre solution. Cela permet aux membres de l'équipe de travailler sur les couches en même temps.

    2.  Ajoutez le projet de modélisation de chaque solution de couche à la solution Architecture. Pour cela, ouvrez la solution Architecture. Dans l’Explorateur de solutions, cliquez sur le nœud solution, pointez sur Ajouter, puis cliquez sur **projet existant**. Accédez au projet de modélisation (.modelproj) dans une solution de couche.

         Chaque modèle est maintenant visible dans deux solutions : sa solution d'origine et la solution Architecture.

    3.  Le projet de modélisation de chaque couche, ajoutez un diagramme de dépendances. Démarrez avec une copie du diagramme d’Architecture de la dépendance. Vous pouvez supprimer les parties qui ne sont pas des dépendances du diagramme de dépendance.

         Vous pouvez également ajouter des diagrammes de dépendance qui représentent la structure détaillée de cette couche.

         Ces diagrammes servent à valider le code développé dans cette couche.

    4.  Dans la solution Architecture, modifiez les spécifications et les modèles de conception de toutes les couches à l'aide de Visual Studio.

         Dans chaque solution de couche, développez le code de cette couche, en faisant référence au modèle. Si effectuer le développement sans utiliser le même ordinateur pour mettre à jour le modèle ne vous pose pas de problème, vous pouvez lire le modèle et développer le code à l'aide de versions de Visual Studio qui ne peuvent pas créer de modèles. Vous pouvez également générer le code à partir du modèle dans ces versions.

     Cette méthode garantit qu'aucune interférence ne sera provoquée par les développeurs qui modifient les modèles de couche en même temps.

     Toutefois, les modèles étant distincts, il est difficile de faire référence à des concepts communs. Chaque modèle doit avoir sa propre copie des éléments dont il dépend et qui proviennent d'autres couches et de l'architecture. Le diagramme de dépendances dans chaque couche doit être synchronisé avec le diagramme d’Architecture de dépendance. Il est difficile de maintenir la synchronisation quand ces éléments changent, bien que vous puissiez développer des outils pour cela.

    ###### <a name="to-use-a-separate-package-for-each-layer"></a>Pour utiliser un package distinct pour chaque couche

    1.  Dans la solution de chaque couche, ajoutez le projet de modélisation Architecture. Dans l’Explorateur de solutions, cliquez sur le nœud solution, pointez sur **ajouter**, puis cliquez sur **projet existant**. Le projet de modélisation unique est maintenant accessible à partir de chaque solution : le projet Architecture et le projet de développement de chaque couche.

    2.  Dans le modèle partagé, créez un package pour chaque couche : dans l’Explorateur de solutions, sélectionnez le projet de modélisation. Dans l’Explorateur de modèles UML, le nœud racine du modèle avec le bouton droit, pointez sur **ajouter**, puis cliquez sur **Package**.

         Chaque package contiendra des diagrammes qui décrivent la configuration requise et la conception de la couche correspondante.

    3.  Si nécessaire, ajouter des diagrammes de dépendance local pour la structure interne de chaque couche.

     Cette méthode permet aux éléments de conception de chaque couche de faire directement référence aux éléments des couches et de l'architecture commune dont ils dépendent.

     Bien que le travail simultané sur différents packages puisse provoquer des conflits, ils sont relativement faciles à gérer car les packages sont stockés dans des fichiers distincts.

## <a name="creating-architecture-templates"></a>Création de modèles d'architecture
 Dans la pratique, vous ne créerez pas toutes vos solutions Visual Studio en même temps, mais vous les ajouterez à mesure que le projet progresse. Vous utiliserez aussi probablement la même structure de solution dans les projets ultérieurs.  Pour vous aider à créer des solutions rapidement, vous pouvez créer un modèle de solution ou de projet. Vous pouvez capturer le modèle dans une Extension d'intégration Visual Studio (VSIX) pour faciliter sa distribution et son installation sur d'autres ordinateurs.

 Par exemple, si vous utilisez fréquemment des solutions qui ont des couches Présentation, Logique métier et Données, vous pouvez configurer un modèle qui crée des solutions ayant cette structure.

#### <a name="to-create-a-solution-template"></a>Pour créer un modèle de solution

1.  [Téléchargez et installez l’Assistant Exportation de modèle](http://go.microsoft.com/fwlink/?LinkId=196686), si vous ne le n'avez pas déjà fait.

2.  Créez la structure de solution que vous souhaitez utiliser comme point de départ pour de futurs projets.

3.  Dans le menu **Fichier** , cliquez sur **Export Template as VSIX**. Le **Export Template as VSIX Assistant** s’ouvre.

4.  Suivez les instructions de l'Assistant et sélectionnez les projets que vous souhaitez inclure dans le modèle, fournissez un nom et une description pour le modèle et spécifiez un emplacement de sortie.

> [!NOTE]
>  Le contenu de cette rubrique est tiré du document Visual Studio Architecture Tooling Guidance, rédigé par les Visual Studio ALM Rangers, qui est une collaboration entre des MVP (Most Valued Professionals), les Services Microsoft et les rédacteurs et l'équipe de produit Visual Studio. [Cliquez ici pour télécharger le package complet du Guide.](http://go.microsoft.com/fwlink/?LinkID=191984)

## <a name="related-materials"></a>Documents associés
 [Organiser et gérer vos modèles](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-9-Organizing-and-Managing-Your-Models/) - vidéo par Clint Edmondson.

 [Guide des outils d’Architecture de Studio Visual](../modeling/visual-studio-architecture-tooling-guidance.md) -plus d’instructions sur la gestion des modèles dans une équipe

## <a name="see-also"></a>Voir aussi

- [Utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md)
