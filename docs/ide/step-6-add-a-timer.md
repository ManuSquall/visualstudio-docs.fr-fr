---
title: 'Étape 6 : Ajouter un minuteur'
description: Découvrez comment ajouter un <xref:System.Windows.Forms.Timer> contrôle au jeu de combinaisons.
ms.custom: SEO-VS-2020
ms.date: 03/31/2020
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f59375e9e64e6a7302d65b8c940d82b63adef54f
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214198"
---
# <a name="step-6-add-a-timer"></a>Étape 6 : Ajouter un minuteur
Ensuite, ajoutez un contrôle <xref:System.Windows.Forms.Timer> au jeu de combinaisons. Une minuterie attend un nombre donné de millisecondes, puis déclenche un événement, appelé *battement*. Ceci permet de démarrer ou répéter périodiquement une action. Ici, vous devez utiliser un minuteur pour permettre aux joueurs de choisir deux icônes et, si ces icônes ne correspondent pas, pour masquer les deux icônes à nouveau après un bref délai.

## <a name="to-add-a-timer"></a>Pour ajouter un minuteur

1. Dans la boîte à outils de **Concepteur Windows Forms**, choisissez **minuterie** (dans la catégorie **composants** ), puis appuyez sur la touche **entrée** ou double-cliquez sur la minuterie pour ajouter un contrôle Timer au formulaire. L’icône du minuteur, appelée **Timer1**, doit apparaître dans un espace sous le formulaire, comme illustré dans l’image suivante.

     ![Minuteur](../ide/media/express_timer.png)<br/>
***Minuteur***

    > [!NOTE]
    > Si la boîte à outils est vide, veillez à sélectionner le concepteur de formulaire et non pas le code derrière le formulaire, avant d'ouvrir la boîte à outils.

2. Choisissez l’icône **Timer1** pour sélectionner la minuterie. Dans la fenêtre **Propriétés**, passez de l’affichage des événements à celui des propriétés. Ensuite, affectez la valeur **750** à la propriété **Interval** de la minuterie, mais n’attribuez pas la valeur **False** à la propriété **Enabled**. La propriété **Interval** indique à la minuterie le délai d’attente entre deux *cycles*, ou quand déclencher son événement <xref:System.Windows.Forms.Timer.Tick>. La valeur 750 indique à la minuterie d'attendre trois quarts de seconde (750 millisecondes) avant de déclencher l'événement Tick. Vous devez appeler la méthode <xref:System.Windows.Forms.Timer.Start> pour démarrer la minuterie une fois seulement que le joueur a choisi le second contrôle Label.

3. Choisissez l’icône du contrôle Timer dans **Concepteur Windows Forms** puis appuyez sur la touche **entrée** ou double-cliquez sur la minuterie pour ajouter un gestionnaire d’événements Tick vide. Remplacez le code par le code suivant ou entrez manuellement ce dernier dans le gestionnaire d'événements.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb" id="Snippet7":::

      > [!IMPORTANT]
      > Utilisez le contrôle de langage de programmation en haut à droite de cette page pour afficher l’extrait de code C# ou l’extrait de code Visual Basic.<br><br>![Contrôle du langage de programmation pour Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Le gestionnaire d'événements Tick effectue trois opérations : tout d'abord, il garantit l'arrêt du minuteur en appelant la méthode <xref:System.Windows.Forms.Timer.Stop>. Ensuite, il utilise deux variables de référence, `firstClicked` et `secondClicked`, pour masquer de nouveau les icônes des deux contrôles Label que le joueur a choisis. Enfin, il réinitialise les `firstClicked` variables de `secondClicked` référence et en `null` C# et `Nothing` en Visual Basic. Cette étape est importante car elle permet au programme de se réinitialiser. À présent, le gestionnaire ne conserve aucune trace des contrôles <xref:System.Windows.Forms.Label> et le joueur peut de nouveau choisir un contrôle label.

    > [!NOTE]
    > Un objet Timer a une méthode `Start()` qui démarre le minuteur et une méthode `Stop()` qui l'arrête. Quand vous affectez la valeur **True** à la propriété **Enabled** de la minuterie dans la fenêtre **Propriétés**, la minuterie démarre en même temps que le programme. Si vous conservez la valeur **False**, la minuterie attend que sa méthode `Start()` soit appelée pour démarrer. Normalement, une minuterie déclenche son événement Tick de façon répétée, en utilisant la propriété **Interval** pour déterminer le délai d’attente en millisecondes entre chaque battement. Vous aurez éventuellement remarqué que la méthode `Stop()` de la minuterie est appelée dans l'événement Tick. La minuterie passe ainsi en *mode déclenchement unique*, ce qui signifie que lorsque la méthode `Start()` est appelée, il patiente pendant l’intervalle spécifié, déclenche un seul événement Tick, puis s’arrête.

4. Pour voir la nouvelle minuterie en action, allez dans l'éditeur de code et ajoutez le code suivant en haut et en bas de la méthode du gestionnaire d'événements `label_Click()`. (Vous ajoutez deux `if` instructions en haut et trois instructions en bas ; le reste de la méthode reste le même.)

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb" id="Snippet8":::

     Le code situé en haut de la méthode vérifie si la minuterie a été démarrée en regardant la valeur de la propriété **Enabled**. Ainsi, si le joueur choisit les premier et deuxième contrôles d’étiquette et que le minuteur démarre, rien ne se passe si le joueur choisit une troisième étiquette. Il empêche également le joueur de cliquer rapidement une troisième fois avant que le jeu ne soit prêt pour un autre premier clic. 

     Le code en bas de la méthode indique à la variable de référence `secondClicked` d'effectuer le suivi du deuxième contrôle d’étiquette choisi par le joueur, puis il définit la couleur de l'icône de cette étiquette sur noir pour le rendre visible. Ensuite, il démarre le minuteur en mode déclenchement unique afin qu'il attende 750 millisecondes avant de déclencher un événement Tick unique. Le gestionnaire d’événements Tick du minuteur masque les deux icônes et réinitialise les variables de référence `firstClicked` et `secondClicked` pour que le joueur puisse choisir une autre paire d’icônes dans le formulaire.

5. Enregistrez et exécutez votre programme. Choisissez une icône et elle devient visible.

6. Choisissez une autre icône. Elle s'affiche brièvement, puis les deux icônes disparaissent. Répétez cette opération plusieurs fois. Le formulaire effectue maintenant le suivi des première et deuxième icônes choisies et utilise le minuteur pour effectuer une pause avant de masquer ces icônes.

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez **[étape 7 : garder les paires visibles](../ide/step-7-keep-pairs-visible.md)**.

- Pour revenir à l’étape précédente du didacticiel, consultez [étape 5 : ajouter des références aux étiquettes](../ide/step-5-add-label-references.md).
