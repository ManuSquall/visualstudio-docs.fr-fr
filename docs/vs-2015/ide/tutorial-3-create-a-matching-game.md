---
title: 'Didacticiel 3 : créer un jeu de combinaisons | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 30ee029fe231202c821c8448d3594192b5ebfdf8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299846"
---
# <a name="tutorial-3-create-a-matching-game"></a>Didacticiel 3 : créer un jeu de combinaisons
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans ce didacticiel, vous générez un jeu de combinaisons dans lequel le joueur doit associer des paires d'icônes masquées. Vous apprenez à :

- stocker des objets, tels que des icônes, dans un objet `List` ;

- utiliser une boucle `foreach` en Visual C# ou une boucle `For Each` en Visual Basic pour effectuer des itérations sur les éléments d'une liste ;

- effectuer le suivi de l'état d'un formulaire à l'aide de variables de référence ;

- générer un gestionnaire d'événements pour réagir aux événements, que vous pouvez utiliser avec plusieurs objets ;

- créer un minuteur qui effectue un calcul à rebours, puis déclenche un événement une seule fois après avoir été démarré.

  Lorsque vous aurez terminé ce didacticiel, votre programme aura l'aspect illustré ci-dessous.

  ![Jeu créé dans ce didacticiel](../ide/media/express-finishedgame.png "Express_FinishedGame") Jeu créé dans ce didacticiel

> [!NOTE]
> Ce didacticiel aborde Visual C# et Visual Basic : ne tenez compte que des informations spécifiques au langage de programmation que vous utilisez.

 Si vous êtes bloqué ou avez des questions liées à la programmation, essayez de publier votre question sur l'un des forums MSDN. Consultez le [Forum Visual Basic](https://social.msdn.microsoft.com/Forums/en-US/home) et [Forum Visual C#](https://social.msdn.microsoft.com/Forums/en-US/home). Des ressources vidéo d'apprentissage efficaces et gratuites sont également à votre disposition. Pour en savoir plus sur la programmation en Visual Basic, consultez [Notions de base de Visual Basic : développement pour les débutants](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Pour en savoir plus sur la programmation en C#, consultez [Notions de base de C# : développement pour les débutants](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Étape 1 : créer un projet et ajouter une table à votre formulaire](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Commencez par créer le projet et ajouter un contrôle `TableLayoutPanel` pour maintenir un bon alignement des contrôles.|
|[Étape 2 : ajouter un objet aléatoire et une liste d’icônes](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Ajoutez un objet `Random` et un objet `List` pour créer une liste d'icônes.|
|[Étape 3 : affecter une icône aléatoire à chaque contrôle Label](../ide/step-3-assign-a-random-icon-to-each-label.md)|Affectez de façon aléatoire les icônes aux contrôles `Label` afin que chaque jeu soit différent.|
|[Étape 4 : ajouter un gestionnaire d’événements Click à chaque contrôle Label](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Ajoutez un gestionnaire d'événements Click pour modifier la couleur du contrôle Label sur lequel clique le joueur.|
|[Étape 5 : ajouter des références de contrôles Label](../ide/step-5-add-label-references.md)|Ajoutez des variables de référence pour suivre les contrôles Label sur lesquels clique le joueur.|
|[Étape 6 : ajouter une minuterie](../ide/step-6-add-a-timer.md)|Ajoutez une horloge au formulaire pour assurer le suivi du temps écoulé dans le jeu.|
|[Étape 7 : garder les paires visibles](../ide/step-7-keep-pairs-visible.md)|Laissez des paires d'icônes visibles, si une paire identique est sélectionnée.|
|[Étape 8 : ajouter une méthode pour vérifier si le joueur a gagné](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Ajoutez une méthode `CheckForWinner()` pour vérifier si le joueur a gagné.|
|[Étape 9 : tester d’autres fonctionnalités](../ide/step-9-try-other-features.md)|Essayez d'autres fonctionnalités (par exemple, la modification des icônes et des couleurs, l'ajout d'une grille et l'ajout de sons). Essayez d'agrandir le plateau et d'ajuster la minuterie.|
