---
title: 'Étape 3 : Définir les propriétés de votre formulaire'
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1cf71ca26a26aecceb605c0483499bc0b0e24d30
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913148"
---
# <a name="step-3-set-your-form-properties"></a>Étape 3 : Définir les propriétés de votre formulaire

Ensuite, vous utilisez la fenêtre **Propriétés** pour changer l’apparence de votre formulaire.

## <a name="how-to-set-your-form-properties"></a>Comment définir les propriétés de votre formulaire

1. Vérifiez que vous êtes dans le **Concepteur Windows Forms**. Dans l’environnement de développement intégré (IDE) de Visual Studio, choisissez l’onglet **Form1.cs [Design]** (ou l’onglet **Form1.vb [Design]** dans Visual Basic).

1. Choisissez un endroit quelconque dans le formulaire **Form1** pour le sélectionner. La fenêtre **Propriétés** doit maintenant afficher les propriétés du formulaire. Les formulaires ont plusieurs propriétés. Par exemple, vous pouvez définir la couleur du premier plan et de l'arrière-plan, le texte du titre qui est affiché en haut du formulaire, les dimensions du formulaire, ainsi que d'autres propriétés.

   > [!NOTE]
   > Si la fenêtre **Propriétés** ne s’affiche pas, arrêtez votre application en choisissant le bouton carré **arrêter le débogage** de la barre d’outils, ou fermez simplement la fenêtre. Si l’application est arrêtée et que vous ne voyez toujours pas la fenêtre **Propriétés** , dans la barre de menus, choisissez **Afficher** > la**fenêtre Propriétés**.

1. Après avoir sélectionné le formulaire, recherchez la propriété **Text** dans la fenêtre **Propriétés**. Suivant la façon dont la liste est triée, vous devrez peut-être la faire défiler. Choisissez **Texte**, tapez **Visionneuse d’images**, puis appuyez sur **Entrée**.  La **visionneuse d’images** de texte doit maintenant être présente dans la barre de titre de votre formulaire, et la fenêtre **Propriétés** doit ressembler à la capture d’écran suivante.

    ![Fenêtre Propriétés](../ide/media/express_edittextproperty.png)<br>
   ***Propriétés*** de *fenêtre*

   > [!NOTE]
   > Les propriétés peuvent être classées selon une vue **Par catégorie** ou **Alphabétique**. Vous pouvez passer d’une vue à l’autre à l’aide des boutons de la fenêtre **Propriétés**. Dans ce tutoriel, il est plus facile de rechercher des propriétés via la vue **Alphabétique**.

1. Revenez au **Concepteur Windows Forms**. Sélectionnez la poignée de déplacement située dans l'angle inférieur droit du formulaire, c'est-à-dire le petit carré blanc présenté ci-dessous.

    ![Faire glisser la poignée](../ide/media/express_bottomrt_drag.png)<br>
   *Faire glisser la poignée*

    Faites glisser la poignée pour redimensionner le formulaire et le rendre plus large et un peu plus grand.

1. Dans la fenêtre **Propriétés**, vous pouvez observer que la propriété **Size** a changé. En effet, la propriété **Size** change dès que vous redimensionnez le formulaire. Essayez de faire glisser la poignée du formulaire pour lui donner une taille adaptée à ce projet, soit environ **550, 350** (l'exactitude n'est pas nécessaire). Vous pouvez également entrer les valeurs directement dans la propriété **Size**, puis choisir la touche **Entrée**.

1. Exécutez à nouveau votre application. N’oubliez pas que vous pouvez utiliser l’une des méthodes suivantes pour exécuter votre application.

   - Choisissez la touche **F5**.

   - Dans la barre de menus, choisissez **Débogage** > **Démarrer le débogage**.

   - Dans la barre d’outils, choisissez le bouton **Démarrer le débogage**, qui se présente comme suit.

      ![Bouton Démarrer le débogage de la barre d’outils](../ide/media/express_icondebug.png)<br>
     ***Démarrer le débogage*** *bouton de barre d’outils*

     Comme auparavant, l’IDE génère et exécute votre application, et une fenêtre s’affiche.

1. Avant de passer à l’étape suivante, arrêtez votre application, car l’IDE ne vous permettra pas de modifier votre application pendant son exécution. N’oubliez pas que vous pouvez utiliser l’une des méthodes suivantes pour arrêter votre application.

   - Dans la barre d’outils, choisissez le bouton **Arrêter le débogage**.

   - Dans la barre de menus, choisissez **Débogage** > **Arrêter le débogage**.

   - À l’aide de votre clavier, appuyez sur **MAJ**+**F5**.

   - Cliquez sur le bouton **X** dans l’angle supérieur de la fenêtre de la **visionneuse d’images** .

## <a name="next-steps"></a>Étapes suivantes

* Pour passer à l’étape suivante du didacticiel, **consultez [étape 4 : Composez votre formulaire avec un contrôle](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)** TableLayoutPanel.

* Pour revenir à l’étape précédente du tutoriel, consultez [Étape 2 : Exécutez votre application](../ide/step-2-run-your-program.md)visionneuse d’images.

## <a name="see-also"></a>Voir aussi

* [Tutoriel 2 : Créer un questionnaire mathématique chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Tutoriel 3 : Créer un jeu de combinaisons](tutorial-3-create-a-matching-game.md)
