---
title: 'Étape 11 : Exécuter votre programme et tester d’autres fonctionnalités'
ms.date: 08/30/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
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
ms.openlocfilehash: 5486aa4d2effa3feb03b31bace7a9cfc86fd9925
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293609"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Étape 11 : Exécuter votre programme et tester d’autres fonctionnalités

Votre programme est terminé et prêt à fonctionner. Vous pouvez l'exécuter et définir la couleur d'arrière-plan du contrôle <xref:System.Windows.Forms.PictureBox>. Pour découvrir d'autres fonctionnalités, essayez d'améliorer le programme en modifiant la couleur du formulaire, en personnalisant les boutons et la case à cocher, et en modifiant les propriétés du formulaire.

## <a name="how-to-run-your-program-and-set-the-background-color"></a>Comment exécuter votre programme et définir la couleur d’arrière-plan

1. Appuyez sur**F5** ou, dans la barre de menus, choisissez **Déboguer** > **Démarrer le débogage**.

1. Avant d’ouvrir une image, choisissez le bouton **Définir la couleur d’arrière-plan**. La boîte de dialogue **Couleur** s’ouvre.

     ![Couleur, boîte de dialogue](../ide/media/express_colordialog.png)<br/>
***Couleur*** *boîte de dialogue*

1. Choisissez une couleur pour définir la couleur d'arrière-plan du contrôle PictureBox. Examinez attentivement la `backgroundButton_Click()` méthode (ou `BackgroundButton_Click()`,) pour comprendre son fonctionnement.

    > [!NOTE]
    > Vous pouvez charger une image à partir d’Internet en collant son URL dans la boîte de dialogue **Ouvrir un fichier**. Essayez de trouver une image avec un arrière-plan transparent, pour que votre couleur d'arrière-plan soit visible.

1. Choisissez le bouton **Effacer l’image** pour vous assurer qu’elle s’efface. Quittez ensuite le programme en choisissant le bouton **Fermer**.

## <a name="try-other-features"></a>Tester d’autres fonctionnalités

* Modifiez la couleur du formulaire et des boutons à l’aide de la propriété **BackColor**.

* Personnalisez vos boutons et votre case à cocher à l’aide des propriétés **Font** et **ForeColor**.

* Modifiez les propriétés**FormBorderStyle** et **ControlBox** de votre formulaire.

* Utilisez les propriétés **AcceptButton** et **CancelButton** de votre formulaire pour que les boutons soient automatiquement sélectionnés quand l’utilisateur appuie sur la touche **Entrée** ou **Échap**. Paramétrez le programme pour qu’il ouvre la boîte de dialogue **Ouvrir un fichier** quand l’utilisateur appuie sur la touche **Entrée** et pour qu’il ferme la boîte de dialogue quand il appuie sur la touche **Échap**.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus, passez au tutoriel suivant :

> [!div class="nextstepaction"]
> [Tutoriel 2 : Créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md)

Pour revenir à l’étape précédente du tutoriel, consultez [Étape 10 : Écrire du code pour des boutons supplémentaires et une case à cocher](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Voir aussi

* [Autres C# didacticiels](/visualstudio/get-started/csharp/)
* [Autres didacticiels de Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++vcwlkEventsTutorial](../ide/getting-started-with-cpp-in-visual-studio.md)
