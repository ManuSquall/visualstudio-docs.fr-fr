---
title: 'Étape 3 : Définir les propriétés de votre formulaire'
description: Découvrez comment utiliser la Fenêtre Propriétés pour modifier l’apparence de votre formulaire.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10f021e8f8151216cd2728e1e9723b0edb9b3e1f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950729"
---
# <a name="step-3-set-your-form-properties"></a>Étape 3 : Définir les propriétés de votre formulaire

Ensuite, vous utilisez la fenêtre **Propriétés** pour changer l’apparence de votre formulaire.

## <a name="how-to-set-your-form-properties"></a>Comment définir les propriétés de votre formulaire

1. Veillez à consulter **Concepteur Windows Forms**. Dans l’environnement de développement intégré (IDE) de Visual Studio, choisissez l’onglet **Form1.cs [Design]** (ou l’onglet **Form1.vb [Design]** dans Visual Basic).

1. Choisissez un endroit quelconque dans le formulaire **Form1** pour le sélectionner. La fenêtre **Propriétés** doit maintenant afficher les propriétés du formulaire. Les formulaires ont plusieurs propriétés. Par exemple, vous pouvez définir la couleur du premier plan et de l'arrière-plan, le texte du titre qui est affiché en haut du formulaire, les dimensions du formulaire, ainsi que d'autres propriétés.

   > [!NOTE]
   > Si la fenêtre **Propriétés** ne s’affiche pas, arrêtez votre application en choisissant le bouton carré **arrêter le débogage** de la barre d’outils, ou fermez simplement la fenêtre. Si l’application est arrêtée et que vous ne voyez toujours pas la fenêtre **Propriétés** , dans la barre de menus, choisissez **Afficher** la  >  **fenêtre Propriétés**.

1. Après avoir sélectionné le formulaire, recherchez la propriété **Text** dans la fenêtre **Propriétés**. Suivant la façon dont la liste est triée, vous devrez peut-être la faire défiler. Choisissez **texte**, tapez **visionneuse d’images**, puis appuyez sur **entrée**.  La **visionneuse d’images** de texte doit maintenant être présente dans la barre de titre de votre formulaire, et la fenêtre **Propriétés** doit ressembler à la capture d’écran suivante.

    ![Fenêtre Propriétés](../ide/media/express_edittextproperty.png)<br>
   ***Propriétés** _ _window *

   > [!NOTE]
   > Les propriétés peuvent être classées selon une vue par **catégorie** ou par **ordre alphabétique** . Vous pouvez passer d’une vue à l’autre à l’aide des boutons de la fenêtre **Propriétés**. Dans ce didacticiel, il est plus facile de rechercher des propriétés via la vue **alphabétique** .

1. Revenez au **Concepteur Windows Forms**. Sélectionnez la poignée de déplacement située dans l'angle inférieur droit du formulaire, c'est-à-dire le petit carré blanc présenté ci-dessous.

    ![Faire glisser la poignée](../ide/media/express_bottomrt_drag.png)<br>
   *Faire glisser la poignée*

    Faites glisser la poignée pour redimensionner le formulaire et le rendre plus large et un peu plus grand.

1. Dans la fenêtre **Propriétés**, vous pouvez observer que la propriété **Size** a changé. En effet, la propriété **Size** change dès que vous redimensionnez le formulaire. Essayez de faire glisser la poignée du formulaire pour lui donner une taille adaptée à ce projet, soit environ **550, 350** (l'exactitude n'est pas nécessaire). Vous pouvez également entrer les valeurs directement dans la propriété **Size** , puis choisir la touche **entrée** .

1. Exécutez à nouveau votre application. N’oubliez pas que vous pouvez utiliser l’une des méthodes suivantes pour exécuter votre application.

   - Choisissez la touche **F5**.

   - Dans la barre de menus, choisissez **Déboguer**  >  **Démarrer le débogage**.

   - Dans la barre d’outils, choisissez le bouton **Démarrer le débogage**, qui se présente comme suit.

      ![Bouton de barre d'outils Démarrer le débogage](../ide/media/express_icondebug.png)<br>
     ***Démarrer le débogage** _ _toolbar bouton *

     Comme auparavant, l’IDE génère et exécute votre application, et une fenêtre s’affiche.

1. Avant de passer à l’étape suivante, arrêtez votre application, car l’IDE ne vous permettra pas de modifier votre application pendant son exécution. N’oubliez pas que vous pouvez utiliser l’une des méthodes suivantes pour arrêter votre application.

   - Dans la barre d’outils, choisissez le bouton **Arrêter le débogage**.

   - Dans la barre de menus, choisissez **Déboguer**  >  **arrêter le débogage**.

   - À l’aide de votre clavier, appuyez sur **MAJ** + **F5**.

   - Cliquez sur le bouton **X** dans l’angle supérieur de la fenêtre de la **visionneuse d’images** .

## <a name="next-steps"></a>Étapes suivantes

* Pour passer à l’étape suivante du didacticiel, consultez **[étape 4 : composer votre formulaire avec un contrôle TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)**.

* Pour revenir à l’étape précédente du didacticiel, consultez [étape 2 : exécuter votre application visionneuse d’images](../ide/step-2-run-your-program.md).

## <a name="see-also"></a>Voir aussi

* [Didacticiel 2 : créer un questionnaire mathématique chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Didacticiel 3 : créer un jeu de combinaisons](tutorial-3-create-a-matching-game.md)
