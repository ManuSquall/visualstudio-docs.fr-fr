---
title: 'Étape 7 : ajouter des composants de dialogue à votre formulaire'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f63397f16e3b2ef1a591a55dc5bfc3171d36d52f
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Étape 7 : ajouter des composants de dialogue à votre formulaire
Pour permettre à votre programme d’ouvrir les fichiers image et de choisir une couleur d’arrière-plan, vous devez ajouter un composant <xref:System.Windows.Forms.OpenFileDialog> et un composant <xref:System.Windows.Forms.ColorDialog> à votre formulaire.  
  
 À certains égards, un composant est semblable à un contrôle. Utilisez la **boîte à outils** pour ajouter un composant à votre formulaire, et la fenêtre **Propriétés** pour définir les propriétés du composant. Mais contrairement à un contrôle, lorsque vous ajoutez un composant, il n'est pas visible dans votre formulaire. À la place, il permet d'utiliser des comportements que vous pouvez déclencher à l'aide de code. Un composant sert, par exemple, à ouvrir une boîte de dialogue **Ouvrir un fichier**.  
  
 ![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo")Pour obtenir une version vidéo de cette rubrique, consultez [Tutoriel 1 : Créer une visionneuse d’images en Visual Basic – Vidéo 3](http://go.microsoft.com/fwlink/?LinkId=205213) ou [Tutoriel 1 : Créer une visionneuse d’images en C# – Vidéo 3](http://go.microsoft.com/fwlink/?LinkId=205202). Ces vidéos utilisent une version antérieure de Visual Studio et présentent donc de légères différences quant à certaines commandes de menu et autres éléments d’interface utilisateur. Toutefois, les concepts et les procédures fonctionnent de façon similaire dans la version actuelle de Visual Studio.  
  
## <a name="to-add-dialog-components-to-your-form"></a>Pour ajouter des composants de boîte de dialogue à votre formulaire  
  
1.  Choisissez le **Concepteur Windows Forms** (**Form1.cs [Design]** ou **Form1.vb [Design])**, puis ouvrez le groupe **Boîtes de dialogue** dans la **boîte à outils**.  
  
    > [!NOTE]
    >  Le groupe **Boîtes de dialogue** dans la **boîte à outils** est doté de composants qui ouvrent de nombreuses boîtes de dialogue utiles. Vous pouvez les utiliser pour ouvrir et enregistrer des fichiers, parcourir des dossiers, ainsi que pour choisir des polices et des couleurs. Dans ce projet, vous utilisez deux composants de dialogue : OpenFileDialog et ColorDialog.  
  
2.  Pour ajouter un composant appelé **openFileDialog1** à votre formulaire, double-cliquez sur **OpenFileDialog**. Pour ajouter un composant appelé **colorDialog1** à votre formulaire, double-cliquez sur **ColorDialog** dans la **boîte à outils**. (Vous l'utiliserez dans la prochaine étape de ce didacticiel.) Une zone, contenant une icône pour chacun des deux composants de boîte de dialogue que vous avez ajoutés, doit s'afficher en bas du **Concepteur Windows Forms** (sous le formulaire de la **visionneuse d'images**), comme indiqué dans l'image suivante.  
  
     ![Composants de boîte de dialogue](../ide/media/express_dialogsadded.png "Express_DialogsAdded")  
Composants de la **boîte de dialogue**  
  
3.  Choisissez l’icône **openFileDialog1** dans la zone située en bas du **Concepteur Windows Forms**. Définissez deux propriétés :  
  
    -   Définissez la propriété **Filter** à la valeur suivante (vous pouvez copier-coller cette valeur) :  

        ```  
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*  
        ```  

    -   Définissez la propriété **Title** à la valeur suivante : **Sélectionner un fichier image**  

         Les paramètres de la propriété **Filter** spécifient les types de fichiers à afficher dans la boîte de dialogue **Sélectionner un fichier image**.  

    > [!NOTE]
    >  Pour voir un exemple de boîte de dialogue **Ouvrir un fichier** dans une application différente, ouvrez le **Bloc-notes** ou **Paint** et, dans la barre de menus, choisissez **Fichier** >  **Ouvrir**. Notez la liste déroulante **Types de fichiers** qui se trouve en bas. Pour cette configuration, vous venez d’utiliser la propriété **Filter** dans le composant **OpenFileDialog**. Notez également que les propriétés **Title** et **Filter** sont affichées en gras dans la fenêtre **Propriétés**. L'IDE utilise ce style pour vous montrer toutes les propriétés dont les valeurs par défaut ont été modifiées.  
  
## <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Pour passer à l’étape suivante du tutoriel, consultez [Étape 8 : écrire du code pour le gestionnaire d’événements du bouton Afficher une image](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).  
  
-   Pour revenir à l’étape précédente du tutoriel, consultez [Étape 6 : affecter un nom à vos contrôles bouton](../ide/step-6-name-your-button-controls.md).
