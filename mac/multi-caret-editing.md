---
title: Modification avec signes insertion multiples
description: Insérez du texte à plusieurs endroits lors de l’édition de code dans Visual Studio pour Mac.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451446"
---
# <a name="multi-caret-editing"></a>Modification avec signes insertion multiples

L’édition multi-soins vous permet d’ajouter _n_ n nombre de points d’insertion à une seule fois. Lorsque vous êtes en mode multi-caret, vous pouvez ajouter des carets supplémentaires à votre document, soit via des clics de souris, soit via des commandes de clavier. Le caret primaire est dénoté par un curseur rouge, tandis que les carets secondaires présents dans une couleur bleu clair. Le mode d’édition multi-soins `ESC` peut être désactivé via la clé.

## <a name="enabling-multi-caret-editing"></a>Permettre l’édition multi-caret

### <a name="keyboard"></a>Clavier

Vous êtes en mesure d’activer le mode multi-caret via le clavier de plusieurs façons. Le tableau suivant fournit les raccourcis clavier disponibles pour entrer des modes spécifiques d’édition multi-caret:

| Touche d’accès rapide  | Action                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Insérer la prochaine caret assortie    | 
|  ⌥⇧;   | Insérer des carets à tous les correspondants | 
|  ⌥⇧,   | Enlever la dernière caret             | 
|  ⌥⇧/   | Déplacez-vous dernière caret vers le bas          | 

Chacun de ces comportements est ancré à la position actuelle de la caret lorsque vous invoquez la commande. Par exemple, si le caret est au début du mot «nom» et que vous invoquez « Insérez des carets à tous les correspondances » (;) chaque instance du mot «nom» dans votre document actuel aura une caret insérée au début du mot. De même, si vous invoquez la commande "Insérer le prochain caret correspondant" () alors une caret sera placée à la prochaine instance du mot "nom". Cette commande peut être invoquée plusieurs fois.

![clavier multi-caret](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Souris/touchpad

En utilisant votre curseur, vous êtes en mesure de sélectionner gratuitement des points d’insertion spécifiques pour vos plusieurs carets. Alors que les raccourcis clavier sont liés à des cordes assorties, vous pouvez insérer manuellement un caret n’importe où dans le document avec le curseur. Une fois les carets réglés, chacun fera écho aux entrées clés que vous tapez sur votre clavier.

Pour utiliser la souris pour insérer plusieurs carets, vous devez appuyer et tenir et tenir et cliquer là où vous souhaitez que les carets soient entrés. Vous serez en mode insertion tant que les clés sont conservées. Si vous insérez une caret dans un endroit incorrect, vous pouvez supprimer le caret en continuant à tenir et en cliquant à nouveau dans la même zone. Une fois que vous avez tous les carets situés où vous les souhaitez, arrêtez d’appuyer sur les touches et commencer à taper. Le GIF suivant démontre à la fois la sélection d’un ensemble de points d’insertion ainsi que la suppression des points réglés par erreur.

![souris multi-soins](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Voir aussi

- [Actions rapides (Visual Studio sur Windows)](/visualstudio/ide/quick-actions)
- [Refactoriser du code (Visual Studio sur Windows)](/visualstudio/ide/refactoring-in-visual-studio)
