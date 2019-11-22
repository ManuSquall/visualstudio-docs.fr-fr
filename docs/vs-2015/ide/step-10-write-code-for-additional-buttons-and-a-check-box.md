---
title: 'Étape 10 : écrire du code pour les boutons supplémentaires et une case à cocher | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c23dc511f0dd45a9d62715ed74bc6e2a05afa9a6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295801"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Étape 10 : écrire du code pour les boutons supplémentaires et une case à cocher
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous êtes maintenant prêt à générer les quatre autres méthodes. Vous pourriez copier et coller ce code, mais pour tirer pleinement parti de ce didacticiel, il serait préférable que vous tapiez le code et que vous utilisiez IntelliSense.

 Ce code ajoute des fonctionnalités aux boutons que vous avez ajoutés précédemment. Sans le code, les boutons n'ont aucun effet. Les boutons utilisent un code dans leurs événements `Click` (et la case à cocher utilise l'événement `CheckChanged`) pour effectuer différentes opérations lorsque vous activez les contrôles. Par exemple, l’événement `clearButton_Click`, qui s’active quand vous choisissez le bouton **Effacer l’image**, efface l’image actuelle en attribuant à sa propriété `Image` la valeur `null` (ou `nothing`). Chaque événement dans le code inclut des commentaires qui expliquent la fonction du code.

 ![lien vers la vidéo](../data-tools/media/playvideo.gif "PlayVideo") Pour obtenir une version vidéo de cette rubrique, consultez [didacticiel 1 : créer une visionneuse d’images dans Visual Basic-vidéo 5](https://go.microsoft.com/fwlink/?LinkId=205216) ou [didacticiel 1 : créer une C# visionneuse d’images dans la vidéo 5](https://go.microsoft.com/fwlink/?LinkId=205206). Ces vidéos utilisent une version antérieure de Visual Studio et présentent donc de légères différences quant à certaines commandes de menu et autres éléments d’interface utilisateur. Toutefois, les concepts et les procédures fonctionnent de façon similaire dans la version actuelle de Visual Studio.

> [!NOTE]
> N'oubliez pas de toujours commenter votre code. Les commentaires sont des informations qu'une personne peut lire, et il est toujours utile de prendre un peu de temps pour détailler les objectifs de votre code. Tout le contenu d'une ligne de commentaire est ignoré par le programme. Pour insérer un commentaire, tapez deux barres obliques au début de la ligne (//) si vous écrivez en Visual C# et un guillemet simple (') si vous écrivez en Visual Basic.

### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Pour écrire du code pour des boutons supplémentaires et une case à cocher

- Ajoutez le code suivant à votre fichier de code Form1 (Form1.cs ou Form1.vb). Sélectionnez l'onglet **VB** pour afficher le code Visual Basic.

     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]

### <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez [Étape 11 : exécuter votre programme et tester d’autres fonctionnalités](../ide/step-11-run-your-program-and-try-other-features.md).

- Pour revenir à l’étape précédente du didacticiel, consultez [Étape 9 : examiner, commenter et tester votre code](../ide/step-9-review-comment-and-test-your-code.md).
