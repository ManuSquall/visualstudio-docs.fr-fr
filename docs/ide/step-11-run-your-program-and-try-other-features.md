---
title: Exécutez votre application visionneuse d’images et essayez d’autres fonctionnalités
description: Exécutez votre application visionneuse d’images et essayez d’autres fonctionnalités dans le didacticiel créer une visionneuse d’images.
ms.date: 09/11/2019
ms.custom: SEO-VS-2020
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1a4488c212cabe95d73f75246fb297c17ce073b4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950898"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Étape 11 : exécuter votre application visionneuse d’images et essayer d’autres fonctionnalités

Votre application visionneuse d’images est terminée et prête à être exécutée. Vous pouvez exécuter votre application et définir la couleur d’arrière-plan du <xref:System.Windows.Forms.PictureBox> . Pour plus d’informations, essayez d’améliorer l’application en modifiant la couleur du formulaire, en personnalisant les boutons et la case à cocher, et en modifiant les propriétés du formulaire.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Comment exécuter votre application et définir la couleur d’arrière-plan

1. Appuyez sur **F5** ou, dans la barre de menus, choisissez **Déboguer** > **Démarrer le débogage**.

1. Avant d’ouvrir une image, choisissez le bouton **Définir la couleur d’arrière-plan**. La boîte de dialogue **Couleur** s’ouvre.

     ![Couleur, boîte de dialogue](../ide/media/express_colordialog.png)<br/>
***Couleur** _ _dialog zone *

1. Choisissez une couleur pour définir la couleur d'arrière-plan du contrôle PictureBox. Examinez attentivement la `backgroundButton_Click()` méthode (ou, `BackgroundButton_Click()` ) pour comprendre son fonctionnement.

    > [!NOTE]
    > Vous pouvez charger une image à partir d’Internet en collant son URL dans la boîte de dialogue **Ouvrir un fichier**. Essayez de trouver une image avec un arrière-plan transparent, pour que votre couleur d'arrière-plan soit visible.

1. Choisissez le bouton **Effacer l’image** pour vous assurer qu’elle s’efface. Ensuite, quittez l’application en choisissant le bouton **Fermer** .

## <a name="try-other-features"></a>Tester d’autres fonctionnalités

* Modifiez la couleur du formulaire et des boutons à l’aide de la propriété **BackColor**.

* Personnalisez vos boutons et votre case à cocher à l’aide des propriétés **Font** et **ForeColor**.

* Modifiez les propriétés **FormBorderStyle** et **ControlBox** de votre formulaire.

* Utilisez les propriétés **AcceptButton** et **CancelButton** de votre formulaire pour que les boutons soient automatiquement sélectionnés quand l’utilisateur appuie sur la touche **Entrée** ou **Échap**. Rendre l’application ouverte la boîte de dialogue **ouvrir un fichier** lorsque l’utilisateur choisit **Enter** et ferme la zone lorsque l’utilisateur choisit **ESC**.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus, passez au tutoriel suivant :

> [!div class="nextstepaction"]
> [Didacticiel 2 : créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md)

Pour revenir à l’étape précédente du tutoriel, consultez [Étape 10 : écrire du code pour les boutons supplémentaires et une case à cocher](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Voir aussi

* [Autres didacticiels C#](../get-started/csharp/index.yml)
* [Autres didacticiels de Visual Basic](../get-started/visual-basic/index.yml)
* [Didacticiel C++](/cpp/get-started/tutorial-console-cpp)