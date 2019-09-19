---
title: 'Étape 9 : Tester d’autres fonctionnalités'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aff87247afb79d62867da9e55f7a059192789d79
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118852"
---
# <a name="step-9-try-other-features"></a>Étape 9 : Tester d’autres fonctionnalités
Pour découvrir d'autres fonctionnalités, essayez de modifier les icônes et les couleurs, d'ajouter une horloge de jeu et d'ajouter des sons. Pour augmenter la difficulté du jeu, essayez d'agrandir la taille du plateau et d'ajuster la minuterie.

Pour télécharger une version complète de l’exemple, consultez [Exemple complet de tutoriel de création d’un jeu de combinaisons](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

## <a name="to-try-other-features"></a>Pour essayer d’autres fonctionnalités

- Remplacez les icônes et les couleurs par d'autres de votre choix.

    > [!TIP]
    > Examinez la propriété [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>) du contrôle Label.

- Ajoutez une horloge de jeu qui relèvera le temps requis par le joueur pour gagner.

    > [!TIP]
    > Pour cela, vous pouvez ajouter une étiquette pour afficher sur le formulaire le temps écoulé au-dessus du <xref:System.Windows.Forms.TableLayoutPanel> et ajouter une autre horloge au formulaire pour relever le temps. Utilisez le code pour démarrer l'horloge lorsque le joueur commence à jouer et arrêter l'horloge lorsque la dernière paire est indiquée.

- Ajoutez un son lorsque le joueur trouve une paire identique, un autre lorsqu'il sélectionne deux icônes différentes et un troisième lorsque le programme masque à nouveau les icônes.

    > [!TIP]
    > Pour émettre des sons, vous pouvez utiliser l'espace de noms <xref:System.Media>. Pour plus d’informations, consultez [Lire des sons dans une application Windows Forms (C#)](http://youtu.be/qOh4ooHg1UU) ou [Comment lire de l’audio dans Visual Basic](http://youtu.be/-4oPDeQrtMs).

- Augmentez la difficulté du jeu en agrandissant la taille du plateau.

    > [!TIP]
    > Vous ne devez pas seulement ajouter des lignes et des colonnes au TableLayoutPanel : vous devez également considérer le nombre d’icônes que vous créez.

- Augmentez la difficulté du jeu en masquant la première icône si le joueur réagit trop lentement et ne choisit pas la deuxième icône dans un délai imparti.

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Si vous êtes bloqué ou avez des questions liées à la programmation, essayez de publier votre question sur l'un des forums MSDN. Consultez le [forum Visual Basic](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral) et le [forum Visual C#](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral).

- Des ressources vidéo d'apprentissage efficaces et gratuites sont à votre disposition. Pour en savoir plus sur la programmation en Visual Basic, consultez [Notions de base de Visual Basic : développement pour grands débutants](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Pour en savoir plus sur la programmation en Visual C#, consultez [Notions de base de C# : développement pour grands débutants](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Pour revenir à l’étape précédente du tutoriel, consultez [Étape 8 : Ajouter une méthode pour vérifier si le joueur a gagné](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
