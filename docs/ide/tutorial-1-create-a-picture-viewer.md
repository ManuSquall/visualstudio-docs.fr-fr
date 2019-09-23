---
title: 'Tutoriel 1 : Créer une visionneuse d’images'
ms.date: 08/30/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d9a525ef9da6583a37d5e4d26bfec7d0558cde4
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118665"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Tutoriel 1 : Créer une visionneuse d’images

Dans ce didacticiel, vous allez créer une application qui charge une image à partir d’un fichier et l’affiche dans une fenêtre. Vous apprenez à utiliser la **Concepteur Windows Forms** pour faire glisser des contrôles tels que des boutons et des zones d’image sur votre formulaire, définir leurs propriétés et utiliser des conteneurs pour redimensionner facilement le formulaire. Vous commencez également à écrire du code.

> [!NOTE]
> Ce didacticiel couvre à la fois Visual C# et Visual Basic : ne tenez compte que des informations spécifiques au langage de programmation que vous utilisez.

Ce didacticiel vous guide tout au long des tâches suivantes :

* Créer un nouveau projet.

* Tester (déboguer) une application.

* Ajouter des contrôles de base, comme des cases à cocher et des boutons, à un formulaire.

* Positionner des contrôles sur un formulaire à l’aide de dispositions.

* Ajouter des boîtes de dialogue **Ouvrir un fichier** et **Couleur** à un formulaire.

* Écrire du code à l’aide d’IntelliSense et d’extraits de code.

* Écrire des méthodes de gestionnaire d'événements.

Lorsque vous avez terminé, votre application doit ressembler à l’image suivante :

![Application visionneuse d’images que vous créez dans ce didacticiel](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Liens de tutoriels

|Titre|Description|
|-----------|-----------------|
|[Étape 1 : Créer un projet d’application Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Commencez par créer un projet d’application Windows Forms.|
|[Étape 2 : Exécuter votre application visionneuse d’images](../ide/step-2-run-your-program.md)|Exécutez le projet d’application Windows Forms que vous avez créé à l’étape précédente.|
|[Étape 3 : Définir les propriétés de votre formulaire](../ide/step-3-set-your-form-properties.md)|Modifiez l’apparence de votre formulaire à l’aide de la fenêtre **Propriétés**.|
|[Étape 4 : Composer votre formulaire avec un contrôle TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Ajoutez un contrôle `TableLayoutPanel` à votre formulaire.|
|[Étape 5 : Ajouter des contrôles à votre formulaire](../ide/step-5-add-controls-to-your-form.md)|Ajoutez des contrôles à votre formulaire (notamment des contrôles `PictureBox` et `CheckBox`). Ajoutez des boutons à votre formulaire.|
|[Étape 6 : Nommer vos contrôles bouton](../ide/step-6-name-your-button-controls.md)|Renommez vos boutons en leur donnant des noms plus explicites.|
|[Étape 7 : Ajouter des composants de boîte de dialogue à votre formulaire](../ide/step-7-add-dialog-components-to-your-form.md)|Ajoutez un composant `OpenFileDialog` et un composant `ColorDialog` à votre formulaire.|
|[Étape 8 : Écrire du code pour le gestionnaire d’événements du bouton Afficher une image](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Écrivez du code à l’aide de l’outil IntelliSense.|
|[Étape 9 : Passer en revue, commenter et tester votre code](../ide/step-9-review-comment-and-test-your-code.md)|Vérifiez et testez votre code. Ajoutez autant de commentaires que nécessaire.|
|[Étape 10 : Écrire du code pour des boutons supplémentaires et une case à cocher](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Écrivez du code à l'aide d'IntelliSense pour faire fonctionner d'autres boutons et une case à cocher.|
|[Étape 11 : Exécuter votre application et essayer d’autres fonctionnalités](../ide/step-11-run-your-program-and-try-other-features.md)|Exécutez votre application et définissez la couleur d’arrière-plan. Essayez d'autres fonctionnalités, telles que la modification des couleurs, des polices et des bordures.|

## <a name="next-steps"></a>Étapes suivantes

Pour commencer le didacticiel, commencez à  **[l’étape 1 : Créez un projet](../ide/step-1-create-a-windows-forms-application-project.md)** d’application Windows Forms.

## <a name="see-also"></a>Voir aussi

* [Autres C# didacticiels](/visualstudio/get-started/csharp/)
* [Didacticiels de Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++gratuits](/cpp/get-started/tutorial-console-cpp)
