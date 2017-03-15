---
title: "Étape 9 : Tester d’autres fonctionnalités | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 11
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: 9d5e8a86d71cf1f6aa47853b862a4668dea05633
ms.lasthandoff: 02/22/2017

---
# <a name="step-9-try-other-features"></a>Étape 9 : Tester d’autres fonctionnalités
Pour découvrir d'autres fonctionnalités, essayez de modifier les icônes et les couleurs, d'ajouter une horloge de jeu et d'ajouter des sons. Pour augmenter la difficulté du jeu, essayez d'agrandir la taille du plateau et d'ajuster la minuterie.  
  
 Pour télécharger une version complète de l’exemple, consultez [Exemple complet de didacticiel de création d’un jeu de combinaisons](http://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).  
  
### <a name="to-try-other-features"></a>Pour essayer d’autres fonctionnalités  
  
-   Remplacez les icônes et les couleurs par d'autres de votre choix.  
  
    > [!TIP]
    >  Examinez la propriété [Forecolor](http://msdn.microsoft.com/library/system.windows.forms.control.forecolor.aspx) du contrôle Label.  
  
-   Ajoutez une horloge de jeu qui relèvera le temps requis par le joueur pour gagner.  
  
    > [!TIP]
    >  Pour cela, vous pouvez ajouter un contrôle Label pour afficher sur le formulaire le temps écoulé au-dessus du TableLayoutPanel et ajouter une autre horloge au formulaire pour relever le temps. Utilisez le code pour démarrer l'horloge lorsque le joueur commence à jouer et arrêter l'horloge lorsque la dernière paire est indiquée.  
  
-   Ajoutez un son lorsque le joueur trouve une paire identique, un autre lorsqu'il sélectionne deux icônes différentes et un troisième lorsque le programme masque à nouveau les icônes.  
  
    > [!TIP]
    >  Pour émettre des sons, vous pouvez utiliser l'espace de noms System.media. Pour plus d’informations, consultez [Lire des sons dans une application Windows Forms (C# .NET)](http://youtu.be/qOh4ooHg1UU) ou [Comment lire de l’audio dans Visual Basic](http://youtu.be/-4oPDeQrtMs).  
  
-   Augmentez la difficulté du jeu en agrandissant la taille du plateau.  
  
    > [!TIP]
    >  Vous ne devez pas seulement ajouter des lignes et des colonnes au TableLayoutPanel – vous devez également considérer le nombre d'icônes que vous créez.  
  
-   Augmentez la difficulté du jeu en masquant la première icône si le joueur réagit trop lentement et ne choisit pas la deuxième icône dans un délai imparti.  
  
### <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Si vous êtes bloqué ou avez des questions liées à la programmation, essayez de publier votre question sur l'un des forums MSDN. Consultez le [Forum Visual Basic](http://social.msdn.microsoft.com/Forums/home?forum=vbgeneral) et [Forum Visual C#](http://social.msdn.microsoft.com/Forums/home?forum=csharpgeneral).  
  
-   Des ressources vidéo d'apprentissage efficaces et gratuites sont à votre disposition. Pour en savoir plus sur la programmation en Visual Basic, consultez [Notions de base de Visual Basic : développement pour les débutants](http://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Pour en savoir plus sur la programmation en C#, consultez [Notions de base de C# : développement pour les débutants](http://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).  
  
-   Pour revenir à l’étape précédente du didacticiel, consultez [Étape 8 : Ajouter une méthode pour vérifier si le joueur a gagné](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
