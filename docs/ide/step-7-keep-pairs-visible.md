---
title: 'Étape 7 : garder les paires visibles'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e27a5378aacec6af4ca07f13242f24bd665a762e
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747852"
---
# <a name="step-7-keep-pairs-visible"></a>Étape 7 : garder les paires visibles
Le jeu fonctionne correctement tant que le joueur se contente de choisir des paires d'icônes qui ne correspondent pas. Voyons ce qui doit se produire lorsque le joueur choisit une paire d'icônes identiques. Au lieu de faire disparaître les icônes en activant le minuteur (à l'aide de la méthode <xref:System.Windows.Forms.Timer.Start>), le jeu doit se réinitialiser pour arrêter le suivi de tous les contrôles Label à l'aide des variables de référence `firstClicked` et `secondClicked`, sans réinitialiser les couleurs des deux contrôles Label choisis.

## <a name="to-keep-pairs-visible"></a>Pour garder des paires visibles

1.  Ajoutez l'instruction `if` suivante à la méthode de gestionnaire d'événements `label_Click()`, vers la fin du code, juste au-dessus de l'instruction où vous démarrez le minuteur. Examinez attentivement le code lorsque vous l'ajoutez au programme. Analysez son fonctionnement.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

     La première ligne de l'instruction `if` que vous venez d'ajouter vérifie si l'icône du premier contrôle Label choisi par le joueur est la même que l'icône du deuxième contrôle Label. Si les icônes sont identiques, le programme exécute les trois instructions entre les accolades en C# ou les trois instructions dans l'instruction `if` en Visual Basic. Les deux premières instructions réinitialisent les variables de référence `firstClicked` et `secondClicked` pour arrêter le suivi des différents contrôles Label. (Vous pouvez identifier ces deux instructions dans le gestionnaire d'événements <xref:System.Windows.Forms.Timer.Tick> de la minuterie.) La troisième instruction est une instruction `return`, qui indique au programme d'ignorer le reste des instructions dans la méthode et de ne pas les exécuter.

     Si vous programmez en Visual C#, vous aurez éventuellement remarqué qu'une partie du code utilise un seul signe égal (`=`), alors que d'autres instructions en utilisent deux (`==`). Examinez pourquoi `=` est utilisé dans certains cas et `==` dans d'autres.

     Cet exemple montre bien la différence entre les deux cas. Examinez attentivement le code entre parenthèses dans l'instruction `if`.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Analysez ensuite attentivement la première instruction dans le bloc de code après l'instruction `if`.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     La première de ces deux instructions vérifie si deux icônes sont identiques. Étant donné que deux valeurs sont comparées, le programme Visual C# utilise l'opérateur d'égalité `==`. En fait, la deuxième instruction modifie la valeur (appelée *assignation*) en affectant la valeur `null` à la variable de référence `firstClicked` pour la réinitialiser. C'est la raison pour laquelle elle utilise plutôt l'opérateur d'assignation `=`. Visual C# utilise `=` pour définir des valeurs et `==` pour les comparer. Le langage Visual Basic utilise `=` pour l'affectation et la comparaison des variables.

2.  Enregistrez et exécutez le programme, puis commencez à choisir des icônes sur le formulaire. Si vous choisissez une paire qui ne correspond pas, l'événement Tick du minuteur se déclenche et les deux icônes disparaissent. Si vous choisissez une paire d'icônes identiques, la nouvelle instruction `if` s'exécute et l'instruction return indique à la méthode d'ignorer le code qui démarre le minuteur. De cette façon, les icônes restent visibles, comme le montre la figure ci-dessous.

     ![Jeu créé dans ce didacticiel](../ide/media/express_finishedgame.png)
**Jeu de combinaisons** avec des paires d’icônes visibles

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

-   Pour passer à l’étape suivante du tutoriel, consultez [Étape 8 : ajouter une méthode pour vérifier si le joueur a gagné](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

-   Pour revenir à l’étape précédente du tutoriel, consultez [Étape 6 : ajouter une minuterie](../ide/step-6-add-a-timer.md).
