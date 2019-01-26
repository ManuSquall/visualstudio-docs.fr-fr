---
title: Cartes de code sont lentes
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: ebdd8809ed4c9ad7079cecd8f28986eb711bc304
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981290"
---
# <a name="improve-performance-for-code-maps"></a>Améliorer les performances pour les cartes de code

Quand vous générez une carte pour la première fois, Visual Studio indexe toutes les dépendances qu’il trouve. Ce processus peut prendre un certain temps, en particulier pour les solutions de grande taille, mais améliore les performances ultérieures. Si votre code change, Visual Studio réindexe uniquement le code mis à jour. Pour réduire le temps nécessaire pour le mappage à la fin du rendu, envisagez les suggestions suivantes :

- [Créez uniquement une carte des dépendances qui vous intéressent.](#create-a-code-map-to-see-specific-dependencies)

- Avant de générer la carte pour une solution entière, limitez la portée de la solution.

- Désactiver la génération automatique de la solution en sélectionnant **Skip Build** sur la barre d’outils de carte de code.

- Désactivez l’ajout automatique d’éléments parents en sélectionnant **inclure les Parents** sur la barre d’outils de carte de code.

   ![Ignorer les boutons Build et Inclure les parents](../modeling/media/codemapsfilterskipbuildicons.png)

- Modifiez directement le fichier de la carte de code pour supprimer les nœuds et les liens dont vous n’avez pas besoin. La modification de la carte n’affecte pas le code sous-jacent. Consultez [Personnaliser des cartes de code en modifiant les fichiers DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

Il peut prendre plus de temps pour la création de cartes ou d’ajouter des éléments à un mappage à partir de **l’Explorateur de solutions** lorsqu’un élément de projet **Copy to Output Directory** propriété est définie sur **toujours copier**. Pour accroître les performances, remplacez la valeur de cette propriété par **Copier si plus récent** ou `PreserveNewest`. Consultez [les builds incrémentielles](../msbuild/incremental-builds.md).

Le mappage terminé montre les dépendances uniquement pour le code généré avec succès. Si des erreurs de build se produisent pour certains composants, ces erreurs apparaissent sur la carte. Assurez-vous qu’un composant est réellement généré et qu’il a des dépendances avant de prendre des décisions architecturales basées sur la carte.