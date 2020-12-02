---
title: 'Étape 5 : Ajouter des contrôles à votre formulaire'
description: Découvrez comment ajouter des contrôles, tels qu’un <xref:System.Windows.Forms.PictureBox> contrôle et un <xref:System.Windows.Forms.CheckBox> contrôle, à votre formulaire.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4ff3e132087b97339bc710555428ba7488fa2e06
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480575"
---
# <a name="step-5-add-controls-to-your-form"></a>Étape 5 : Ajouter des contrôles à votre formulaire

Lors de cette étape, vous ajoutez des contrôles à votre formulaire (notamment des contrôles <xref:System.Windows.Forms.PictureBox> et <xref:System.Windows.Forms.CheckBox>). Ensuite, vous ajoutez des contrôles <xref:System.Windows.Forms.Button> à votre formulaire.

## <a name="how-to-add-controls-to-your-form"></a>Comment ajouter des contrôles à votre formulaire

1. Choisissez l’onglet **boîte à outils** sur le côté gauche de l’IDE de Visual Studio (ou appuyez sur **CTRL** + **ALT** + **X**), puis développez le groupe **contrôles communs** . Il affiche les principaux contrôles que vous apercevez dans les formulaires.

1. Double-cliquez sur l’élément **PictureBox** pour ajouter un contrôle PictureBox à votre formulaire. Étant donné que le contrôle TableLayoutPanel est ancré pour remplir votre formulaire, l'IDE ajoute le contrôle PictureBox dans la première cellule vide (angle supérieur gauche).

1. Choisissez le nouveau contrôle **PictureBox** pour le sélectionner, puis choisissez le triangle noir sur le nouveau contrôle PictureBox pour afficher sa liste de tâches, comme illustré dans la capture d’écran suivante.

    ![Tâches PictureBox](../ide/media/express_pictureboxtasks.png)<br/>PictureBox **_ _tasks**

    > [!NOTE]
    > Si vous ajoutez par erreur un type de contrôle incorrect à votre TableLayoutPanel, vous pouvez le supprimer. Cliquez avec le bouton droit sur le contrôle, puis choisissez **Supprimer** dans le menu contextuel. Vous pouvez également supprimer des contrôles du formulaire à l'aide de la barre de menus. Dans la barre de menus, choisissez **modifier**  >  **Annuler** ou **modifier** la  >  **suppression**.

1. Dans le menu **tâches PictureBox** du contrôle **PictureBox** , choisissez le lien **ancrer dans le conteneur parent** . La valeur **Fill** est alors affectée automatiquement à la propriété **Dock** de PictureBox. Pour le voir, choisissez le contrôle **PictureBox** pour le sélectionner, accédez à la fenêtre **Propriétés** et assurez-vous que la propriété **Dock** a la valeur **Fill**.

1. Modifiez la propriété **ColumnSpan** du PictureBox pour qu’il s’étende sur deux colonnes. Dans le **PictureBox**, choisissez le contrôle **PictureBox** et affectez à sa propriété **ColumnSpan** la valeur **2**. Vous voulez également que le PictureBox affiche un cadre vide lorsqu'il ne contient aucun élément. Affectez la valeur **Fixed3D** à sa propriété **BorderStyle**.

    > [!NOTE]
    > Si vous ne voyez pas de propriété **ColumnSpan** pour votre contrôle PictureBox, il est probable que le contrôle PictureBox a été ajouté au formulaire et non au contrôle TableLayoutPanel. Pour résoudre ce problème, choisissez le contrôle **PictureBox**, supprimez-le, choisissez le **TableLayoutPanel**, puis ajoutez un nouveau contrôle PictureBox.

1. Choisissez le **TableLayoutPanel** sur le formulaire, puis ajoutez un contrôle CheckBox au formulaire. Double-cliquez sur l’élément **CheckBox** dans la **boîte à outils** pour ajouter un nouveau contrôle CheckBox à la cellule libre suivante de votre tableau. Étant donné qu'un contrôle PictureBox occupe les deux premières cellules du contrôle TableLayoutPanel, le contrôle CheckBox est ajouté à la cellule inférieure gauche. Choisissez la propriété **Text** et tapez le mot **Stretch**, comme illustré dans l’image suivante.

    ![Contrôle TextBox avec propriété Stretch](../ide/media/express_pictureviewercheckbox.png)<br/>**_TextBox_* _ _Control avec * ***Stretch**_ _property *

1. Choisissez le **TableLayoutPanel** dans le formulaire, puis accédez au groupe **conteneurs** dans la **boîte à outils** (où vous avez obtenu votre contrôle TableLayoutPanel) et double-cliquez sur l’élément **FlowLayoutPanel** pour ajouter un nouveau contrôle à la dernière cellule (en bas à droite). Ancrez ensuite le FlowLayoutPanel dans le TableLayoutPanel. Pour ce faire, vous pouvez soit choisir **ancrer dans le conteneur parent** dans la liste des tâches triangle noir du contrôle FlowLayoutPanel, soit définir la propriété **Dock** de FlowLayoutPanel sur **Fill**.

    > [!NOTE]
    > Un <xref:System.Windows.Forms.FlowLayoutPanel> est un conteneur qui réorganise les autres contrôles d’une ligne, l’un après l’autre. Quand vous redimensionnez un FlowLayoutPanel, il dispose tous ses contrôles sur une seule ligne, s’il y a de la place pour le faire. Sinon, il les réorganise par lignes, les unes au-dessus des autres. <br/><br/>Ici, vous allez utiliser un FlowLayoutPanel pour contenir quatre boutons. Si les boutons sont disposés les uns au-dessus des autres lorsque vous les ajoutez, veillez à sélectionner le contrôle FlowLayoutPanel avant d’ajouter les boutons. <br/><br/>(En général, chaque cellule contient un seul contrôle. Dans cet exemple, la cellule inférieure droite du contrôle TableLayoutPanel contient quatre contrôles bouton. Pourquoi ?  Comme FlowLayoutPanel est un contrôle conteneur, qui est un contrôle dans une cellule qui contient d’autres contrôles.)

## <a name="to-add-buttons"></a>Pour ajouter des boutons

1. Choisissez le nouveau contrôle FlowLayoutPanel que vous avez ajouté. Accédez à **contrôles communs** dans la **boîte à outils** et double-cliquez sur l’élément de **bouton** pour ajouter un contrôle bouton appelé **Button1** à votre FlowLayoutPanel. Répétez la même opération pour ajouter un deuxième bouton. L’IDE détermine qu’il existe déjà un bouton appelé **button1** et appelle donc le suivant, **button2**.

1. En général, vous ajoutez les autres boutons à l’aide de la **boîte à outils**. Cette fois-ci, choisissez **button2**, puis dans la barre de menus, choisissez **modifier** la  >  **copie** (ou appuyez sur **CTRL** + **C**). Ensuite, choisissez **Edition**  >  **coller** dans la barre de menus (ou appuyez sur **CTRL** + **V**) pour coller une copie de votre bouton. Maintenant collez-le à nouveau. Notez que l’IDE ajoute **button3** et **Button4** au contrôle FlowLayoutPanel.

    > [!NOTE]
    > Vous pouvez copier et coller n'importe quel contrôle. L'IDE nomme et place les nouveaux contrôles de façon logique. Si vous collez un contrôle dans un conteneur, l'IDE choisit de le placer dans l'espace logique suivant.

1. Choisissez le premier bouton et affectez la valeur **Afficher une image** à sa propriété **Text**. Affectez ensuite les valeurs **Effacer l’image**, **Définir la couleur d’arrière-plan** et **Fermer** aux propriétés **Text** des trois boutons suivants.

1. Dimensionnez les boutons et organisez-les afin qu’ils s’alignent sur le côté droit du panneau. Choisissez le contrôle **FlowLayoutPanel** et examinez sa propriété **FlowDirection** . Modifiez-la pour qu’elle ait la valeur **RightToLeft**.

   Les boutons doivent s’aligner eux-mêmes sur le côté droit de la cellule et dans l’ordre inverse pour que le bouton **afficher une image** soit à droite.

    > [!NOTE]
    > Si les boutons sont encore dans le désordre, vous pouvez les faire glisser autour du FlowLayoutPanel pour les réorganiser comme vous le voulez. Vous pouvez choisir un bouton et le faire glisser vers la gauche ou vers la droite.

1. Choisissez le bouton **Fermer** pour le sélectionner. Ensuite, pour choisir le reste des boutons en même temps, appuyez sur la touche **CTRL** et maintenez-la enfoncée, puis sélectionnez-les.

   Après avoir sélectionné tous les boutons, accédez à la fenêtre **Propriétés** et faites défiler jusqu’à la propriété **AutoSize** . Cette propriété indique au bouton qu'il doit se redimensionner automatiquement pour s'ajuster à l'ensemble de son texte. Affectez-lui la valeur **true**.

   Vos boutons doivent maintenant avoir des dimensions correctes et se trouver dans le bon ordre. (Tant que les quatre boutons sont sélectionnés, vous pouvez modifier les quatre propriétés **AutoSize** en même temps.) L’illustration suivante montre les quatre boutons.

    ![Visionneuse d’images avec quatre boutons](../ide/media/express_autosize.png)<br/>**_Visionneuse d’images_* _ _with quatre boutons *

1. Maintenant, exécutez à nouveau votre programme pour voir vos modifications.

   Notez que les boutons et la case à cocher ne sont pas encore disponibles &mdash; , mais ils seront bientôt disponibles.

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

* Pour passer à l’étape suivante du didacticiel, consultez **[étape 6 : nommer vos contrôles bouton](../ide/step-6-name-your-button-controls.md)**.

* Pour revenir à l’étape précédente du didacticiel, consultez [étape 4 : composer votre formulaire avec un contrôle TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Voir aussi

* [Didacticiel 2 : créer un questionnaire mathématique chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Didacticiel 3 : créer un jeu de combinaisons](tutorial-3-create-a-matching-game.md)
