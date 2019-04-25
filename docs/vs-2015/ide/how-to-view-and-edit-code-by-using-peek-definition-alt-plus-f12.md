---
title: 'Procédure : Afficher et modifier le Code à l’aide d’aperçu de définition (Alt + F12) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 45f3dd20-902a-4047-8cca-9f18216123f4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a4c170b533b1eadb60be2ec1ca5d5fe000c5b4d6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60055729"
---
# <a name="how-to-view-and-edit-code-by-using-peek-definition-altf12"></a>Procédure : Afficher et modifier le Code à l’aide d’aperçu de définition (Alt + F12)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Utilisez la commande **Aperçu de définition** pour afficher et modifier du code sans sortir du code que vous écrivez. Les options **Aperçu de définition** et **Atteindre la définition** affichent les mêmes informations, mais **Aperçu de définition** affiche le code dans une fenêtre contextuelle, alors que l’option **Atteindre la définition** affiche le code dans une fenêtre de code distincte. L’option **Atteindre la définition** provoque le basculement de votre contexte (c’est-à-dire, la fenêtre de code active, la ligne active et la position du curseur) vers la fenêtre du code de définition. Avec l’option **Aperçu de définition**, vous pouvez afficher et modifier la définition et vous déplacer dans le fichier de définition tout en conservant votre position dans le fichier de code d’origine.  
  
 Vous pouvez utiliser **Aperçu de définition** avec du code C#, Visual Basic et C++. En Visual Basic, l’option **Aperçu de définition** affiche un lien vers l’**Explorateur d’objets** pour les symboles qui ne disposent pas de métadonnées de définition (par exemple, les types .NET Framework intégrés).  
  
> [!IMPORTANT]
>  Vous ne pouvez pas utiliser cette commande dans une version Express de Visual Studio 2013.  
  
## <a name="working-with-peek-definition"></a>Utilisation de l'option Aperçu de définition  
  
#### <a name="to-open-a-peek-definition-window"></a>Pour ouvrir une fenêtre Aperçu de définition  
  
1. Vous pouvez trouver l’option **Aperçu de définition** en ouvrant le menu contextuel d’une méthode que vous voulez explorer. (Clavier : Alt+F12)  
  
     Cette illustration représente la fenêtre **Aperçu de définition** pour une méthode nommée `Print()` :  
  
     ![Fenêtre d’aperçu](../ide/media/peekwindow.png "PeekWindow")  
  
     La fenêtre de définition apparaît sous la ligne `printer.Print(“Hello World!”)` du fichier d'origine. La fenêtre ne masque aucune partie du code de votre fichier d'origine. Les lignes qui suivent l'appel `printer.Print(“Hello World!”)` apparaissent sous la fenêtre de définition.  
  
2. Vous pouvez déplacer le curseur vers différents emplacements dans la fenêtre de définition du code. Vous pouvez encore vous déplacer dans la fenêtre de code d'origine au-dessus ou au-dessous de la fenêtre de définition.  
  
3. Vous pouvez copier une chaîne dans la fenêtre de définition et la coller dans le code d'origine. Vous pouvez également effectuer un glisser-déposer de la chaîne de la fenêtre de définition vers le code d’origine sans la supprimer dans la fenêtre de définition.  
  
4. Vous pouvez fermer la fenêtre de définition en choisissant la touche Échap ou le bouton **Fermer** dans l’onglet de la fenêtre de définition.  
  
#### <a name="to-open-a-peek-definition-window-from-within-a-peek-definition-window"></a>Pour ouvrir une fenêtre Aperçu de définition à partir d'une fenêtre Aperçu de définition  
  
- Si une fenêtre **Aperçu de définition** est déjà ouverte, vous pouvez appeler de nouveau **Aperçu de définition** sur le code affiché dans cette fenêtre. Une autre fenêtre de définition s'ouvre. Un ensemble de points de navigation apparaissent en regard de l'onglet de la fenêtre de définition. Vous pouvez les utiliser pour naviguer entre les fenêtres de définition. L’info-bulle sur chaque point indique le nom et le chemin du fichier de définition que le point représente.  
  
     ![Fenêtre d’aperçu dans une fenêtre d’aperçu](../ide/media/peekwithinpeek.png "PeekWithinPeek")  
  
#### <a name="to-use-peek-definition-with-multiple-results"></a>Pour utiliser l'option Aperçu de définition avec plusieurs résultats  
  
- Si vous utilisez l’option **Aperçu de définition** sur du code possédant plusieurs définitions (par exemple, des classes partielles), une liste de résultats apparaît à droite de la vue Définition de code. Vous pouvez choisir un résultat quelconque dans la liste pour afficher sa définition.  
  
     ![Fenêtre d’aperçu de plusieurs résultats](../ide/media/peekmultiple.png "PeekMultiple")  
  
#### <a name="to-edit-inside-the-peek-definition-window"></a>Pour apporter des modifications dans la fenêtre Aperçu de définition  
  
- Lorsque vous commencez à apporter des modifications dans une fenêtre **Aperçu de définition**, le fichier que vous modifiez s’ouvre automatiquement dans un onglet distinct dans l’éditeur de code et reflète les modifications déjà effectuées. Vous pouvez continuer à apporter, annuler et enregistrer des modifications dans la fenêtre **Aperçu de définition** et l’onglet continuera à refléter ces modifications. Même si vous fermez la fenêtre sans enregistrer les modifications, vous pouvez apporter, annuler et enregistrer des modifications supplémentaires dans l'onglet, en reprenant exactement là où vous vous êtes arrêté dans la fenêtre.  
  
     ![Modification dans une fenêtre d’aperçu](../ide/media/peekedit.png "PeekEdit")  
  
#### <a name="to-use-keyboard-shortcuts-for-peek-definition"></a>Pour utiliser des raccourcis clavier pour l'option Aperçu de définition  
  
- Vous pouvez utiliser les raccourcis clavier suivants avec la fenêtre **Aperçu de définition** :  
  
    |Fonctionnalité|Raccourci clavier|  
    |-------------------|-----------------------|  
    |Ouvrir la fenêtre de définition|Alt+F12|  
    |Fermer la fenêtre de définition|Échap|  
    |Promouvoir la fenêtre de définition en onglet de document standard|Maj+Alt+Début|  
    |Naviguer entre les fenêtres de définition|Ctrl+Alt+- et Ctrl+Alt+=|  
    |Naviguer entre plusieurs résultats|F8 et Maj+F8|  
    |Permuter entre la fenêtre de l'éditeur de code et la fenêtre de définition|Maj+Échap|  
  
    > [!NOTE]
    >  Pour modifier le code dans une fenêtre **Aperçu de définition**, vous pouvez utiliser les mêmes raccourcis clavier que vous utilisez ailleurs dans Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Conseils de productivité](../ide/productivity-tips-for-visual-studio.md)
