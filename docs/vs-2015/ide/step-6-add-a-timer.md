---
title: 'Étape 6 : Ajouter une minuterie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 09e7930b-cab6-4a22-9a6f-72e23f489585
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 31116171a15a7a38b76451777faaed35dc8b1e52
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54795285"
---
# <a name="step-6-add-a-timer"></a>Étape 6 : Ajouter une minuterie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ensuite, ajoutez un contrôle **Timer** au jeu de combinaisons. Une minuterie attend un nombre donné de millisecondes, puis déclenche un événement, appelé *battement*. Ceci permet de démarrer ou répéter périodiquement une action. Ici, vous devez utiliser un minuteur pour permettre aux joueurs de choisir deux icônes et, si ces icônes ne correspondent pas, pour masquer les deux icônes à nouveau après un bref délai.  
  
### <a name="to-add-a-timer"></a>Pour ajouter un minuteur  
  
1.  Dans la boîte à outils du Concepteur Windows Forms, choisissez **Timer** (dans la catégorie **Composants**) et appuyez sur Entrée ou double-cliquez sur la minuterie pour ajouter un contrôle Timer au formulaire. L’icône de la minuterie, appelée **Timer1**, doit apparaître dans un espace sous le formulaire, comme le montre la figure suivante.  
  
     ![Minuteur](../ide/media/express-timer.png "Express_Timer")  
Minuterie  
  
    > [!NOTE]
    >  Si la boîte à outils est vide, veillez à sélectionner le concepteur de formulaire et non pas le code derrière le formulaire, avant d'ouvrir la boîte à outils.  
  
2.  Choisissez l’icône **Timer1** pour sélectionner la minuterie. Dans la fenêtre **Propriétés**, passez de l’affichage des événements à celui des propriétés. Ensuite, affectez la valeur **750** à la propriété **Interval** de la minuterie, mais n’attribuez pas la valeur **False** à la propriété **Enabled**. La propriété **Interval** indique à la minuterie le délai d’attente entre deux *battements*, ou quand déclencher son événement Tick. La valeur 750 indique à la minuterie d'attendre trois quarts de seconde (750 millisecondes) avant de déclencher l'événement Tick. Vous devez appeler la méthode `Start()` pour démarrer la minuterie une fois seulement que le joueur a choisi le second contrôle Label.  
  
3.  Choisissez l’icône du contrôle Timer dans le Concepteur Windows Forms et appuyez sur Entrée ou double-cliquez sur la minuterie pour ajouter un gestionnaire d’événements **Tick** vide. Remplacez le code par le code suivant ou entrez manuellement ce dernier dans le gestionnaire d'événements.  
  
     [!code-csharp[VbExpressTutorial4Step6#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial4Step6#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#7)]  
  
     Le gestionnaire d'événements Tick effectue trois opérations : tout d'abord, il garantit l'arrêt du minuteur en appelant la méthode `Stop()`. Ensuite, il utilise deux variables de référence, `firstClicked` et `secondClicked`, pour masquer de nouveau les icônes des deux contrôles Label que le joueur a choisis. Enfin, il réinitialise les variables de référence `firstClicked` et `secondClicked` à la valeur `null` en Visual C# et `Nothing` en Visual Basic. Cette étape est importante car elle permet au programme de se réinitialiser. À présent, le gestionnaire ne conserve aucune trace des contrôles `Label` et le joueur peut de nouveau choisir un contrôle label.  
  
    > [!NOTE]
    >  Un objet `Timer` a une méthode `Start()` qui démarre le minuteur et une méthode `Stop()` qui l'arrête. Quand vous affectez la valeur **True** à la propriété **Enabled** de la minuterie dans la fenêtre **Propriétés**, la minuterie démarre en même temps que le programme. Si vous conservez la valeur **False**, la minuterie attend que sa méthode `Start()` soit appelée pour démarrer. Normalement, une minuterie déclenche son événement Tick de façon répétée, en utilisant la propriété **Interval** pour déterminer le délai d’attente en millisecondes entre chaque battement. Vous aurez éventuellement remarqué que la méthode `Stop()` de la minuterie est appelée dans l'événement Tick. La minuterie passe ainsi en *mode déclenchement unique*, ce qui signifie que lorsque la méthode `Start()` est appelée, il patiente pendant l’intervalle spécifié, déclenche un seul événement Tick, puis s’arrête.  
  
4.  Pour voir la nouvelle minuterie en action, allez dans l'éditeur de code et ajoutez le code suivant en haut et en bas de la méthode du gestionnaire d'événements `label_Click()`. (Ajoutez une instruction `if` en haut et trois instructions en bas ; le reste de la méthode ne change pas.)  
  
     [!code-csharp[VbExpressTutorial4Step6#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial4Step6#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb#8)]  
  
     Le code situé en haut de la méthode vérifie si la minuterie a été démarrée en regardant la valeur de la propriété **Enabled**. Ainsi, si le joueur choisit les premier et deuxième contrôles `Label` et que la minuterie démarre, rien ne se passe si le joueur choisit un troisième contrôle.  
  
     Le code situé au bas de la méthode indique à la variable de référence `secondClicked` d’effectuer le suivi du deuxième contrôle `Label` choisi par le joueur, puis il définit la couleur de l’icône de ce contrôle Label sur noir pour la rendre visible. Ensuite, il démarre le minuteur en mode déclenchement unique afin qu'il attende 750 millisecondes avant de déclencher un événement Tick unique. Le gestionnaire d'événements Tick du minuteur masque les deux icônes et réinitialise les variables de référence `firstClicked` et `secondClicked` pour que le joueur puisse choisir une autre paire d'icônes dans le formulaire.  
  
5.  Enregistrez et exécutez votre programme. Choisissez une icône et elle devient visible.  
  
6.  Choisissez une autre icône. Elle s'affiche brièvement, puis les deux icônes disparaissent. Répétez cette opération plusieurs fois. Le formulaire effectue maintenant le suivi des première et deuxième icônes choisies et utilise le minuteur pour effectuer une pause avant de masquer ces icônes.  
  
### <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Pour passer à l’étape suivante du didacticiel, consultez [Étape 7 : Garder les paires visibles](../ide/step-7-keep-pairs-visible.md).  
  
-   Pour revenir à l’étape précédente du didacticiel, consultez [Étape 5 : Ajouter des références de contrôles Label](../ide/step-5-add-label-references.md).
