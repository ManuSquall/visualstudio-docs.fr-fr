---
title: 'Étape 11 : Exécutez votre application de visionneuse d’images et essayez d’autres fonctionnalités'
ms.date: 09/11/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865064bd85d45ccb24129d289b48143321486ca1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579899"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Étape 11 : Exécutez votre application de visionneuse d’images et essayez d’autres fonctionnalités

Votre application de visionneuse d’images est terminée et prête à fonctionner. Vous pouvez exécuter votre application et <xref:System.Windows.Forms.PictureBox>définir la couleur de fond de la . Pour en savoir plus, essayez d’améliorer l’application en changeant la couleur du formulaire, en personnalisant les boutons et la case à cocher, et en changeant les propriétés du formulaire.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Comment exécuter votre application et définir la couleur de fond

1. Appuyez sur**F5** ou, dans la barre de menus, choisissez **Déboguer** > **Démarrer le débogage**.

1. Avant d’ouvrir une image, choisissez le bouton **Définir la couleur d’arrière-plan**. La boîte de dialogue **Couleur** s’ouvre.

     ![Couleur, boîte de dialogue](../ide/media/express_colordialog.png)<br/>
***Boîte de*** *dialogue de couleur*

1. Choisissez une couleur pour définir la couleur d'arrière-plan du contrôle PictureBox. Regardez attentivement `backgroundButton_Click()` la méthode `BackgroundButton_Click()`(ou, ) pour comprendre comment cela fonctionne.

    > [!NOTE]
    > Vous pouvez charger une image à partir d’Internet en collant son URL dans la boîte de dialogue **Ouvrir un fichier**. Essayez de trouver une image avec un arrière-plan transparent, pour que votre couleur d'arrière-plan soit visible.

1. Choisissez le bouton **Effacer l’image** pour vous assurer qu’elle s’efface. Ensuite, quittez l’application en choisissant le bouton **Close.**

## <a name="try-other-features"></a>Tester d’autres fonctionnalités

* Modifiez la couleur du formulaire et des boutons à l’aide de la propriété **BackColor**.

* Personnalisez vos boutons et votre case à cocher à l’aide des propriétés **Font** et **ForeColor**.

* Modifiez les propriétés**FormBorderStyle** et **ControlBox** de votre formulaire.

* Utilisez les propriétés **AcceptButton** et **CancelButton** de votre formulaire pour que les boutons soient automatiquement sélectionnés quand l’utilisateur appuie sur la touche **Entrée** ou **Échap**. Faites ouvrir l’application open la boîte de dialogue **Open File** lorsque l’utilisateur choisit **Entrez** et fermez la boîte lorsque l’utilisateur choisit **Esc**.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus, passez au tutoriel suivant :

> [!div class="nextstepaction"]
> [Tutorial 2: Créer un quiz de mathématiques chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md)

Pour revenir à l’étape précédente du tutoriel, consultez [Étape 10 : écrire du code pour les boutons supplémentaires et une case à cocher](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Voir aussi

* [Plus de tutoriels C](/visualstudio/get-started/csharp/)
* [Plus de tutoriels de base visuelle](/visualstudio/get-started/visual-basic/)
* [Tutoriel CMD](/cpp/get-started/tutorial-console-cpp)
