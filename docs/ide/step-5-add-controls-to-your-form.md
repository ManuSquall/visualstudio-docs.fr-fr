---
title: 'Étape 5 : Ajouter des contrôles à votre formulaire'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f1662f484d8738c381f704732389537b0ac3ad5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431479"
---
# <a name="step-5-add-controls-to-your-form"></a>Étape 5 : Ajouter des contrôles à votre formulaire
Lors de cette étape, vous ajoutez des contrôles à votre formulaire (notamment des contrôles <xref:System.Windows.Forms.PictureBox> et <xref:System.Windows.Forms.CheckBox>). Ensuite, vous ajoutez des contrôles <xref:System.Windows.Forms.Button> à votre formulaire.

 ![lien vers la vidéo](../data-tools/media/playvideo.gif)Pour obtenir une version vidéo de cette rubrique, consultez [Turoriel 1 : Créer une visionneuse d’images en Visual Basic – Vidéo 2](http://go.microsoft.com/fwlink/?LinkId=205211) ou [Tutoriel 1 : Créer une visionneuse d’images en C# - Vidéo 2](http://go.microsoft.com/fwlink/?LinkId=205200). Ces vidéos utilisent une version antérieure de Visual Studio et présentent donc de légères différences quant à certaines commandes de menu et autres éléments d’interface utilisateur. Toutefois, les concepts et les procédures fonctionnent de façon similaire dans la version actuelle de Visual Studio.

## <a name="to-add-controls-to-your-form"></a>Pour ajouter des contrôles à votre formulaire

1. Accédez à l’onglet **Boîte à outils** (situé à gauche de l’IDE de Visual Studio) et développez le groupe **Contrôles communs**. Il affiche les principaux contrôles que vous apercevez dans les formulaires.

2. Sélectionnez le contrôle **TableLayoutPanel** dans le formulaire. Pour vérifier que le contrôle TableLayoutPanel est sélectionné, vérifiez que son nom apparaît dans la zone de liste déroulante en haut de la fenêtre **Propriétés**. Vous pouvez également choisir des contrôles de formulaire à l’aide de la zone de liste déroulante en haut de la fenêtre **Propriétés**. Il est souvent plus simple de choisir un contrôle de cette manière que de choisir un contrôle de petite taille à l'aide de la souris.

3. Double-cliquez sur l’élément **PictureBox** pour ajouter un contrôle PictureBox à votre formulaire. Étant donné que le contrôle TableLayoutPanel est ancré pour remplir votre formulaire, l'IDE ajoute le contrôle PictureBox dans la première cellule vide (angle supérieur gauche).

4. Choisissez le nouveau contrôle **PictureBox** pour le sélectionner, puis choisissez le triangle noir sur le nouveau contrôle PictureBox pour afficher sa liste de tâches, comme l’illustre l’image suivante.

     ![Tâches PictureBox](../ide/media/express_pictureboxtasks.png)
Tâches **PictureBox**

    > [!NOTE]
    > Si vous ajoutez par erreur un type de contrôle incorrect à votre TableLayoutPanel, vous pouvez le supprimer. Cliquez avec le bouton droit sur le contrôle, puis choisissez **Supprimer** dans le menu contextuel. Vous pouvez également supprimer des contrôles du formulaire à l'aide de la barre de menus. Dans la barre de menus, choisissez **Modification** > **Annuler**, ou **Modification** > **Supprimer**.

5. Choisissez le lien **Ancrer dans le conteneur parent**. La valeur **Fill** est alors affectée automatiquement à la propriété **Dock** de PictureBox. Pour vous en assurer, choisissez le contrôle **PictureBox** pour le sélectionner, ouvrez la fenêtre **Propriétés** et vérifiez que la propriété **Dock** a la valeur **Fill**.

6. Modifiez la propriété **ColumnSpan** du PictureBox pour qu’il s’étende sur deux colonnes. Choisissez le contrôle **PictureBox** et affectez à sa propriété **ColumnSpan** la valeur **2**. Vous voulez également que le PictureBox affiche un cadre vide lorsqu'il ne contient aucun élément. Affectez la valeur **Fixed3D** à sa propriété **BorderStyle**.

    > [!NOTE]
    > Si vous ne voyez pas de propriété **ColumnSpan** pour votre contrôle PictureBox, il est probable que le contrôle PictureBox a été ajouté au formulaire et non au contrôle TableLayoutPanel. Pour résoudre ce problème, choisissez le contrôle **PictureBox**, supprimez-le, choisissez le contrôle **TableLayoutPanel**, puis ajoutez un nouveau contrôle PictureBox.

7. Choisissez le contrôle **TableLayoutPanel** dans le formulaire, puis ajoutez un contrôle CheckBox au formulaire. Double-cliquez sur l’élément **CheckBox** dans la **Boîte à outils** pour ajouter un nouveau contrôle CheckBox dans la cellule libre suivante de votre tableau. Étant donné qu'un contrôle PictureBox occupe les deux premières cellules du contrôle TableLayoutPanel, le contrôle CheckBox est ajouté à la cellule inférieure gauche. Choisissez la propriété **Text** et tapez le mot **Stretch**, illustré sur l’image suivante.

     ![Contrôle TextBox avec propriété Stretch](../ide/media/express_pictureviewercheckbox.png)
Contrôle **TextBox** avec propriété **Stretch**

8. Choisissez le contrôle **TableLayoutPanel** dans le formulaire, puis accédez au groupe **Conteneurs** dans la **Boîte à outils** (où vous avez obtenu votre contrôle TableLayoutPanel) et double-cliquez sur l’élément **FlowLayoutPanel** pour ajouter un nouveau contrôle à la dernière cellule du contrôle PictureBox (en bas à droite). Ancrez ensuite l’élément FlowLayoutPanel dans le contrôle TableLayoutPanel (en sélectionnant **Ancrer dans le conteneur parent** dans la liste des tâches avec triangle noir du contrôle FlowLayoutPanel, ou en affectant à la propriété **Dock** du contrôle FlowLayoutPanel la valeur **Fill**).

    > [!NOTE]
    > Un <xref:System.Windows.Forms.FlowLayoutPanel> est un conteneur qui classe, dans l'ordre, d'autres contrôles au sein de lignes structurées. Lorsque vous redimensionnez un FlowLayoutPanel, il dispose tous ses contrôles sur une même ligne s'il a suffisamment de place pour le faire. Sinon, il les réorganise par lignes, les unes au-dessus des autres. Vous allez utiliser un FlowLayoutPanel pour contenir quatre boutons. Si les boutons sont disposés les uns au-dessus des autres lorsqu'ils sont ajoutés, vérifiez que le contrôle FlowLayoutPanel est sélectionné avant d'ajouter les boutons. Bien qu'il ait été indiqué que chaque cellule ne peut contenir qu'un seul contrôle, la cellule inférieure droite du contrôle TableLayoutPanel comporte quatre contrôles Button. En effet, vous pouvez insérer un contrôle dans une cellule contenant d'autres contrôles. Ce type de contrôle est appelé conteneur et le contrôle FlowLayoutPanel en est un exemple.

## <a name="to-add-buttons"></a>Pour ajouter des boutons

1. Choisissez le nouveau contrôle FlowLayoutPanel que vous avez ajouté. Accédez à **Contrôles communs** dans la **Boîte à outils** et double-cliquez sur l’élément **Bouton** pour ajouter un contrôle bouton appelé **button1** à votre contrôle FlowLayoutPanel. Répétez la même opération pour ajouter un deuxième bouton. L’IDE détermine qu’il existe déjà un bouton appelé **button1** et appelle donc le suivant, **button2**.

2. En général, vous ajoutez les autres boutons à l'aide de la **Boîte à outils**. Cette fois-ci, choisissez **button2** puis, dans la barre de menus, choisissez **Modification** > **Copier** (ou appuyez sur **Ctrl**+**C**). Dans la barre de menus, choisissez **Modification** > **Coller** (ou appuyez sur **Ctrl**+**V**) pour coller une copie de votre bouton. Maintenant collez-le à nouveau. L’IDE a maintenant ajouté **button3** et **button4** au contrôle FlowLayoutPanel.

    > [!NOTE]
    > Vous pouvez copier et coller n'importe quel contrôle. L'IDE nomme et place les nouveaux contrôles de façon logique. Si vous collez un contrôle dans un conteneur, l'IDE choisit de le placer dans l'espace logique suivant.

3. Choisissez le premier bouton et affectez la valeur **Afficher une image** à sa propriété **Text**. Affectez ensuite les valeurs **Effacer l’image**, **Définir la couleur d’arrière-plan** et **Fermer** aux propriétés **Text** des trois boutons suivants.

4. L'étape suivante consiste à redimensionner les boutons et à les disposer de façon à les aligner à droite du volet. Choisissez le contrôle **FlowLayoutPanel** et examinez sa propriété **FlowDirection**. Modifiez-la pour qu’elle ait la valeur **RightToLeft**. Une fois la modification effectuée, les boutons doivent s’aligner automatiquement à droite de la cellule et se positionner dans l’ordre inverse pour que le bouton **Afficher une image** soit à droite.

    > [!NOTE]
    > Si les boutons sont encore dans le désordre, vous pouvez les faire glisser autour du FlowLayoutPanel pour les réorganiser comme vous le voulez. Vous pouvez choisir un bouton et le faire glisser vers la gauche ou vers la droite.

5. Choisissez le bouton **Fermer** pour le sélectionner. Maintenez la touche **Ctrl** enfoncée et choisissez les trois autres boutons de façon à les sélectionner tous. Quand tous les boutons sont sélectionnés, ouvrez la fenêtre **Propriétés** et faites défiler jusqu’à la propriété **AutoSize**. Cette propriété indique au bouton qu'il doit se redimensionner automatiquement pour s'ajuster à l'ensemble de son texte. Affectez-lui la valeur **true**. Vos boutons doivent maintenant avoir des dimensions correctes et se trouver dans le bon ordre. (Si les quatre boutons sont sélectionnés, vous pouvez modifier les quatre propriétés **AutoSize** en même temps.) L'image suivante montre les quatre boutons.

     ![Visionneuse d’images avec quatre boutons](../ide/media/express_autosize.png)
**Visionneuse d’images** avec quatre boutons

6. Maintenant, exécutez à nouveau votre programme pour examiner la nouvelle présentation de votre formulaire. La sélection des boutons et de la case à cocher n'a pour l'instant pas d'effet, mais cela n'est que provisoire.

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du tutoriel, consultez [Étape 6 : Nommer vos contrôles bouton](../ide/step-6-name-your-button-controls.md).

- Pour revenir à l’étape précédente du tutoriel, consultez [Étape 4 : Composer votre formulaire avec un contrôle TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).
