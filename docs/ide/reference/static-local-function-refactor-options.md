---
title: Options de refactorisation de fonction locale statique
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour rendre une fonction locale statique et passer des variables définies en dehors de la fonction à la déclaration et aux appels de la fonction.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 8e85fcc96542b4f3538729aeb50a4e080c902657
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479886"
---
# <a name="static-local-function-refactorings-and-quick-actions"></a>Refactorisations de fonction locale statique et actions rapides

Cet article décrit deux fonctionnalités de productivité liées aux fonctions locales statiques. L’une est une refactorisation qui rend une fonction locale statique, et l’autre est une action rapide qui génère du code pour passer des variables dans une fonction locale statique.

## <a name="make-local-function-static"></a>Rendre la fonction locale statique

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Rend une fonction locale statique et passe des variables définies en dehors de la fonction à la déclaration de la fonction et appelle.

Dans les **cas suivants :** Vous souhaitez que votre fonction locale soit statique et que toutes les variables soient définies dans l’étendue de la fonction.

**Pourquoi :** Les fonctions locales statiques améliorent la lisibilité : sachant que le code spécifique est isolé, il est plus facile à comprendre, à relire et à réutiliser. Les fonctions locales statiques fournissent également une étendue pour empêcher la pollution d’une classe avec une fonction statique appelée uniquement dans une méthode unique.

### <a name="how-to"></a>Procédures

1. Placez le signe insertion sur le nom de la fonction locale.

2. Appuyez sur **CTRL** + **.** (point) pour déclencher le menu **actions rapides et refactorisations** .

   ![Rendre la fonction locale statique](media/make-local-function-static.png)

3. Sélectionnez **rendre la fonction locale « static ».**

## <a name="pass-variable-explicitly-in-a-static-local-function"></a>Passer explicitement une variable dans une fonction locale statique

Cette action rapide s’applique à :

- C#

**Ce qui suit :** Passe une variable explicitement dans une fonction statique locale.

Dans les **cas suivants :** Vous souhaitez qu’une fonction locale soit statique, tout en continuant à utiliser des variables initialisées en dehors de celle-ci.

**Pourquoi :** L’utilisation de fonctions locales statiques apporte des éclaircissements aux lecteurs, car ils savent qu’ils ne peuvent être déclarés et appelés que dans un contexte spécifique du programme. Il offre la possibilité de définir des variables en dehors de ce contexte, tout en étant en mesure de les transmettre en tant qu’arguments à la fonction locale statique.

### <a name="how-to"></a>Procédures

1. Placez le signe insertion sur la variable où elle est utilisée dans la fonction locale statique.

2. Appuyez sur **CTRL** + **.** (point) pour déclencher le menu **actions rapides et refactorisations** .

   ![Passer la variable explicitement dans une fonction locale statique](media/pass-variable-explicitly-static-local-function.png)

3. Sélectionnez **Pass variable explicitly in local static function** (Passer explicitement la variable dans une fonction statique locale).

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)