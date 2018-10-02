---
title: Structurer votre solution de modélisation | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 16
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 96f545c980cd49c6f70c45f3ee7fc80be3a25421
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505625"
---
# <a name="structure-your-modeling-solution"></a>Structurer votre solution de modélisation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [structurer votre solution de modélisation](https://docs.microsoft.com/visualstudio/modeling/structure-your-modeling-solution).  
  
Pour utiliser efficacement des modèles dans un projet de développement, les membres de l'équipe doivent pouvoir travailler sur des modèles de différentes parties du projet en même temps. Cette rubrique suggère comment diviser l'application en différentes parties correspondant aux couches d'un diagramme de couche global.  
  
 Pour démarrer rapidement un projet ou un sous-projet, il est utile de disposer d'un modèle de projet qui suit la structure du projet que vous avez choisie. Cette rubrique décrit comment créer et utiliser un tel modèle.  
  
 Cette rubrique part du principe que votre projet est suffisamment grand pour nécessiter la participation de plusieurs membres d'équipe et qu'il peut même comporter plusieurs équipes. Le code et les modèles du projet sont stockés dans un système de contrôle de code source tel que [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. Au moins quelques membres de l'équipe utilisent Visual Studio pour développer des modèles et les autres membres de l'équipe peuvent visualiser ces modèles à l'aide d'autres versions de Visual Studio.  
  
 Pour connaître les versions de Visual Studio prennent en charge chaque outil et fonctionnalité de modélisation, consultez [versions prises en charge pour l’architecture et les outils de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="solution-structure"></a>Structure de la solution  
 Dans un projet de taille moyenne ou grande, la structure de l'équipe est basée sur celle de l'application. Chaque équipe utilise une solution Visual Studio.  
  
#### <a name="to-divide-an-application-into-layers"></a>Pour diviser une application en couches  
  
1.  Vous devez baser la structure de vos solutions sur la structure de votre application, qu'il s'agisse d'une application web, d'une application de service ou d'une application de bureau. Diverses architectures courantes est abordée dans [Archétypes d’Application dans le Guide d’Architecture Microsoft Application](http://go.microsoft.com/fwlink/?LinkId=196681).  
  
2.  Créez une solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], que nous appellerons la solution Architecture. Nous l'utiliserons pour créer la conception globale du système. Elle contiendra des modèles, mais pas de code.  
  
     Ajoutez un diagramme de couche à cette solution. Sur le diagramme de couche, dessinez l'architecture que vous avez choisie pour votre application. Par exemple, le diagramme peut comporter les couches suivantes et les dépendances entre elles : Présentation, Logique métier et Données.  
  
     Vous pouvez créer le diagramme de couche et une nouvelle solution Visual Studio en même temps à l’aide de la **nouveau UML ou diagramme de couche** commande sur le **Architecture** menu.  
  
3.  Ajoutez au modèle Architecture des diagrammes UML qui représentent les concepts métier importants et utilisez des cas d'usage auxquels il est fait référence dans la conception de toutes les couches.  
  
4.  Créez une solution Visual Studio distincte pour chaque couche dans le diagramme de couche Architecture.  
  
     Vous utiliserez ces solutions pour développer le code des couches.  
  
5.  Créez des modèles UML qui représenteront les conceptions des couches et les concepts qui sont communs à toutes les couches. Réorganisez les modèles pour qu'ils puissent tous être vus à partir de la solution Architecture et pour que les modèles pertinents puissent être vus à partir de chaque couche.  
  
     Vous pouvez pour cela appliquer l'une des procédures suivantes. La première approche crée un projet de modélisation distinct pour chaque couche, tandis que la seconde crée un projet de modélisation unique partagé entre les couches.  
  
    ###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Pour utiliser un projet de modélisation distinct pour chaque couche  
  
    1.  Créez un projet de modélisation dans chaque solution de couche.  
  
         Ce modèle contiendra des diagrammes UML décrivant les spécifications et la conception de cette couche. Il peut aussi contenir des diagrammes de couche qui montrent des couches imbriquées.  
  
         Vous avez maintenant un modèle pour chaque couche, plus un modèle pour l'architecture de l'application. Chaque modèle est contenu dans sa propre solution. Cela permet aux membres de l'équipe de travailler sur les couches en même temps.  
  
    2.  Ajoutez le projet de modélisation de chaque solution de couche à la solution Architecture. Pour cela, ouvrez la solution Architecture. Dans l’Explorateur de solutions, cliquez sur le nœud de solution, pointez sur Ajouter, puis cliquez sur **projet existant**. Accédez au projet de modélisation (.modelproj) dans une solution de couche.  
  
         Chaque modèle est maintenant visible dans deux solutions : sa solution d'origine et la solution Architecture.  
  
    3.  Ajoutez un diagramme de couche au projet de modélisation de chaque couche. Commencez avec une copie du diagramme de couche Architecture. Vous pouvez supprimer les parties qui ne sont pas des dépendances du diagramme de couche.  
  
         Vous pouvez aussi ajouter des diagrammes de couche qui représentent la structure détaillée de cette couche.  
  
         Ces diagrammes servent à valider le code développé dans cette couche.  
  
    4.  Dans la solution Architecture, modifiez les spécifications et les modèles de conception de toutes les couches à l'aide de Visual Studio.  
  
         Dans chaque solution de couche, développez le code de cette couche, en faisant référence au modèle. Si effectuer le développement sans utiliser le même ordinateur pour mettre à jour le modèle ne vous pose pas de problème, vous pouvez lire le modèle et développer le code à l'aide de versions de Visual Studio qui ne peuvent pas créer de modèles. Vous pouvez également générer le code à partir du modèle dans ces versions.  
  
     Cette méthode garantit qu'aucune interférence ne sera provoquée par les développeurs qui modifient les modèles de couche en même temps.  
  
     Toutefois, les modèles étant distincts, il est difficile de faire référence à des concepts communs. Chaque modèle doit avoir sa propre copie des éléments dont il dépend et qui proviennent d'autres couches et de l'architecture. Le diagramme de couche de chaque couche doit être synchronisé avec le diagramme de couche Architecture. Il est difficile de maintenir la synchronisation quand ces éléments changent, bien que vous puissiez développer des outils pour cela.  
  
    ###### <a name="to-use-a-separate-package-for-each-layer"></a>Pour utiliser un package distinct pour chaque couche  
  
    1.  Dans la solution de chaque couche, ajoutez le projet de modélisation Architecture. Dans l’Explorateur de solutions, cliquez sur le nœud de solution, pointez sur **ajouter**, puis cliquez sur **projet existant**. Le projet de modélisation unique est maintenant accessible à partir de chaque solution : le projet Architecture et le projet de développement de chaque couche.  
  
    2.  Dans le modèle UML partagé, créez un package pour chaque couche : dans l'Explorateur de solutions, sélectionnez le projet de modélisation. Dans l’Explorateur de modèles UML, le nœud racine du modèle avec le bouton droit, pointez sur **ajouter**, puis cliquez sur **Package**.  
  
         Chaque package contiendra des diagrammes UML décrivant les spécifications et la conception de la couche correspondante.  
  
    3.  Si nécessaire, ajoutez des diagrammes de couche locale pour la structure interne de chaque couche.  
  
     Cette méthode permet aux éléments de conception de chaque couche de faire directement référence aux éléments des couches et de l'architecture commune dont ils dépendent.  
  
     Bien que le travail simultané sur différents packages puisse provoquer des conflits, ils sont relativement faciles à gérer car les packages sont stockés dans des fichiers distincts. La difficulté majeure est due à la suppression d'un élément qui est référencé à partir d'un package dépendant. Pour plus d’informations, consultez [gérer des modèles et des diagrammes sous contrôle de version](../modeling/manage-models-and-diagrams-under-version-control.md).  
  
## <a name="creating-architecture-templates"></a>Création de modèles d'architecture  
 Dans la pratique, vous ne créerez pas toutes vos solutions Visual Studio en même temps, mais vous les ajouterez à mesure que le projet progresse. Vous utiliserez aussi probablement la même structure de solution dans les projets ultérieurs.  Pour vous aider à créer des solutions rapidement, vous pouvez créer un modèle de solution ou de projet. Vous pouvez capturer le modèle dans une Extension d'intégration Visual Studio (VSIX) pour faciliter sa distribution et son installation sur d'autres ordinateurs.  
  
 Par exemple, si vous utilisez fréquemment des solutions qui ont des couches Présentation, Logique métier et Données, vous pouvez configurer un modèle qui crée des solutions ayant cette structure.  
  
#### <a name="to-create-a-solution-template"></a>Pour créer un modèle de solution  
  
1.  [Téléchargez et installez l’Assistant Exportation de modèle](http://go.microsoft.com/fwlink/?LinkId=196686), si vous ne le n'avez pas déjà fait.  
  
2.  Créez la structure de solution que vous souhaitez utiliser comme point de départ pour de futurs projets.  
  
3.  Dans le menu **Fichier** , cliquez sur **Export Template as VSIX**. Le **Export Template as VSIX Wizard** s’ouvre.  
  
4.  Suivez les instructions de l'Assistant et sélectionnez les projets que vous souhaitez inclure dans le modèle, fournissez un nom et une description pour le modèle et spécifiez un emplacement de sortie.  
  
> [!NOTE]
>  Le contenu de cette rubrique est tiré du document Visual Studio Architecture Tooling Guidance, rédigé par les Visual Studio ALM Rangers, qui est une collaboration entre des MVP (Most Valued Professionals), les Services Microsoft et les rédacteurs et l'équipe de produit Visual Studio. [Cliquez ici pour télécharger le package d’instructions complète.](http://go.microsoft.com/fwlink/?LinkID=191984)  
  
## <a name="related-materials"></a>Documents associés  
 [Organiser et gérer vos modèles](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-9-Organizing-and-Managing-Your-Models/) - vidéo par Clint Edmondson.  
  
 [Visual Studio Architecture Tooling Guidance](../modeling/visual-studio-architecture-tooling-guidance.md) – conseils supplémentaires sur la gestion des modèles dans une équipe  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer des modèles et des diagrammes sous contrôle de version](../modeling/manage-models-and-diagrams-under-version-control.md)   
 [Utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md)



