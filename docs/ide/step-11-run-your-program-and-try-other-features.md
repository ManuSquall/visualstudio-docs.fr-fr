---
title: "Étape 11 : exécuter votre programme et tester d’autres fonctionnalités | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 12
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 019d72fece70586013455bbe74f09b990c9fac80
ms.contentlocale: fr-fr
ms.lasthandoff: 02/22/2017

---
# <a name="step-11-run-your-program-and-try-other-features"></a>Étape 11 : exécuter votre programme et tester d’autres fonctionnalités
Votre programme est terminé et prêt à fonctionner. Vous pouvez l'exécuter et définir la couleur d'arrière-plan du contrôle PictureBox. Pour découvrir d'autres fonctionnalités, essayez d'améliorer le programme en modifiant la couleur du formulaire, en personnalisant les boutons et la case à cocher, et en modifiant les propriétés du formulaire.  
  
 Pour télécharger une version complète de l’exemple, consultez la rubrique [Exemple complet de visionneuse d’images du didacticiel](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).  
  
 ![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo")Pour obtenir une version vidéo de cette rubrique, consultez [Didacticiel 1 : Créer une visionneuse d’images en Visual Basic – Vidéo 5](http://go.microsoft.com/fwlink/?LinkId=205216) ou [Didacticiel 1 : Créer une visionneuse d’images en C# – Vidéo 5](http://go.microsoft.com/fwlink/?LinkId=205206). Ces vidéos utilisent une version antérieure de Visual Studio et présentent donc de légères différences quant à certaines commandes de menu et autres éléments d’interface utilisateur. Toutefois, les concepts et les procédures fonctionnent de façon similaire dans la version actuelle de Visual Studio.  
  
### <a name="to-run-your-program-and-set-the-background-color"></a>Pour exécuter votre programme et définir la couleur d'arrière-plan.  
  
1.  Appuyez sur F5 ou, dans la barre de menus, choisissez **Déboguer**, **Démarrer le débogage**.  
  
2.  Avant d’ouvrir une image, choisissez le bouton **Définir la couleur d’arrière-plan**. La boîte de dialogue **Couleur** s’ouvre.  
  
     ![Couleur, boîte de dialogue](../ide/media/express_colordialog.png "Express_ColorDialog")  
Couleur, boîte de dialogue  
  
3.  Choisissez une couleur pour définir la couleur d'arrière-plan du contrôle PictureBox. Examinez attentivement la méthode `backgroundButton_Click()` pour comprendre son fonctionnement.  
  
    > [!NOTE]
    >  Vous pouvez charger une image à partir d’Internet en collant son URL dans la boîte de dialogue **Ouvrir un fichier**. Essayez de trouver une image avec un arrière-plan transparent, pour que votre couleur d'arrière-plan soit visible.  
  
4.  Choisissez le bouton **Effacer l’image** pour vous assurer qu’elle s’efface. Quittez ensuite le programme en choisissant le bouton **Fermer**.  
  
### <a name="to-try-other-features"></a>Pour essayer d’autres fonctionnalités  
  
-   Modifiez la couleur du formulaire et des boutons à l’aide de la propriété **BackColor**.  
  
-   Personnalisez vos boutons et votre case à cocher à l’aide des propriétés **Font** et **ForeColor**.  
  
-   Modifiez les propriétés**FormBorderStyle** et **ControlBox** de votre formulaire.  
  
-   Utilisez les propriétés **AcceptButton** et **CancelButton** de votre formulaire pour que les boutons soient automatiquement sélectionnés quand l’utilisateur appuie sur la touche Entrée ou Échap. Paramétrez le programme pour qu’il ouvre la boîte de dialogue **Ouvrir un fichier** quand l’utilisateur appuie sur la touche Entrée et pour qu’il ferme la boîte de dialogue quand il appuie sur la touche Échap.  
  
### <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Pour en savoir plus sur la programmation en Visual Studio, consultez [Concepts de programmation](http://msdn.microsoft.com/Library/65c12cca-af4f-4017-886e-2dbc00a189d6).  
  
-   Pour en savoir plus sur Visual Basic, consultez [Développement d’applications avec Visual Basic](/dotnet/visual-basic/developing-apps/index).  
  
-   Pour en savoir plus sur Visual C#, consultez [Introduction au langage C# et au .NET Framework](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework).  
  
-   Pour passer à l’étape suivante du didacticiel, consultez [Didacticiel 2 : créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
-   Pour revenir à l’étape précédente du didacticiel, consultez [Étape 10 : écrire du code pour les boutons supplémentaires et une case à cocher](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
