---
title: 'Étape 11 : Exécutez votre application visionneuse d’images et essayez d’autres fonctionnalités'
ms.date: 09/11/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad0489cce76642df0dd069e0a05e1e50b55d5d8f
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118790"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Étape 11 : Exécutez votre application visionneuse d’images et essayez d’autres fonctionnalités

Votre application visionneuse d’images est terminée et prête à être exécutée. Vous pouvez exécuter votre application et définir la couleur d’arrière- <xref:System.Windows.Forms.PictureBox>plan du. Pour plus d’informations, essayez d’améliorer l’application en modifiant la couleur du formulaire, en personnalisant les boutons et la case à cocher, et en modifiant les propriétés du formulaire.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Comment exécuter votre application et définir la couleur d’arrière-plan

1. Appuyez sur**F5** ou, dans la barre de menus, choisissez **Déboguer** > **Démarrer le débogage**.

1. Avant d’ouvrir une image, choisissez le bouton **Définir la couleur d’arrière-plan**. La boîte de dialogue **Couleur** s’ouvre.

     ![Couleur, boîte de dialogue](../ide/media/express_colordialog.png)<br/>
***Couleur*** *boîte de dialogue*

1. Choisissez une couleur pour définir la couleur d'arrière-plan du contrôle PictureBox. Examinez attentivement la `backgroundButton_Click()` méthode (ou `BackgroundButton_Click()`,) pour comprendre son fonctionnement.

    > [!NOTE]
    > Vous pouvez charger une image à partir d’Internet en collant son URL dans la boîte de dialogue **Ouvrir un fichier**. Essayez de trouver une image avec un arrière-plan transparent, pour que votre couleur d'arrière-plan soit visible.

1. Choisissez le bouton **Effacer l’image** pour vous assurer qu’elle s’efface. Ensuite, quittez l’application en choisissant le bouton **Fermer** .

## <a name="try-other-features"></a>Tester d’autres fonctionnalités

* Modifiez la couleur du formulaire et des boutons à l’aide de la propriété **BackColor**.

* Personnalisez vos boutons et votre case à cocher à l’aide des propriétés **Font** et **ForeColor**.

* Modifiez les propriétés**FormBorderStyle** et **ControlBox** de votre formulaire.

* Utilisez les propriétés **AcceptButton** et **CancelButton** de votre formulaire pour que les boutons soient automatiquement sélectionnés quand l’utilisateur appuie sur la touche **Entrée** ou **Échap**. Rendre l’application ouverte la boîte de dialogue **ouvrir un fichier** lorsque l’utilisateur choisit **Enter** et ferme la zone lorsque l’utilisateur choisit **ESC**.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus, passez au tutoriel suivant :

> [!div class="nextstepaction"]
> [Tutoriel 2 : Créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md)

Pour revenir à l’étape précédente du tutoriel, consultez [Étape 10 : Écrire du code pour des boutons supplémentaires et une case à cocher](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Voir aussi

* [Autres C# didacticiels](/visualstudio/get-started/csharp/)
* [Autres didacticiels de Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++vcwlkEventsTutorial](/cpp/get-started/tutorial-console-cpp)
