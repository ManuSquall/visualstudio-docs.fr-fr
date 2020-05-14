---
title: Options de refactorisation de fonction locale statique
ms.date: 02/10/2020
ms.topic: reference
author: governesss
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.make.local.function.static
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c297457c910c484c05c974c581e89c75e0ad44e5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77144839"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Refactorings de fonction locale statique et actions rapides

Cet article décrit deux caractéristiques de productivité liées aux fonctions locales statiques. L’un est un refactoring qui rend une fonction locale statique, et l’autre est une action rapide qui génère du code pour passer des variables dans une fonction locale statique.

## <a name="make-local-function-static"></a>Rendre la fonction locale statique

Cette refactorisation s’applique à :

- C#

**Quoi :** Rend une fonction locale statique et passe en variables définies en dehors de la fonction à la déclaration et aux appels de la fonction.

**Quand :** Vous voulez que votre fonction locale soit statique et que toutes les variables soient définies dans la portée de la fonction.

**Pourquoi:** Les fonctions locales statiques améliorent la lisibilité : savoir que le code spécifique est isolé facilite la compréhension, la reliure et la réutilisation. Les fonctions locales statiques fournissent également la portée pour empêcher de polluer une classe avec une fonction statique qui n’est appelée que dans une seule méthode.

### <a name="how-to"></a>Procédures

1. Placez votre caret sur le nom de la fonction locale.

2. Appuyez **sur Ctrl**+**.** (période) pour déclencher le menu **Actions rapides et Refactorings.**

   ![Rendre la fonction locale statique](media/make-local-function-static.png)

3. Sélectionnez **Rendre la fonction locale 'statique'.**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Passer la variable explicitement dans une fonction locale statique

Cette action rapide s’applique à :

- C#

**Quoi :** Passe une variable explicitement dans une fonction statique locale.

**Quand :** Vous voulez qu’une fonction locale soit statique, mais utilisez toujours des variables parastérisées en dehors de celle-ci.

**Pourquoi:** L’utilisation de fonctions locales statiques fournit des éclaircissements aux lecteurs parce qu’ils savent qu’il ne peut être déclaré et appelé que dans un contexte spécifique du programme. Il offre la flexibilité de définir des variables en dehors de ce contexte, mais tout de même être en mesure de les transmettre en tant qu’arguments à la fonction locale statique.

### <a name="how-to"></a>Procédures

1. Placez votre caret sur la variable où elle est utilisée dans la fonction locale statique.

2. Appuyez **sur Ctrl**+**.** (période) pour déclencher le menu **Actions rapides et Refactorings.**

   ![Variation de passage explicitement dans la fonction locale statique](media/pass-variable-explicitly-static-local-function.png)

3. Sélectionnez **Pass variable explicitly in local static function** (Passer explicitement la variable dans une fonction statique locale).

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)