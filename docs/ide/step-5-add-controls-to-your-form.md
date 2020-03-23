---
title: 'Étape 5 : ajouter des contrôles à votre formulaire'
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631def96fc7e4b5d7858ea3474492b41c526da65
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579351"
---
# <a name="step-5-add-controls-to-your-form"></a>Étape 5 : ajouter des contrôles à votre formulaire

Lors de cette étape, vous ajoutez des contrôles à votre formulaire (notamment des contrôles <xref:System.Windows.Forms.PictureBox> et <xref:System.Windows.Forms.CheckBox>). Ensuite, vous ajoutez des contrôles <xref:System.Windows.Forms.Button> à votre formulaire.

## <a name="how-to-add-controls-to-your-form"></a>Comment ajouter des contrôles à votre formulaire

1. Choisissez l’onglet **Toolbox** sur le côté gauche de l’IDE Visual Studio (ou appuyez sur **Ctrl**+**Alt**+**X**), puis agrandir le groupe **Common Controls.** Il affiche les principaux contrôles que vous apercevez dans les formulaires.

1. Double-cliquez sur l’élément **PictureBox** pour ajouter un contrôle PictureBox à votre formulaire. Étant donné que le contrôle TableLayoutPanel est ancré pour remplir votre formulaire, l'IDE ajoute le contrôle PictureBox dans la première cellule vide (angle supérieur gauche).

1. Choisissez le nouveau contrôle **PictureBox** pour le sélectionner, puis choisissez le triangle noir sur le nouveau contrôle PictureBox pour afficher sa liste de tâches, comme indiqué dans la capture d’écran suivante.

    ![Tâches PictureBox](../ide/media/express_pictureboxtasks.png)<br/>*Tâches* PictureBoxMD*

    > [!NOTE]
    > Si vous ajoutez par erreur un type de contrôle incorrect à votre TableLayoutPanel, vous pouvez le supprimer. Cliquez avec le bouton droit sur le contrôle, puis choisissez **Supprimer** dans le menu contextuel. Vous pouvez également supprimer des contrôles du formulaire à l'aide de la barre de menus. Sur la barre de menu, choisissez **Edit** > **Undo**, ou **Modifier** > **Supprimer**.

1. Dans le menu **PictureBox Tasks** du contrôle **PictureBox,** choisissez le Dock dans le lien **de conteneur parent.** La valeur **Fill** est alors affectée automatiquement à la propriété **Dock** de PictureBox. Pour voir cela, choisissez le contrôle **PictureBox** pour le sélectionner, allez à la fenêtre **Propriétés,** et assurez-vous que la propriété **Dock** est réglé pour **remplir**.

1. Modifiez la propriété **ColumnSpan** du PictureBox pour qu’il s’étende sur deux colonnes. Dans la **PictureBox**, choisissez le contrôle **PictureBox** et définissez sa propriété **ColumnSpan** à **2**. Vous voulez également que le PictureBox affiche un cadre vide lorsqu'il ne contient aucun élément. Affectez la valeur **Fixed3D** à sa propriété **BorderStyle**.

    > [!NOTE]
    > Si vous ne voyez pas de propriété **ColumnSpan** pour votre contrôle PictureBox, il est probable que le contrôle PictureBox a été ajouté au formulaire et non au contrôle TableLayoutPanel. Pour résoudre ce problème, choisissez la **PictureBox**, supprimez-la, choisissez le **TableLayoutPanel,** puis ajoutez une nouvelle PictureBox.

1. Choisissez le **TableLayoutPanel** sur le formulaire, puis ajoutez un contrôle CheckBox au formulaire. Double-cliquez sur l’élément **CheckBox** dans la boîte à **outils** pour ajouter un nouveau contrôle CheckBox à la cellule gratuite suivante dans votre table. Étant donné qu'un contrôle PictureBox occupe les deux premières cellules du contrôle TableLayoutPanel, le contrôle CheckBox est ajouté à la cellule inférieure gauche. Choisissez la propriété **de texte** et tapez le mot **Stretch**, comme indiqué dans l’image suivante.

    ![Contrôle TextBox avec propriété Stretch](../ide/media/express_pictureviewercheckbox.png)<br/>***Contrôle TextBox*** *avec la* ***propriété*** *Stretch*

1. Choisissez le **TableLayoutPanel** sur le formulaire, puis allez au groupe **Containers** dans la boîte à **outils** (où vous avez obtenu votre contrôle TableLayoutPanel) et double-cliquez sur **l’élément FlowLayoutPanel** pour ajouter un nouveau contrôle à la dernière cellule (en bas à droite). Ensuite, amarrez le FlowLayoutPanel dans le TableLayoutPanel. Vous pouvez le faire soit en choisissant **Dock dans le conteneur parent** sur la liste de tâches triangle noir du FlowLayoutPanel, soit en définissant la propriété **Dock** de FlowLayoutPanel à **remplir**.

    > [!NOTE]
    > A <xref:System.Windows.Forms.FlowLayoutPanel> est un conteneur qui arrange d’autres commandes d’affilée, l’une après l’autre. Lorsque vous resize un FlowLayoutPanel, il établit tous ses contrôles dans une seule rangée, si elle a de la place pour le faire. Sinon, il les réorganise par lignes, les unes au-dessus des autres. <br/><br/>Ici, vous utiliserez un FlowLayoutPanel pour contenir quatre boutons. Si les boutons s’arrangent un sur le dessus l’autre lorsque vous les ajoutez, assurez-vous de sélectionner le FlowLayoutPanel avant d’ajouter les boutons. <br/><br/>(Typiquement, chaque cellule ne contient qu’un seul contrôle. Dans cet exemple, la cellule inférieure à droite du TableLayoutPanel contient quatre commandes de boutons. Pourquoi ?  Parce que le FlowLayoutPanel est un contrôle des conteneurs, qui est un contrôle dans une cellule qui détient d’autres contrôles.)

## <a name="to-add-buttons"></a>Pour ajouter des boutons

1. Choisissez le nouveau contrôle FlowLayoutPanel que vous avez ajouté. Rendez-vous sur **les contrôles communs** dans la boîte à **outils** et cliquez deux fois sur l’élément **Bouton** pour ajouter un bouton de contrôle appelé **bouton1** à votre FlowLayoutPanel. Répétez la même opération pour ajouter un deuxième bouton. L’IDE détermine qu’il existe déjà un bouton appelé **button1** et appelle donc le suivant, **button2**.

1. Typiquement, vous ajoutez les autres boutons en utilisant la **boîte à outils**. Cette fois, choisissez **bouton2**, puis à partir de la barre de menu, choisissez **Edit** > **Copy** (ou appuyez sur **Ctrl**+**C**). Ensuite, choisissez **Edit** > **Paste** de la barre de menu (ou appuyez sur **Ctrl**+**V**) pour coller une copie de votre bouton. Maintenant collez-le à nouveau. Notez que l’IDE ajoute **le bouton3** et **le bouton4** au FlowLayoutPanel.

    > [!NOTE]
    > Vous pouvez copier et coller n'importe quel contrôle. L'IDE nomme et place les nouveaux contrôles de façon logique. Si vous collez un contrôle dans un conteneur, l'IDE choisit de le placer dans l'espace logique suivant.

1. Choisissez le premier bouton et affectez la valeur **Afficher une image** à sa propriété **Text**. Affectez ensuite les valeurs **Effacer l’image**, **Définir la couleur d’arrière-plan** et **Fermer** aux propriétés **Text** des trois boutons suivants.

1. Taillez les boutons et arrangeons-les pour qu’ils s’alignent sur le côté droit du panneau. Choisissez le **FlowLayoutPanel** et regardez sa propriété **FlowDirection.** Modifiez-la pour qu’elle ait la valeur **RightToLeft**.

   Les boutons doivent s’aligner sur le côté droit de la cellule, et inverser leur commande de sorte que le afficher un bouton **d’image** est sur la droite.

    > [!NOTE]
    > Si les boutons sont encore dans le désordre, vous pouvez les faire glisser autour du FlowLayoutPanel pour les réorganiser comme vous le voulez. Vous pouvez choisir un bouton et le faire glisser vers la gauche ou vers la droite.

1. Choisissez le bouton **Fermer** pour le sélectionner. Ensuite, pour choisir le reste des boutons en même temps, appuyez et maintenez la clé **Ctrl** et choisissez-les, aussi.

   Après avoir sélectionné tous les boutons, allez à la fenêtre **Propriétés** et faites défiler jusqu’à la propriété **AutoSize.** Cette propriété indique au bouton qu'il doit se redimensionner automatiquement pour s'ajuster à l'ensemble de son texte. Réglez-le à **True**.

   Vos boutons doivent maintenant avoir des dimensions correctes et se trouver dans le bon ordre. (Tant que les quatre boutons sont sélectionnés, vous pouvez changer les quatre propriétés **AutoSize** en même temps.) L’image suivante montre les quatre boutons.

    ![Visionneuse d’images avec quatre boutons](../ide/media/express_autosize.png)<br/>***Visionneuse d’images*** *avec quatre boutons*

1. Maintenant, exécutez votre programme à nouveau pour voir vos changements.

   Notez que les boutons et la case&mdash;à cocher ne font rien encore, mais ils le feront, bientôt.

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

* Pour passer à l’étape suivante tutoriel, voir **[Étape 6: Nommez vos commandes de bouton](../ide/step-6-name-your-button-controls.md)**.

* Pour revenir à l’étape tutoriel précédente, voir [Étape 4: Exposer votre formulaire avec un contrôle TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Voir aussi

* [Tutorial 2: Créer un quiz de mathématiques chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Créer un jeu correspondant](tutorial-3-create-a-matching-game.md)
