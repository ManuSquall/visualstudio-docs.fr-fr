---
title: Les cartes de code sont lentes
ms.date: 05/16/2018
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8b3f889661cf0d1c775cd80dad61a92c3f5b60a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654175"
---
# <a name="improve-performance-for-code-maps"></a>Améliorer les performances des cartes de code

Quand vous générez une carte pour la première fois, Visual Studio indexe toutes les dépendances qu’il trouve. Ce processus peut prendre un certain temps, en particulier pour les solutions volumineuses, mais il améliore les performances ultérieures. Si votre code change, Visual Studio réindexe uniquement le code mis à jour. Pour réduire le temps nécessaire au rendu de la carte pour terminer, tenez compte des suggestions suivantes :

- Créez uniquement une carte des dépendances qui vous intéressent.

- Avant de générer la carte pour une solution entière, limitez la portée de la solution.

- Désactivez la génération automatique pour la solution en sélectionnant **ignorer la génération** dans la barre d’outils de la carte de code.

- Désactivez l’ajout automatique d’éléments parents en sélectionnant **inclure les parents** dans la barre d’outils de la carte de code.

   ![Ignorer les boutons Build et Inclure les parents](../modeling/media/codemapsfilterskipbuildicons.png)

- Modifiez directement le fichier de la carte de code pour supprimer les nœuds et les liens dont vous n’avez pas besoin. La modification de la carte n’affecte pas le code sous-jacent. Consultez [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Il peut être nécessaire de créer des mappages ou d’ajouter des éléments à une carte à partir de **Explorateur de solutions** lorsque la propriété copier **dans le répertoire de sortie** d’un élément de projet a la valeur **toujours copier**. Pour accroître les performances, remplacez la valeur de cette propriété par **Copier si plus récent** ou `PreserveNewest`. Consultez [Builds incrémentielles](../msbuild/incremental-builds.md).

Le mappage terminé affiche uniquement les dépendances pour le code correctement généré. Si des erreurs de build se produisent pour certains composants, ces erreurs apparaissent sur la carte. Assurez-vous qu’un composant est réellement généré et qu’il a des dépendances avant de prendre des décisions architecturales basées sur la carte.