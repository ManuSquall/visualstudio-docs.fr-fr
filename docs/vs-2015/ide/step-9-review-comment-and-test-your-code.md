---
title: 'Étape 9 : Examiner, commenter et tester votre code | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 090aeb83f6d0480c511acd808498953ae6c01940
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851103"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Étape 9 : examiner, commenter et tester votre code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ensuite, ajoutez un commentaire à votre code. Un commentaire est une annotation qui ne modifie pas le comportement du programme. Il permet à une autre personne qui lit votre code de mieux le comprendre. L'ajout de commentaires à votre code est une bonne habitude à prendre. Une ligne de commentaire est indiquée par deux barres obliques (//) en Visual C# et par un guillemet simple (') en Visual Basic. Après avoir ajouté un commentaire, testez votre programme. Quand vous travaillez sur vos projets, il est recommandé d'exécuter et de tester souvent le code afin que vous puissiez détecter et résoudre les problèmes au plus tôt, avant que le code devienne plus complexe. Cette opération est un *test itératif*.

 Vous venez de générer un programme qui fonctionne, et bien qu'il ne soit pas encore terminé, il peut déjà charger une image. Avant d'ajouter un commentaire à votre code et de le tester, prenez le temps de revoir les concepts de code, car vous serez amené à les utiliser régulièrement :

- Lorsque vous avez double-cliqué sur le bouton **afficher une image** dans Concepteur Windows Forms, l’IDE a ajouté automatiquement une *méthode* au code de votre programme.

- Les méthodes vous permettent d'organiser votre code : c'est ainsi que votre code est regroupé.

- La plupart du temps, une méthode effectue un petit nombre d'actions dans un ordre spécifique, (comme lorsque votre méthode `showButton_Click()` affiche une boîte de dialogue, puis charge une image).

- Une méthode contient des *instructions* ou des lignes de code. En d'autres termes, une méthode permet de regrouper des instructions de code.

- Quand une méthode est exécutée (ou *appelée*), les instructions qu’elle contient s’exécutent dans l’ordre, l’une après l’autre, en commençant par la première.

   Voici un exemple d'instruction.

  ```csharp
  pictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   Les instructions permettent à vos programmes d'effectuer des actions. En Visual C#, une instruction se termine toujours par un point-virgule. En Visual Basic, la fin d'une ligne indique la fin d'une instruction. (Aucun point-virgule n’est nécessaire dans Visual Basic.) L’instruction précédente indique `PictureBox` à votre contrôle de charger le fichier que l’utilisateur a sélectionné avec le composant **OpenFileDialog** .

  ![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo") Pour obtenir une version vidéo de cette rubrique, consultez [didacticiel 1 : créer une visionneuse d’images dans Visual Basic-vidéo 5](https://msdn.microsoft.com/vbasic/gg315356.aspx) ou [didacticiel 1 : créer une visionneuse d’images en C#-vidéo 5](https://msdn.microsoft.com/vcsharp/gg278413.aspx). Ces vidéos utilisent une version antérieure de Visual Studio et présentent donc de légères différences quant à certaines commandes de menu et autres éléments d’interface utilisateur. Toutefois, les concepts et les procédures fonctionnent de façon similaire dans la version actuelle de Visual Studio.

### <a name="to-add-comments"></a>Pour ajouter des commentaires

1. Ajoutez le commentaire suivant à votre code.

     [!code-csharp[VbExpressTutorial1Step9_10#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial1Step9_10#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#1)]

    > [!NOTE]
    > Le gestionnaire d’événements Click du bouton **showButton** est maintenant terminé, et il fonctionne. Vous avez commencé votre code par une instruction `if`. Une instruction `if` vous permet de dire à votre programme : « Vérifie ceci, et si c'est vrai (true), fais cela ». Dans ce cas, vous demandez à votre programme d’ouvrir la boîte de dialogue **ouvrir un fichier** , et si l’utilisateur sélectionne un fichier et choisit le bouton **OK** , chargez ce fichier dans le PictureBox.

    > [!TIP]
    > L’IDE est conçu pour vous aider à écrire votre code rapidement, notamment grâce aux *extraits de code*. Un extrait est un raccourci qui se développe en petit bloc de code.
    >
    >  Vous pouvez consulter tous les extraits de code disponibles. Dans la barre de menus, choisissez **Outils**, **Gestionnaire des extraits de code**. Pour Visual C#, l’extrait de code `if` se trouve dans **Visual C#**. Pour Visual Basic, les extraits de code `if` se trouvent dans **Conditions et boucles**, **Modèles de code**. Vous pouvez utiliser ce gestionnaire pour parcourir les extraits existants ou ajouter les vôtres.
    >
    >  Pour activer un extrait lorsque vous écrivez du code, tapez-le et appuyez sur la touche Tab. De nombreux extraits de code apparaissent dans la fenêtre **IntelliSense** . c’est la raison pour laquelle vous choisissez la touche Tab à deux reprises : tout d’abord pour sélectionner l’extrait de code dans la fenêtre **IntelliSense** , puis pour indiquer à l’IDE d’utiliser l’extrait de code. (IntelliSense prend en charge l'extrait `if`, mais pas `ifelse`.)

2. Avant d’exécuter votre programme, enregistrez-le en choisissant le bouton **Enregistrer tout** (qui se présente comme ci-dessous) dans la barre d’outils.

     ![Bouton enregistrer tout de la barre d’outils](../ide/media/express-iconsaveall.png "Express_IconSaveAll") Bouton enregistrer tout

     Vous pouvez également enregistrer votre programme en choisissant **Fichier**, **Enregistrer tout** dans la barre de menus. Il est conseillé d'enregistrer votre travail régulièrement.

     Lorsqu'il est exécuté, votre programme doit ressembler à l'image suivante.

     ![Visionneuse d’images](../ide/media/express-pictureviewerdonerun.png "Express_PictureViewerDoneRun") Visionneuse d’images

### <a name="to-test-your-program"></a>Pour tester votre programme

1. Appuyez sur la touche F5 ou choisissez le bouton **Démarrer le débogage** dans la barre d’outils.

2. Choisissez le bouton **Afficher une image** pour exécuter le code que vous venez d’écrire. En premier lieu, le programme ouvre une boîte de dialogue **Ouvrir un fichier**. Vérifiez que vos filtres s’affichent dans la liste déroulante **Types de fichiers** en bas de la boîte de dialogue. Ensuite, naviguez jusqu'à une image et ouvrez-la. En général, des échantillons d’images sont fournis avec le système d’exploitation Windows. Ils se trouvent dans votre dossier **Mes documents**, à l’intérieur du dossier **Mes images\Échantillons d’images**.

    > [!NOTE]
    > Si vous ne voyez aucune image dans la boîte de dialogue **Sélectionner un fichier image** , vérifiez que le filtre « tous les fichiers (*. \* ) » est sélectionné dans la liste déroulante située dans la partie inférieure droite de la boîte de dialogue.

3. Chargez une image et elle s'affiche dans votre PictureBox. Essayez ensuite de redimensionner votre formulaire en faisant glisser ses bordures. Étant donné que votre PictureBox est ancré à l’intérieur d’un TableLayoutPanel (lui-même ancré à l’intérieur du formulaire), votre zone d’image se redimensionne automatiquement à la même largeur que le formulaire, et remplit les 90 pour cent supérieurs du formulaire. C'est la raison pour laquelle vous avez utilisé les conteneurs TableLayoutPanel et FlowLayoutPanel : ils permettent à votre formulaire de converser des dimensions correctes lorsque l'utilisateur le redimensionne.

     Pour le moment, les images de grande taille dépassent les bordures de votre visionneuse d'images. Dans l'étape suivante, vous ajouterez du code pour ajuster les images dans la fenêtre.

### <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez [étape 10 : écrire du code pour des boutons supplémentaires et une case à cocher](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

- Pour revenir à l’étape précédente du didacticiel, consultez [étape 8 : écrire du code pour le gestionnaire d’événements du bouton afficher une image](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).
