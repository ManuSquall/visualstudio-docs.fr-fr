---
title: Modification avec signes insertion multiples
description: Insérer du texte à plusieurs emplacements lors de la modification du code dans Visual Studio pour Mac.
author: cobey
ms.author: cobey
ms.date: 08/19/2019
ms.openlocfilehash: a21bebda057a772017fa1481e18f9801d1fbcbdf
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451446"
---
# <a name="multi-caret-editing"></a>Modification avec signes insertion multiples

La modification de plusieurs signets vous permet d’ajouter _n_ points d’insertion à un seul moment. Lorsque vous êtes en mode multipoint, vous pouvez ajouter des signes d’insertion supplémentaires à votre document à l’aide de clics de souris ou de commandes du clavier. Le signe insertion principal est indiqué par un curseur rouge, tandis que les signes secondaires sont présents dans une couleur bleu clair. Le mode d’édition à plusieurs carets peut être désactivé via la clé de `ESC`.

## <a name="enabling-multi-caret-editing"></a>Activation de la modification de plusieurs carets

### <a name="keyboard"></a>Clavier

Vous pouvez activer le mode multicaret à l’aide du clavier de plusieurs façons. Le tableau suivant fournit les raccourcis clavier disponibles pour entrer des modes spécifiques d’édition à plusieurs carets :

| Touche d’accès rapide  | Action                        | 
|---------| ------------------------------|
|  ⌥⇧.   | Insérer le signe insertion correspondant suivant    | 
|  ⌥⇧;   | Insérer des signes d’insertion à la correspondance | 
|  ⌥⇧,   | Supprimer le dernier signe insertion             | 
|  ⌥⇧/   | Déplacer le dernier signe insertion vers le dessous          | 

Chacun de ces comportements est ancré à la position actuelle du signe insertion lorsque vous appelez la commande. Par exemple, si le signe insertion se trouve au début du mot « nom » et que vous appelez « insérer des signes à toutes les correspondances » (⌥ ⇧;) une insertion du mot « Name » dans votre document actif est insérée au début du mot. De même, si vous appelez la commande « Insérer le signe insertion suivant » (⌥ ⇧.), un signe insertion sera placé à l’instance suivante du mot « nom ». Cette commande peut être appelée plusieurs fois.

![clavier à plusieurs carets](media/multi-caret-keyboard.gif)

## <a name="mousetouchpad"></a>Souris/pavé tactile

À l’aide de votre curseur, vous pouvez libérer des points d’insertion spécifiques pour vos multiples signes. Tandis que les raccourcis clavier sont liés aux chaînes correspondantes, vous pouvez insérer manuellement un signe insertion n’importe où dans le document à l’aide du curseur. Une fois que les signes d’insertion sont définis, chacun répercute les entrées de touches que vous tapez sur votre clavier.

Pour utiliser la souris pour insérer plusieurs signes d’insertion, vous devez appuyer et maintenir ⌘ ⌥ et cliquer à l’endroit où vous souhaitez que les signes d’insertion soient saisis. Vous serez en mode insertion tant que les clés ⌘ ⌥ sont conservées. Si vous insérez un signe insertion dans un emplacement incorrect, vous pouvez supprimer le signe insertion en continuant à maintenir ⌘ ⌥ et en cliquant de nouveau sur la même zone. Une fois que vous avez tous les signes indiquant l’emplacement où vous souhaitez les placer, arrêtez l’appui sur les touches ⌘ ⌥ et commencez à taper. Le GIF suivant illustre la sélection d’un ensemble de points d’insertion et la suppression de points définis de manière erronée.

![souris à plusieurs carets](media/multi-caret-mouse.gif)

## <a name="see-also"></a>Voir aussi

- [Actions rapides (Visual Studio sur Windows)](/visualstudio/ide/quick-actions)
- [Refactoriser du code (Visual Studio sur Windows)](/visualstudio/ide/refactoring-in-visual-studio)
