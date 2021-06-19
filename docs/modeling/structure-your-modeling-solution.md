---
title: Structurer votre solution de modélisation
description: Découvrez un schéma de modélisation pour diviser l’application en différentes parties qui correspondent aux couches dans un diagramme de couche global.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 54275c55d3d7a80dc2df1721585bc6c39ba8b06e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385485"
---
# <a name="structure-your-modeling-solution"></a>Structurer votre solution de modélisation

Pour utiliser efficacement des modèles dans un projet de développement, les membres de l'équipe doivent pouvoir travailler sur des modèles de différentes parties du projet en même temps. Cette rubrique suggère comment diviser l'application en différentes parties correspondant aux couches d'un diagramme de couche global.

Pour démarrer rapidement un projet ou un sous-projet, il est utile de disposer d'un modèle de projet qui suit la structure du projet que vous avez choisie. Cette rubrique décrit comment créer et utiliser un tel modèle.

Cette rubrique part du principe que votre projet est suffisamment grand pour nécessiter la participation de plusieurs membres d'équipe et qu'il peut même comporter plusieurs équipes. Le code et les modèles du projet sont stockés dans un système de contrôle de code source tel que [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Au moins quelques membres de l'équipe utilisent Visual Studio pour développer des modèles et les autres membres de l'équipe peuvent visualiser ces modèles à l'aide d'autres versions de Visual Studio.

Pour connaître les versions de Visual Studio qui prennent en charge chaque outil et chaque fonctionnalité de modélisation, consultez [prise en charge des versions pour les outils d’architecture et de modélisation](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="solution-structure"></a>Structure de la solution

Dans un projet de taille moyenne ou grande, la structure de l'équipe est basée sur celle de l'application. Chaque équipe utilise une solution Visual Studio.

### <a name="to-divide-an-application-into-layers"></a>Pour diviser une application en couches

1. Vous devez baser la structure de vos solutions sur la structure de votre application, qu'il s'agisse d'une application web, d'une application de service ou d'une application de bureau. Une série d’architectures courantes est présentée dans [application archétypes dans le Guide de l’architecture des applications Microsoft](/previous-versions/msp-n-p/ee658107(v=pandp.10)).

2. Créez une solution Visual Studio, que nous appellerons la solution d’architecture. Nous l'utiliserons pour créer la conception globale du système. Elle contiendra des modèles, mais pas de code.

   Ajoutez un diagramme de dépendances à cette solution. Sur le diagramme de dépendances, dessinez l’architecture que vous avez choisie pour votre application. Par exemple, le diagramme peut comporter les couches suivantes et les dépendances entre elles : Présentation, Logique métier et Données.

4. Créez une solution Visual Studio distincte pour chaque couche dans le diagramme de dépendance d’architecture.

   Vous utiliserez ces solutions pour développer le code des couches.

5. Créez des modèles qui représentent les conceptions des couches et les concepts qui sont communs à toutes les couches. Réorganisez les modèles pour qu'ils puissent tous être vus à partir de la solution Architecture et pour que les modèles pertinents puissent être vus à partir de chaque couche.

   Vous pouvez pour cela appliquer l'une des procédures suivantes. La première approche crée un projet de modélisation distinct pour chaque couche, tandis que la seconde crée un projet de modélisation unique partagé entre les couches.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Utiliser un projet de modélisation distinct pour chaque couche

1. Créez un projet de modélisation dans chaque solution de couche.

   Ce modèle contient des diagrammes qui décrivent les exigences et la conception de cette couche. Il peut également contenir des diagrammes de dépendances qui affichent des couches imbriquées.

   Vous avez maintenant un modèle pour chaque couche, plus un modèle pour l'architecture de l'application. Chaque modèle est contenu dans sa propre solution. Cela permet aux membres de l'équipe de travailler sur les couches en même temps.

2. Ajoutez le projet de modélisation de chaque solution de couche à la solution Architecture. Pour cela, ouvrez la solution Architecture. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution, pointez sur Ajouter, puis cliquez sur **projet existant**. Accédez au projet de modélisation (.modelproj) dans une solution de couche.

   Chaque modèle est maintenant visible dans deux solutions : sa solution d'origine et la solution Architecture.

3. Ajoutez un diagramme de dépendance au projet de modélisation de chaque couche. Commencez par une copie du diagramme de dépendance d’architecture. Vous pouvez supprimer des parties qui ne sont pas des dépendances du diagramme de dépendances.

   Vous pouvez également ajouter des diagrammes de dépendance qui représentent la structure détaillée de cette couche.

   Ces diagrammes servent à valider le code développé dans cette couche.

4. Dans la solution Architecture, modifiez les spécifications et les modèles de conception de toutes les couches à l'aide de Visual Studio.

   Dans chaque solution de couche, développez le code de cette couche, en faisant référence au modèle. Si effectuer le développement sans utiliser le même ordinateur pour mettre à jour le modèle ne vous pose pas de problème, vous pouvez lire le modèle et développer le code à l'aide de versions de Visual Studio qui ne peuvent pas créer de modèles. Vous pouvez également générer le code à partir du modèle dans ces versions.

   Cette méthode garantit qu'aucune interférence ne sera provoquée par les développeurs qui modifient les modèles de couche en même temps.

   Toutefois, les modèles étant distincts, il est difficile de faire référence à des concepts communs. Chaque modèle doit avoir sa propre copie des éléments dont il dépend et qui proviennent d'autres couches et de l'architecture. Le diagramme de dépendance de chaque couche doit être synchronisé avec le diagramme de dépendance d’architecture. Il est difficile de maintenir la synchronisation quand ces éléments changent, bien que vous puissiez développer des outils pour cela.

#### <a name="use-a-separate-package-for-each-layer"></a>Utiliser un package distinct pour chaque couche

1. Dans la solution de chaque couche, ajoutez le projet de modélisation Architecture. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de la solution, pointez sur **Ajouter**, puis cliquez sur **projet existant**. Le projet de modélisation unique est maintenant accessible à partir de chaque solution : le projet Architecture et le projet de développement de chaque couche.

2. Dans le modèle partagé, créez un package pour chaque couche : dans **Explorateur de solutions**, sélectionnez le projet de modélisation. Dans l' **Explorateur de modèles UML**, cliquez avec le bouton droit sur le nœud racine du modèle, pointez sur **Ajouter**, puis cliquez sur **package**.

   Chaque package contient des diagrammes qui décrivent les exigences et la conception de la couche correspondante.

3. Si nécessaire, ajoutez des diagrammes de dépendances locaux pour la structure interne de chaque couche.

   Cette méthode permet aux éléments de conception de chaque couche de faire directement référence aux éléments des couches et de l'architecture commune dont ils dépendent.

   Bien que le travail simultané sur différents packages puisse provoquer des conflits, ils sont relativement faciles à gérer car les packages sont stockés dans des fichiers distincts.

## <a name="create-architecture-templates"></a>Créer des modèles d’architecture

Dans la pratique, vous ne créez pas toutes vos solutions Visual Studio en même temps, mais vous les ajoutez à mesure que le projet progresse. Vous utiliserez probablement également la même structure de solution dans les futurs projets. Pour vous aider à créer des solutions rapidement, vous pouvez créer un modèle de solution ou de projet. Vous pouvez capturer le modèle dans une Extension d'intégration Visual Studio (VSIX) pour faciliter sa distribution et son installation sur d'autres ordinateurs.

Par exemple, si vous utilisez fréquemment des solutions qui ont des couches Présentation, Logique métier et Données, vous pouvez configurer un modèle qui crée des solutions ayant cette structure.

### <a name="to-create-a-solution-template"></a>Pour créer un modèle de solution

1. [Téléchargez et installez l’Assistant exportation de modèle](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ExportTemplateWizard).

2. Créez la structure de solution que vous souhaitez utiliser comme point de départ pour de futurs projets.

3. Dans le menu **Fichier** , cliquez sur **Export Template as VSIX**.

   L' **Assistant exportation de modèle en tant que VSIX** s’ouvre.

4. Suivez les instructions de l'Assistant et sélectionnez les projets que vous souhaitez inclure dans le modèle, fournissez un nom et une description pour le modèle et spécifiez un emplacement de sortie.

## <a name="watch-a-video"></a>Regarder une vidéo

[Organiser et gérer vos modèles](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Voir aussi

- [Utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md)
