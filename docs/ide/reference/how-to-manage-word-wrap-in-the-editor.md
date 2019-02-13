---
title: Retour automatique à la ligne
ms.date: 11/07/2018
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88d5b4729ec24ef9594e3c0528a8d09156f23b1b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926267"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Procédure : Gérer le retour automatique à la ligne dans l’éditeur

Vous pouvez activer et désactiver l’option **Retour automatique à la ligne**. Lorsque cette option est activée, la partie d’une longue ligne qui s’étend au-delà de la largeur de la fenêtre de l’éditeur de code s’affiche à la ligne suivante. Lorsque cette option est désactivée, par exemple, pour faciliter l’utilisation de la numérotation des lignes, vous pouvez faire défiler l’affichage vers la droite pour voir l’extrémité des longues lignes.

> [!NOTE]
> Cette rubrique s’applique uniquement à Visual Studio sur Windows. Actuellement, Visual Studio pour Mac ne prend pas en charge le retour automatique à la ligne.

## <a name="to-set-word-wrap-preferences"></a>Pour définir les préférences de retour automatique à la ligne

1.  Dans le menu **Outils**, sélectionnez **Options**.

2.  Dans le dossier **Éditeur de texte**, choisissez les options **Général** dans le sous-dossier **Tous les langages** pour définir cette option globalement.

     — ou —

     Choisissez les options **Général** dans le sous-dossier du langage dans lequel vous programmez.

3.  Sous **Paramètres**, activez ou désactivez l’option **Retour automatique à la ligne**.

     Lorsque l’option **Retour automatique à la ligne** est sélectionnée, l’option **Afficher des glyphes visuels pour le retour automatique à la ligne** est activée.

4.  Sélectionnez l’option **Afficher des glyphes visuels pour le retour automatique à la ligne** si vous préférez afficher un indicateur fléché de retour là où une longue ligne est automatiquement renvoyée à une deuxième ligne. Désactivez cette option si vous préférez ne pas afficher d’indicateurs fléchés.

    > [!NOTE]
    > Ces flèches de rappel ne sont pas ajoutées à votre code : elles sont utilisées uniquement à des fins d’affichage.

## <a name="known-issues"></a>Problèmes connus

Si vous êtes familiarisé avec le retour automatique à la ligne dans Notepad++, Sublime Text ou Visual Studio Code, tenez compte des problèmes suivants, où Visual Studio se comporte différemment des autres éditeurs :

* [Le triple-clic ne permet pas de sélectionner la ligne entière](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [La commande Couper ne permet pas de supprimer la ligne entière](https://developercommunity.visualstudio.com/content/problem/138259/cut-command-should-delete-logical-line.html)
* [Si vous appuyez deux fois sur la touche Fin, le curseur ne se déplace pas à la fin de la ligne](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>Voir aussi

- [Personnalisation de l’éditeur](../../ide/customizing-the-editor.md)
- [Éditeur de texte, boîte de dialogue Options](../../ide/reference/text-editor-options-dialog-box.md)
- [Fonctionnalités de l’éditeur de code](../../ide/writing-code-in-the-code-and-text-editor.md)
