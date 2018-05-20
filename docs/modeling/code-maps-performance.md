---
title: Cartes de code sont lentes
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 2dece1e63fffdba67678422ad9241babc63b7abd
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="improve-performance-for-code-maps"></a>Améliorer les performances des cartes de code

Quand vous générez une carte pour la première fois, Visual Studio indexe toutes les dépendances qu’il trouve. Ce processus peut prendre un certain temps, en particulier pour les solutions volumineuses, mais améliore les performances ultérieures. Si votre code change, Visual Studio réindexe uniquement le code mis à jour. Pour réduire le temps nécessaire à la carte pour terminer le rendu, tenez compte des suggestions suivantes :

- [Mapper que les dépendances qui vous intéressent.](#create-a-code-map-to-see-specific-dependencies)

- Avant de générer la carte pour une solution entière, limitez la portée de la solution.

- Désactiver la génération automatique de la solution en sélectionnant **Skip Build** sur la barre d’outils de carte de code.

- Désactivez l’ajout automatique d’éléments parents en sélectionnant **inclure les Parents** sur la barre d’outils de carte de code.

   ![Ignorer les boutons Build et Inclure les parents](../modeling/media/codemapsfilterskipbuildicons.png)

- Modifiez directement le fichier de la carte de code pour supprimer les nœuds et les liens dont vous n’avez pas besoin. La modification de la carte n’affecte pas le code sous-jacent. Consultez [Personnaliser des cartes de code en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Il peut prendre plus de temps pour créer des cartes ou d’ajouter des éléments à un mappage à partir de **l’Explorateur de solutions** lorsqu’un élément de projet **copier dans le répertoire de sortie** est définie sur **toujours copier**. Pour accroître les performances, remplacez la valeur de cette propriété par **Copier si plus récent** ou `PreserveNewest`. Consultez [générations incrémentielles](../msbuild/incremental-builds.md).

Le mappage terminé indique les dépendances que pour du code généré avec succès. Si des erreurs de build se produisent pour certains composants, ces erreurs apparaissent sur la carte. Assurez-vous qu’un composant est réellement généré et qu’il a des dépendances avant de prendre des décisions architecturales basées sur la carte.