---
title: 'Étape 10 : Écrire du code pour des boutons supplémentaires et une case à cocher'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 19c82238a0379e6b94e82bb1e34f20282ff4654f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930166"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Étape 10 : Écrire du code pour des boutons supplémentaires et une case à cocher
Vous êtes maintenant prêt à générer les quatre autres méthodes. Vous pourriez copier et coller ce code, mais pour tirer pleinement parti de ce didacticiel, il serait préférable que vous tapiez le code et que vous utilisiez IntelliSense.

 Ce code ajoute des fonctionnalités aux boutons que vous avez ajoutés précédemment. Sans le code, les boutons n'ont aucun effet. Les boutons utilisent un code dans leurs événements <xref:System.Windows.Forms.Control.Click> (et la case à cocher utilise l'événement <xref:System.Windows.Forms.CheckBox.CheckedChanged>) pour effectuer différentes opérations lorsque vous activez les contrôles. Par exemple, l’événement `clearButton_Click`, qui s’active quand vous choisissez le bouton **Effacer l’image**, efface l’image actuelle en attribuant à sa propriété **Image** la valeur **null** (ou **rien**). Chaque événement dans le code inclut des commentaires qui expliquent la fonction du code.

 ![lien vers la vidéo](../data-tools/media/playvideo.gif)Pour obtenir une version vidéo de cette rubrique, consultez [Turoriel 1 : Créer une visionneuse d’images en Visual Basic – Vidéo 5](http://go.microsoft.com/fwlink/?LinkId=205216) ou [Tutoriel 1 : Créer une visionneuse d’images en C# - Vidéo 5](http://go.microsoft.com/fwlink/?LinkId=205206). Ces vidéos utilisent une version antérieure de Visual Studio et présentent donc de légères différences quant à certaines commandes de menu et autres éléments d’interface utilisateur. Toutefois, les concepts et les procédures fonctionnent de façon similaire dans la version actuelle de Visual Studio.

> [!NOTE]
>  En guise de bonne pratique, veillez à toujours commenter votre code. Les commentaires sont des informations qu'une personne peut lire, et il est toujours utile de prendre un peu de temps pour détailler les objectifs de votre code. Tout le contenu d'une ligne de commentaire est ignoré par le programme. Pour insérer un commentaire, tapez deux barres obliques au début de la ligne (//) si vous écrivez en Visual C# et un guillemet simple (') si vous écrivez en Visual Basic.

## <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Pour écrire du code pour des boutons supplémentaires et une case à cocher

-   Ajoutez le code suivant à votre fichier de code **Form1** (*Form1.cs* ou *Form1.vb*). Sélectionnez l’onglet **VB** pour afficher le code Visual Basic.

     [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]
     [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

-   Pour passer à l’étape suivante du tutoriel, consultez [Étape 11 : Exécuter votre programme et tester d’autres fonctionnalités](../ide/step-11-run-your-program-and-try-other-features.md).

-   Pour revenir à l’étape précédente du tutoriel, consultez [Étape 9 : Passer en revue, commenter et tester votre code](../ide/step-9-review-comment-and-test-your-code.md).
