---
title: 'Tutoriel 3 : Créer un jeu de combinaisons'
ms.date: 11/04/2016
ms.assetid: 525815c8-2845-45e8-be96-100d1f144725
ms.topic: tutorial
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8fafd46561b6a3628989b675b14c493b60da6fe
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118705"
---
# <a name="tutorial-3-create-a-matching-game"></a>Tutoriel 3 : Créer un jeu de combinaisons

Dans ce didacticiel, vous générez un jeu de combinaisons dans lequel le joueur doit associer des paires d'icônes masquées. Vous apprenez à :

- stocker des objets, tels que des icônes, dans un objet <xref:System.Collections.Generic.List%601> ;

- utiliser une boucle `foreach` en Visual C# ou une boucle `For Each` en Visual Basic pour effectuer des itérations sur les éléments d'une liste ;

- effectuer le suivi de l'état d'un formulaire à l'aide de variables de référence ;

- générer un gestionnaire d'événements pour réagir aux événements, que vous pouvez utiliser avec plusieurs objets ;

- créer un minuteur qui effectue un calcul à rebours, puis déclenche un événement une seule fois après avoir été démarré.

Une fois ce tutoriel terminé, votre programme se présente comme dans l’image suivante :

![Jeu créé dans ce didacticiel](../ide/media/express_finishedgame.png)

## <a name="tutorial-links"></a>Liens de tutoriels

Pour télécharger une version complète de l’exemple, consultez [Exemple complet de tutoriel de création d’un jeu de combinaisons](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

> [!NOTE]
> Ce didacticiel aborde Visual C# et Visual Basic : ne tenez compte que des informations spécifiques au langage de programmation que vous utilisez.

Si vous êtes bloqué ou avez des questions liées à la programmation, essayez de publier votre question sur l'un des forums MSDN. Consultez le [forum Visual Basic](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral) et le [forum Visual C#](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral). Des ressources vidéo d'apprentissage efficaces et gratuites sont également à votre disposition. Pour en savoir plus sur la programmation en Visual Basic, consultez [Notions de base de Visual Basic : développement pour grands débutants](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Pour en savoir plus sur la programmation en Visual C#, consultez [Notions de base de C# : développement pour grands débutants](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Étape 1 : Créer un projet et ajouter une table à votre formulaire](../ide/step-1-create-a-project-and-add-a-table-to-your-form.md)|Commencez par créer le projet et ajouter un contrôle `TableLayoutPanel` pour maintenir un bon alignement des contrôles.|
|[Étape 2 : Ajouter un objet aléatoire et une liste d’icônes](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)|Ajoutez un objet `Random` et un objet `List` pour créer une liste d'icônes.|
|[Étape 3 : Affecter une icône aléatoire à chaque étiquette](../ide/step-3-assign-a-random-icon-to-each-label.md)|Affectez de façon aléatoire les icônes aux contrôles `Label` afin que chaque jeu soit différent.|
|[Étape 4 : Ajouter un gestionnaire d’événements Click à chaque étiquette](../ide/step-4-add-a-click-event-handler-to-each-label.md)|Ajoutez un gestionnaire d'événements `Click` pour modifier la couleur de l’étiquette sur laquelle le joueur clique.|
|[Étape 5 : Ajouter des références aux étiquettes](../ide/step-5-add-label-references.md)|Ajoutez des variables de référence pour suivre les contrôles Label sur lesquels clique le joueur.|
|[Étape 6 : Ajouter une minuterie](../ide/step-6-add-a-timer.md)|Ajoutez une horloge au formulaire pour assurer le suivi du temps écoulé dans le jeu.|
|[Étape 7 : Garder les paires visibles](../ide/step-7-keep-pairs-visible.md)|Laissez des paires d'icônes visibles, si une paire identique est sélectionnée.|
|[Étape 8 : Ajouter une méthode pour vérifier si le joueur a gagné](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)|Ajoutez une méthode `CheckForWinner()` pour vérifier si le joueur a gagné.|
|[Étape 9 : Tester d’autres fonctionnalités](../ide/step-9-try-other-features.md)|Essayez d'autres fonctionnalités (par exemple, la modification des icônes et des couleurs, l'ajout d'une grille et l'ajout de sons). Essayez d'agrandir le plateau et d'ajuster la minuterie.|
