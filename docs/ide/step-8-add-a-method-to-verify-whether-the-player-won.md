---
title: 'Étape 8 : Ajouter une méthode pour vérifier si le joueur a gagné'
description: Découvrez comment ajouter une méthode pour déterminer si le joueur a gagné.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 931e39a4f3cf87fe2d147d90f2111c9a9db3faeb
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107297000"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Étape 8 : Ajouter une méthode pour vérifier si le joueur a gagné
Vous avez créé un jeu divertissant, mais il a besoin d'un élément supplémentaire pour être complet. Le jeu doit se terminer en cas de victoire du joueur : vous devez donc ajouter une méthode `CheckForWinner()` pour vérifier si le joueur a gagné.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Pour ajouter une méthode afin de vérifier si le joueur a gagné

1. Ajoutez une méthode `CheckForWinner()` en bas de votre code, sous le gestionnaire d'événements `timer1_Tick()`, comme illustré dans le code suivant.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet10":::

      > [!IMPORTANT]
      > Utilisez le contrôle de langage de programmation en haut à droite de cette page pour afficher l’extrait de code C# ou l’extrait de code Visual Basic.<br><br>![Contrôle du langage de programmation pour Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)     

     La méthode utilise une autre `foreach` boucle en C# ou une `For Each` boucle dans Visual Basic pour parcourir chaque étiquette dans le <xref:System.Windows.Forms.TableLayoutPanel> . Elle utilise l’opérateur d’égalité ( `==` en C# et `=` en Visual Basic) pour vérifier la couleur de l’icône de chaque contrôle Label afin de vérifier s’il correspond à l’arrière-plan. Si les couleurs correspondent, l'icône reste invisible et le joueur n'a pas associé toutes les icônes restantes. Dans ce cas, le programme utilise une instruction `return` pour ignorer le reste de la méthode. Si la boucle parcourt tous les contrôles Label sans exécuter l'instruction `return`, cela signifie que toutes les icônes du formulaire ont été associées. Le programme affiche un MessageBox pour féliciter le joueur d'avoir gagné, puis appelle la méthode `Close()` du formulaire pour arrêter le jeu.

2. Ensuite, appelez la nouvelle méthode `CheckForWinner()` via le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du contrôle Label. Veillez à ce que votre programme vérifie si le joueur a gagné après avoir affiché la seconde icône choisie par le joueur. Recherchez la ligne où vous définissez la couleur de la seconde icône choisie, puis appelez la méthode `CheckForWinner()` juste après, comme cela est illustré dans le code suivant.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet11":::

3. Enregistrez et exécutez le programme. Jouez au jeu et associez toutes les icônes. Lorsque vous gagnez, le programme affiche un **MessageBox** (comme illustré dans la capture d’écran suivante), puis ferme la boîte.

     ![Jeu de combinaisons avec MessageBox](../ide/media/express_tut4step8.png)<br/>
***Jeu de combinaisons** _ _With * ***MessageBox***

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez **[étape 9 : essayer d’autres fonctionnalités](../ide/step-9-try-other-features.md)**.

- Pour revenir à l’étape précédente du tutoriel, consultez [Étape 7 : garder les paires visibles](../ide/step-7-keep-pairs-visible.md).
