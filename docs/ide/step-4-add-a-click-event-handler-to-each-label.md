---
title: 'Étape 4 : Ajouter un gestionnaire d’événements Click à chaque étiquette'
description: Découvrez comment ajouter un gestionnaire d’événements Click à chaque contrôle Label.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- vb
ms.assetid: 16bdbc7c-4129-411d-bace-f4a3e5375975
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f620b097e2a565bbacf3322d03385aa70fd0356f
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480601"
---
# <a name="step-4-add-a-click-event-handler-to-each-label"></a>Étape 4 : Ajouter un gestionnaire d’événements Click à chaque étiquette

Le jeu de combinaisons fonctionne comme suit :

1. Lorsqu'un joueur choisit l'une des cases avec une icône masquée, le programme révèle l'icône en lui conférant une couleur noire.

2. Le joueur choisit ensuite une autre icône masquée.

3. Si les deux icônes sélectionnées sont identiques, elles restent visibles. Dans le cas contraire, elles sont à nouveau masquées.

   Pour que votre programme suive ces principes, vous devez ajouter un gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> qui modifiera la couleur de l’étiquette choisie.

## <a name="to-add-a-click-event-handler-to-each-label"></a>Pour ajouter un gestionnaire d'événements Click à chaque étiquette

1. Ouvrez le formulaire dans le **Concepteur Windows Forms**. Dans l'**Explorateur de solutions**, choisissez *Form1.cs* ou *Form1.vb*. Dans la barre de menus, choisissez Concepteur de **vues**  >  **Designer**.

2. Choisissez le premier contrôle Label pour le sélectionner. Ensuite, maintenez la touche **Ctrl** enfoncée tout en choisissant d'autres étiquettes pour les sélectionner. Assurez-vous que chaque contrôle Label est sélectionné.

3. Choisissez le bouton **Événements** dans la barre d’outils de la fenêtre **Propriétés** pour afficher la page **Événements** dans la fenêtre **Propriétés**. Faites défiler jusqu’à l’événement **Click** , puis entrez **label_Click** dans la zone, comme indiqué dans la capture d’écran suivante.

     ![Fenêtre Propriétés affichant l'événement Click](../ide/media/express_labelclick.png)

4. Appuyez sur la touche **entrée** . L'IDE ajoute un `Click`gestionnaire d'événements appelé `label_Click()` au code et le raccorde à chacune des étiquettes sur le formulaire.

5. Remplissez le reste du code, comme suit :

     [!code-csharp[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/CSharp/step-4-add-a-click-event-handler-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#4](../ide/codesnippet/VisualBasic/step-4-add-a-click-event-handler-to-each-label_1.vb)]

     > [!IMPORTANT]
     > Utilisez le contrôle de langage de programmation en haut à droite de cette page pour afficher l’extrait de code C# ou l’extrait de code Visual Basic.<br><br>![Contrôle du langage de programmation pour Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

    > [!NOTE]
    > Si vous effectuez un copier-coller du bloc de code `label_Click()` au lieu d'écrire le code manuellement, veillez à remplacer le code `label_Click()` existant. Sinon, vous obtiendrez au final un bloc de code en double.

    > [!NOTE]
    > Vous pouvez reconnaître `object sender` en haut du gestionnaire d’événements comme étant le même que celui utilisé dans le [Tutoriel 2 : créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md). Comme vous avez raccordé plusieurs événements Click de contrôle d’étiquette à une seule méthode de gestionnaire d'événements, la même méthode est appelée quel que soit l’étiquette choisie par l'utilisateur. La méthode de gestionnaire d’événements doit savoir quelle étiquette a été choisie. Elle utilise donc le nom `sender` pour identifier le contrôle d’étiquette. La première ligne de la méthode indique au programme qu’il ne s’agit pas uniquement d’un objet générique, mais plus précisément d’un contrôle d’étiquette, et qu’il utilise le nom `clickedLabel` pour accéder aux propriétés et méthodes de l’étiquette.

     Cette méthode vérifie d’abord si un objet `clickedLabel` a été correctement converti (cast) en contrôle d’étiquette. Dans le cas contraire, il a une valeur `null` (C#) ou `Nothing` (Visual Basic), et vous ne voudrez pas exécuter le reste du code dans la méthode. Ensuite, la méthode vérifie la couleur de texte du contrôle Label choisi en utilisant la propriété **ForeColor** de ce dernier. Si la couleur du texte du contrôle Label est noire, cela signifie que l'icône a déjà été choisie et la méthode est terminée. (C’est ce que `return` fait l’instruction : elle indique au programme d’arrêter l’exécution de la méthode.) Dans le cas contraire, l’icône n’a pas été choisie et le programme modifie la couleur du texte de l’étiquette en noir.

6. Dans la barre de menus, choisissez **fichier**  >  **enregistrer tout** pour enregistrer votre progression, puis, dans la barre de menus, choisissez **Déboguer**  >  **Démarrer le débogage** pour exécuter votre programme. Un formulaire vierge doit s'afficher avec un arrière-plan bleu. Choisissez l'une des cellules du formulaire et l'une des icônes doit apparaître. Continuez à choisir des emplacements différents dans le formulaire. Chaque fois que vous choisissez une icône, elle doit s'afficher.

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez **[étape 5 : ajouter des références aux étiquettes](../ide/step-5-add-label-references.md)**.

- Pour revenir à l’étape précédente du tutoriel, consultez [Étape 3 : affecter une icône aléatoire à chaque étiquette](../ide/step-3-assign-a-random-icon-to-each-label.md).
