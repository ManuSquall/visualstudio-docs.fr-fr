---
title: 'Didacticiel 1 : Créer une visionneuse d’images | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ad57a05e45b7e9acd3db455f0a8849166dc3c735
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654760"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Didacticiel 1 : créer une visionneuse d'images
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans ce didacticiel, vous générez un programme qui charge une image à partir d'un fichier et l'affiche dans une fenêtre. Vous apprenez à faire glisser des contrôles (par exemple, des boutons et des zones d'image) sur votre formulaire, définir leurs propriétés et utiliser des conteneurs pour redimensionner facilement le formulaire. Vous commencez également à écrire du code. Vous apprenez à :

- Créer un nouveau projet.

- Tester (déboguer) une application.

- Ajouter des contrôles de base, comme des cases à cocher et des boutons, à un formulaire.

- Positionner des contrôles sur un formulaire à l'aide de dispositions.

- Ajouter des boîtes de dialogue **Ouvrir un fichier** et **Couleur** à un formulaire.

- Écrire du code à l'aide d'IntelliSense et d'extraits de code.

- Écrire des méthodes de gestionnaire d'événements.

  Lorsque vous aurez terminé, votre programme ressemblera à l'image suivante.

  ![Image créée dans ce didacticiel](../ide/media/express-pictureviewerdone.png "Express_PictureViewerDone") Image créée dans ce didacticiel

  Pour télécharger une version complète de l’exemple, consultez la rubrique [Exemple complet de visionneuse d’images du didacticiel](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).

  ![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo") Pour obtenir une version vidéo de cette rubrique, consultez [comment créer une visionneuse d’images dans Visual Basic ?](http://go.microsoft.com/fwlink/?LinkId=205207) ou [Comment faire : créer une visionneuse d’images C#dans ?](http://go.microsoft.com/fwlink/?LinkId=205198).

> [!NOTE]
> Ces vidéos utilisent une version antérieure de Visual Studio et présentent donc de légères différences quant à certaines commandes de menu et autres éléments d’interface utilisateur. Toutefois, les concepts et les procédures fonctionnent de façon similaire dans la version actuelle de Visual Studio. Visual C# et Visual Basic sont tous deux traités dans ce didacticiel. Ne tenez compte que des informations spécifiques au langage de programmation que vous utilisez.
>
> Pour afficher le code pour Visual Basic, choisissez l’onglet **VB** en haut des blocs de code, et pour afficher le code C#pour Visual, **C#** choisissez l’onglet. Si vous souhaitez en savoir plus sur Visual C++, consultez le didacticiel [prise en main](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) et [ C++ langage](http://www.cplusplus.com/doc/tutorial/).
>
> Si vous souhaitez savoir comment écrire des applications Visual C# ou Visual Basic pour le Windows Store, consultez [Créer votre première application du Windows Store en C# ou Visual Basic](https://msdn.microsoft.com/library/windows/apps/hh974581.aspx). Pour plus d’informations sur la création d’applications JavaScript pour le Windows Store, consultez [Créer votre première application du Windows Store en JavaScript](https://msdn.microsoft.com/library/windows/apps/br211385.aspx).

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Étape 1 : créer un projet d’application Windows Forms](../ide/step-1-create-a-windows-forms-application-project.md)|Commencez par créer un projet d’application Windows Forms.|
|[Étape 2 : exécuter votre programme](../ide/step-2-run-your-program.md)|Exécutez le programme d’application Windows Forms que vous avez créé dans l’étape précédente.|
|[Étape 3 : définir les propriétés de votre formulaire](../ide/step-3-set-your-form-properties.md)|Modifiez l’apparence de votre formulaire à l’aide de la fenêtre **Propriétés**.|
|[Étape 4 : composer votre formulaire avec un contrôle TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Ajoutez un contrôle `TableLayoutPanel` à votre formulaire.|
|[Étape 5 : ajouter des contrôles à votre formulaire](../ide/step-5-add-controls-to-your-form.md)|Ajoutez des contrôles à votre formulaire (notamment des contrôles `PictureBox` et `CheckBox`). Ajoutez des boutons à votre formulaire.|
|[Étape 6 : affecter un nom à vos contrôles bouton](../ide/step-6-name-your-button-controls.md)|Renommez vos boutons en leur donnant des noms plus explicites.|
|[Étape 7 : ajouter des composants de dialogue à votre formulaire](../ide/step-7-add-dialog-components-to-your-form.md)|Ajoutez un composant **OpenFileDialog** et un composant **ColorDialog** à votre formulaire.|
|[Étape 8 : écrire du code pour le gestionnaire d’événements du bouton Afficher une image](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|Écrivez du code à l'aide de l'outil IntelliSense.|
|[Étape 9 : examiner, commenter et tester votre code](../ide/step-9-review-comment-and-test-your-code.md)|Vérifiez et testez votre code. Ajoutez autant de commentaires que nécessaire.|
|[Étape 10 : écrire du code pour les boutons supplémentaires et une case à cocher](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|Écrivez du code à l'aide d'IntelliSense pour faire fonctionner d'autres boutons et une case à cocher.|
|[Étape 11 : exécuter votre programme et tester d’autres fonctionnalités](../ide/step-11-run-your-program-and-try-other-features.md)|Exécutez votre programme et définissez la couleur d'arrière-plan. Essayez d'autres fonctionnalités, telles que la modification des couleurs, des polices et des bordures.|
