---
title: 'Tutoriel 3 : créer un jeu de combinaisons'
description: Apprenez à créer un jeu de combinaisons, où le joueur doit associer des paires d’icônes masquées.
ms.custom: SEO-VS-2020
ms.date: 10/16/2019
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cfb5a8af72d7c41cdee913ee94c382c57e8cf5dc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971412"
---
# <a name="tutorial-3-create-a-matching-game"></a>Tutoriel 3 : créer un jeu de combinaisons

Dans ce didacticiel, vous générez un jeu de combinaisons dans lequel le joueur doit associer des paires d'icônes masquées.

> [!NOTE]
> Ce didacticiel couvre à la fois C# et Visual Basic. vous devez donc vous concentrer sur les informations spécifiques au langage de programmation que vous utilisez.

Ce didacticiel vous guide tout au long des tâches suivantes :

- stocker des objets, tels que des icônes, dans un objet <xref:System.Collections.Generic.List%601> ;

- Utilisez une `foreach` boucle en C# ou une `For Each` boucle dans Visual Basic pour itérer au sein des éléments d’une liste.

- effectuer le suivi de l'état d'un formulaire à l'aide de variables de référence ;

- générer un gestionnaire d'événements pour réagir aux événements, que vous pouvez utiliser avec plusieurs objets ;

- créer un minuteur qui effectue un calcul à rebours, puis déclenche un événement une seule fois après avoir été démarré.

Lorsque vous avez terminé, votre application doit ressembler à l’image suivante :

![Jeu créé dans ce didacticiel](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Liens de tutoriels

|Titre|Description|
|-----------|-----------------|
|[Étape 1 : Créer un projet et ajouter une table à votre formulaire](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Commencez par créer le projet et ajouter un contrôle `TableLayoutPanel` pour maintenir un bon alignement des contrôles.|
|[Étape 2 : Ajouter un objet aléatoire et une liste d’icônes](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Ajoutez un objet `Random` et un objet `List` pour créer une liste d'icônes.|
|[Étape 3 : Affecter une icône aléatoire à chaque étiquette](../ide/step-3-assign-a-random-icon-to-each-label.md)|Affectez de façon aléatoire les icônes aux contrôles `Label` afin que chaque jeu soit différent.|
|[Étape 4 : Ajouter un gestionnaire d’événements Click à chaque étiquette](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Ajoutez un gestionnaire d'événements `Click` pour modifier la couleur de l’étiquette sur laquelle le joueur clique.|
|[Étape 5 : Ajouter des références aux étiquettes](../ide/step-5-add-label-references.md)|Ajoutez des variables de référence pour suivre les contrôles Label sur lesquels clique le joueur.|
|[Étape 6 : Ajouter un minuteur](../ide/step-6-add-a-timer.md)|Ajoutez une horloge au formulaire pour assurer le suivi du temps écoulé dans le jeu.|
|[Étape 7 : Garder les paires visibles](../ide/step-7-keep-pairs-visible.md)|Laissez des paires d'icônes visibles, si une paire identique est sélectionnée.|
|[Étape 8 : Ajouter une méthode pour vérifier si le joueur a gagné](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Ajoutez une méthode `CheckForWinner()` pour vérifier si le joueur a gagné.|
|[Étape 9 : Tester d’autres fonctionnalités](../ide/step-9-try-other-features.md)|Essayez d'autres fonctionnalités (par exemple, la modification des icônes et des couleurs, l'ajout d'une grille et l'ajout de sons). Essayez d'agrandir le plateau et d'ajuster la minuterie.|

D’autres ressources de formation vidéo gratuites sont également disponibles. Pour en savoir plus sur la programmation en C#, consultez [notions de base de c# : développement pour les débutants](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Pour en savoir plus sur la programmation en Visual Basic, consultez [Notions de base de Visual Basic : développement pour grands débutants](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Étapes suivantes

Pour commencer le didacticiel, commencez à l' **[étape 1 : créer un projet et ajouter une table à votre formulaire](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)**.

## <a name="see-also"></a>Voir aussi

* [Autres didacticiels C#](../get-started/csharp/index.yml)
* [Didacticiels de Visual Basic](../get-started/visual-basic/index.yml)
* [Didacticiels C++](/cpp/get-started/tutorial-console-cpp)