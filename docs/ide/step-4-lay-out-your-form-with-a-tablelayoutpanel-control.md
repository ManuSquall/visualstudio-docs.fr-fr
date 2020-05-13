---
title: 'Étape 4 : composer votre formulaire avec un contrôle TableLayoutPanel'
ms.date: 08/30/2019
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d827077266adbe0a1ba8cabd1f19ae6d815df833
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579382"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Étape 4 : composer votre formulaire avec un contrôle TableLayoutPanel

Dans cette étape, vous allez ajouter un contrôle <xref:System.Windows.Forms.TableLayoutPanel> à votre formulaire. Le TableLayoutPanel permet d’aligner correctement les contrôles dans la forme que vous ajouterez plus tard.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Comment établir votre formulaire avec un contrôle TableLayoutPanel

1. Sur le côté gauche de l’IDE Visual Studio, choisissez **l’onglet Toolbox.** (Alternativement, choisissez **View** > **Toolbox** de la barre de menu, ou appuyez sur **Ctrl**+**Alt**+**X**.)

1. Choisissez le petit symbole triangle à côté du groupe **Containers** pour l’ouvrir, comme le montre la capture d’écran suivante.

     ![Groupe Conteneurs](../ide/media/express_toolbox.png)<br>
***Groupe de conteneurs*** *group*

1. Vous pouvez ajouter des contrôles comme des boutons, des cases à cocher et des étiquettes à votre formulaire. Double-cliquez sur le contrôle TableLayoutPanel dans la **Boîte à outils**. (Ou, vous pouvez faire glisser le contrôle de la boîte à outils sur le formulaire.) Lorsque vous faites cela, l’IDE ajoute un contrôle TableLayoutPanel à votre formulaire, comme indiqué dans la capture d’écran suivante.

     ![Contrôle TableLayoutPanel](../ide/media/express_formtablelayout.png)<br>
***Contrôle TableLayoutPanel*** *control*

    > [!NOTE]
    > Après avoir ajouté votre contrôle TableLayoutPanel, si une fenêtre intitulée **Tâches TableLayoutPanel** s’affiche à l’intérieur de votre formulaire, cliquez n’importe où dans le formulaire pour la fermer. Vous en apprendrez plus sur cette fenêtre plus tard dans le tutoriel.

     Notez que la **Boîte à outils** se développe pour recouvrir votre formulaire lorsque vous sélectionnez son onglet, et se referme lorsque vous effectuez une sélection en dehors de celle-ci. C’est la fonction Auto Hide dans l’IDE. Vous pouvez l’allumer ou désactiver pour l’une des fenêtres en choisissant l’icône pushpin dans le coin supérieur droit de la fenêtre pour basculer Auto Hide et le verrouiller en place. L'icône de la punaise apparaît comme suit.

     ![Icône Punaise](../ide/media/express_pushpintoolbox.png)<br>
***Icône Pushpin*** *icon*

1. Veillez à ce que TableLayoutPanel soit sélectionné lorsque vous le choisissez. Vous pouvez vérifier quel contrôle est sélectionné en regardant la liste des gouttes en haut de la fenêtre **Propriétés,** comme indiqué dans la capture d’écran suivante.

     ![Fenêtre Propriétés affichant le contrôle TableLayoutPanel](../ide/media/express_controlspropwin.png)<br>
***Fenêtre de propriétés*** *affichant* le *contrôle* de ***TableLayoutPanel***

1. Dans la barre d’outils de la fenêtre **Propriétés**, choisissez le bouton **Ordre alphabétique**. Cela trie la liste des propriétés dans la fenêtre **Propriétés** dans l’ordre alphabétique, ce qui rend plus facile de localiser les propriétés dans ce tutoriel.

1. Le sélecteur de contrôles est une liste déroulante située en haut de la fenêtre **Propriétés**. Dans cet exemple, il indique qu’un contrôle appelé `tableLayoutPanel1` est sélectionné. Vous pouvez sélectionner des contrôles en choisissant une zone dans le **Concepteur Windows Forms** ou en utilisant le sélecteur de contrôles.

   À présent que TableLayoutPanel est sélectionné, recherchez la propriété **Dock** et sélectionnez-la **.** Sa valeur doit être **Aucun**. Notez qu’une flèche de déroulement s’affiche en regard de la valeur. Choisissez la flèche, puis sélectionnez le bouton **Fill** (le grand bouton au milieu), comme indiqué dans la capture d’écran suivante.

     ![Fenêtre Propriétés avec Remplissage sélectionné](../ide/media/express_docktable.png)<br>
***Fenêtre de propriété*** *avec* ***Fill*** *sélectionné*

     Dans Visual Studio, le terme *ancrage* signifie qu’une fenêtre est attachée à une autre fenêtre ou zone dans l’IDE. Par exemple, la fenêtre **Propriétés** &mdash;peut être désamarrée qui est,&mdash;non attaché et flottant librement dans Visual Studio ou il peut être amarré contre **Solution Explorer**.

1. Après avoir réglé la propriété TableLayoutPanel **Dock** à **remplir**, notez que le panneau remplit l’ensemble du formulaire. Si vous redimensionnez à nouveau le formulaire, le TableLayoutPanel reste ancré et se redimensionne automatiquement pour s'adapter aux nouvelles dimensions.

    > [!NOTE]
    > Un TableLayoutPanel fonctionne comme un tableau dans Microsoft Office Word : il est composé de lignes et de colonnes, et une même cellule peut s'étendre sur plusieurs lignes et colonnes. Chaque cellule ne peut contenir qu'un seul contrôle (comme un bouton, une case à cocher ou une étiquette). Votre TableLayoutPanel devrait <xref:System.Windows.Forms.PictureBox> avoir un contrôle couvrant <xref:System.Windows.Forms.CheckBox> toute sa première rangée, <xref:System.Windows.Forms.Button> un contrôle dans sa cellule inférieure-gauche, et quatre contrôles dans sa cellule inférieure-droite.

1. Actuellement, le TableLayoutPanel est composé de deux lignes et colonnes de taille égale. Resize eux afin que la première rangée et la colonne de droite sont tous deux beaucoup plus grands. Dans le **Concepteur Windows Forms**, sélectionnez le TableLayoutPanel. Dans l'angle supérieur droit, il y a un petit bouton en forme de triangle noir, comme celui illustré ci-dessous.

     ![Bouton Triangle](../ide/media/express_iconblacktriangle.gif)<br>
***Bouton Triangle*** *button*

     Ce bouton indique que le contrôle dispose de tâches vous permettant de définir ses propriétés automatiquement.

1. Choisissez le triangle pour afficher la liste de tâches du contrôle, comme indiqué dans la capture d’écran suivante.

     ![Tâches TableLayoutPanel](../ide/media/express_tablepanel.png)<br>
***Tâches TableLayoutPanel*** *tasks*

1. Sélectionnez la tâche **Modifier les lignes et les colonnes** pour afficher la fenêtre **Styles de ligne et de colonne**. Sélectionnez **Column1** et affectez-lui la valeur 15 pour cent en vérifiant que le bouton **Pourcentage** est sélectionné et en entrant **15** dans la zone **Pourcentage**. (C’est <xref:System.Windows.Forms.NumericUpDown> un contrôle, que vous allez utiliser dans un tutoriel ultérieur.) Choisissez **la colonne2** et définissez-la à 85 pour cent. Ne sélectionnez pas encore le bouton **OK**, sinon la fenêtre se fermera. (Mais si vous le faites, vous pouvez le rouvrir en utilisant la liste des tâches.)

     ![Styles des lignes et des colonnes TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***TableLayoutPanel*** *colonne et styles de rangée*

1. De la liste **d’abandon Show** en haut de la colonne et **Row Styles** fenêtre, choisissez **Rows**. Affectez les valeurs 90 pour cent à **Ligne1** et 10 pour cent à **Ligne2**.

1. Choisissez le bouton **OK**. Votre TableLayoutPanel doit maintenant avoir une grande ligne en haut, une petite ligne en bas, une petite colonne à gauche et une grande colonne à droite. (Vous pouvez resize les lignes et les colonnes dans le TableLayoutPanel en choisissant **tableLayoutPanel1** sous la forme, puis en faisant glisser ses bordures de rangée et de colonne.)

     ![Form1 avec TableLayoutPanel redimensionné](../ide/media/vs_formafterlayoutpanel.png)<br>
***Form1*** *(Picture Viewer) avec* ***TableLayoutPanel*** resized

## <a name="next-steps"></a>Étapes suivantes

* Pour passer à l’étape suivante tutoriel, voir **[Étape 5: Ajouter des contrôles à votre formulaire](../ide/step-5-add-controls-to-your-form.md)**.

* Pour revenir à l’étape précédente du tutoriel, consultez [Étape 3 : définir les propriétés de votre formulaire](../ide/step-3-set-your-form-properties.md).

## <a name="see-also"></a>Voir aussi

* [Tutorial 2: Créer un quiz de mathématiques chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Créer un jeu correspondant](tutorial-3-create-a-matching-game.md)
