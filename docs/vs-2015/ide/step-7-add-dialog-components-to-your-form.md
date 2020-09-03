---
title: 'Étape 7 : Ajouter des composants de boîte de dialogue à votre formulaire | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40b90096f768a7dd836507c83dff935261a99a25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851142"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Étape 7 : ajouter des composants Dialog à votre formulaire
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour permettre à votre programme d’ouvrir les fichiers image et de choisir une couleur d’arrière-plan, vous devez maintenant ajouter un composant **OpenFileDialog** et un composant **ColorDialog** à votre formulaire.

 À certains égards, un composant est semblable à un contrôle. Utilisez la boîte à outils pour ajouter un composant à votre formulaire, et la fenêtre **Propriétés** pour définir les propriétés du composant. Mais contrairement à un contrôle, lorsque vous ajoutez un composant, il n'est pas visible dans votre formulaire. À la place, il permet d'utiliser des comportements que vous pouvez déclencher à l'aide de code. Un composant sert, par exemple, à ouvrir une boîte de dialogue **Ouvrir un fichier**.

 ![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo") Pour obtenir une version vidéo de cette rubrique, consultez [didacticiel 1 : créer une visionneuse d’images dans Visual Basic-vidéo 3](https://msdn.microsoft.com/vbasic/gg315354.aspx) ou [didacticiel 1 : créer une visionneuse d’images en C#-vidéo 3](https://msdn.microsoft.com/vcsharp/gg278411.aspx). Ces vidéos utilisent une version antérieure de Visual Studio et présentent donc de légères différences quant à certaines commandes de menu et autres éléments d’interface utilisateur. Toutefois, les concepts et les procédures fonctionnent de façon similaire dans la version actuelle de Visual Studio.

### <a name="to-add-dialog-components-to-your-form"></a>Pour ajouter des composants de boîte de dialogue à votre formulaire

1. Choisissez le Concepteur Windows Forms (Form1.cs [Design] ou Form1. vb [Design]), puis ouvrez le groupe **boîtes de dialogue** dans la boîte à outils.

    > [!NOTE]
    > Le groupe **Boîtes de dialogue** dans la boîte à outils est doté de composants qui ouvrent de nombreuses boîtes de dialogue utiles. Vous pouvez les utiliser pour ouvrir et enregistrer des fichiers, parcourir des dossiers, ainsi que pour choisir des polices et des couleurs. Dans ce projet, vous utilisez deux composants de boîte de dialogue : **OpenFileDialog** et **ColorDialog**.

2. Pour ajouter un composant appelé **openFileDialog1** à votre formulaire, double-cliquez sur **OpenFileDialog**. Pour ajouter un composant appelé **colorDialog1** à votre formulaire, double-cliquez sur **ColorDialog** dans la boîte à outils. (Vous l’utilisez dans l’étape suivante du didacticiel.) Vous devez voir une zone en bas de Concepteur Windows Forms (sous le formulaire de la visionneuse d’images) qui contient une icône pour chacun des deux composants de boîte de dialogue que vous avez ajoutés, comme illustré dans l’image suivante.

     ![Composants de boîte de dialogue](../ide/media/express-dialogsadded.png "Express_DialogsAdded") Composants de boîte de dialogue

3. Choisissez l’icône **OpenFileDialog1** dans la zone située en bas de la Concepteur Windows Forms. Définissez deux propriétés :

    - Définissez la propriété **Filter** à la valeur suivante (vous pouvez copier-coller cette valeur) :

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Définissez la propriété **Title** à la valeur suivante : **Sélectionner un fichier image**

         Les paramètres de la propriété **Filter** spécifient les types de fichiers à afficher dans la boîte de dialogue **Sélectionner un fichier image**.

    > [!NOTE]
    > Pour voir un exemple de boîte de dialogue **Ouvrir un fichier** dans une application différente, ouvrez le Bloc-notes ou Paint et, dans la barre de menus, choisissez **Fichier**, **Ouvrir**. Notez la liste déroulante **Types de fichiers** qui se trouve en bas. Pour cette configuration, vous venez d’utiliser la propriété **Filter** dans le composant **OpenFileDialog**. Notez également que les propriétés **Title** et **Filter** sont affichées en gras dans la fenêtre **Propriétés**. L'IDE utilise ce style pour vous montrer toutes les propriétés dont les valeurs par défaut ont été modifiées.

### <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez [étape 8 : écrire du code pour le gestionnaire d’événements du bouton afficher une image](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

- Pour revenir à l’étape précédente du didacticiel, consultez [étape 6 : nommer vos contrôles bouton](../ide/step-6-name-your-button-controls.md).
