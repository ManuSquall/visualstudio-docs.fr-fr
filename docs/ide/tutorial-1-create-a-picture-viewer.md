---
title: "Tutoriel 1 : créer une visionneuse d'images"
ms.date: 10/16/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f1431d56516c749004cef1b35ada482a6c53446
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579727"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Tutoriel 1 : créer une visionneuse d'images

Dans ce tutoriel, vous construisez une application qui charge une image à partir d’un fichier et l’affiche dans une fenêtre. Vous apprenez à utiliser le **concepteur de formulaires Windows** pour faire glisser les commandes comme les boutons et les boîtes d’image sur votre formulaire, définir leurs propriétés, et utiliser des conteneurs pour resize en douceur le formulaire. Vous commencez également à écrire du code.

> [!NOTE]
> Ce tutoriel couvre à la fois C et Visual Basic, alors concentrez-vous sur les informations spécifiques au langage de programmation que vous utilisez.

Ce tutoriel vous guide à travers les tâches suivantes:

* Créez un projet.

* Tester (déboguer) une application.

* Ajouter des contrôles de base, comme des cases à cocher et des boutons, à un formulaire.

* Contrôle de position sur un formulaire en utilisant des mises en page.

* Ajouter des boîtes de dialogue **Ouvrir un fichier** et **Couleur** à un formulaire.

* Écrivez du code en utilisant IntelliSense et des extraits de code.

* Écrire des méthodes de gestionnaire d'événements.

Lorsque vous avez terminé, votre application doit ressembler à l’image suivante :

![Application Picture Viewer que vous créez dans ce tutoriel](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>Liens de tutoriels

|Intitulé|Description|
|-----------|-----------------|
|[Étape 1 : Créer un projet Windows Forms App](../ide/step-1-create-a-windows-forms-application-project.md)|Commencez par créer un projet Windows Forms App.|
|[Étape 2 : Exécutez votre application de visionneuse d’images](../ide/step-2-run-your-program.md)|Exécutez le projet Windows Forms App que vous avez créé dans l’étape précédente.|
|[Étape 3 : Définissez vos propriétés de formulaire](../ide/step-3-set-your-form-properties.md)|Modifiez l’apparence de votre formulaire à l’aide de la fenêtre **Propriétés**.|
|[Étape 4 : Présentez votre formulaire avec un contrôle TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Ajoutez un contrôle `TableLayoutPanel` à votre formulaire.|
|[Étape 5 : Ajoutez des commandes à votre formulaire](../ide/step-5-add-controls-to-your-form.md)|Ajoutez des contrôles à votre formulaire (notamment des contrôles `PictureBox` et `CheckBox`). Ajoutez des boutons à votre formulaire.|
|[Étape 6 : Nommez vos commandes de bouton](../ide/step-6-name-your-button-controls.md)|Renommez vos boutons en leur donnant des noms plus explicites.|
|[Étape 7 : ajouter des composants de dialogue à votre formulaire](../ide/step-7-add-dialog-components-to-your-form.md)|Ajoutez un composant `OpenFileDialog` et un composant `ColorDialog` à votre formulaire.|
|[Étape 8 : Écrivez du code pour afficher un gestionnaire d’événement de bouton d’image](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Écrivez du code en utilisant l’outil IntelliSense.|
|[Étape 9 : Examinez, commentez et testez votre code](../ide/step-9-review-comment-and-test-your-code.md)|Vérifiez et testez votre code. Ajoutez autant de commentaires que nécessaire.|
|[Étape 10 : Écrivez du code pour des boutons supplémentaires et une case à cocher](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Écrivez du code à l'aide d'IntelliSense pour faire fonctionner d'autres boutons et une case à cocher.|
|[Étape 11 : Exécutez votre application et essayez d’autres fonctionnalités](../ide/step-11-run-your-program-and-try-other-features.md)|Exécutez votre application et définissez la couleur de fond. Essayez d'autres fonctionnalités, telles que la modification des couleurs, des polices et des bordures.|

Il ya aussi d’excellentes ressources d’apprentissage vidéo gratuit à votre disposition. Pour en savoir plus sur la programmation dans le domaine de la programmation, consultez [les principes fondamentaux de CMD : Développement pour les débutants absolus.](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) Pour en savoir plus sur la programmation en Visual Basic, consultez [Notions de base de Visual Basic : développement pour grands débutants](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Étapes suivantes

Pour commencer le tutoriel, commencez par **[l’étape 1: Créer un projet d’application Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)**.

## <a name="see-also"></a>Voir aussi

* [Plus de tutoriels C](/visualstudio/get-started/csharp/)
* [Tutoriels Visual Basic](/visualstudio/get-started/visual-basic/)
* [Tutoriels CMD](/cpp/get-started/tutorial-console-cpp)
