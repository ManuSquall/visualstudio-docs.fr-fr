---
title: Convertir l’instruction switch en expression switch
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour convertir une instruction switch en expression de commutateur C# 8,0.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: add43010fcec04cbe12889672f561f22057efb8c
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305525"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Convertir l’instruction switch en expression switch

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Convertit une [instruction switch](/dotnet/csharp/language-reference/keywords/switch) en [expression de commutateur](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8,0.

Dans les **cas suivants :** Vous souhaitez convertir une `switch` instruction en `switch` expression, et vice versa. 

**Pourquoi :** Si vous utilisez uniquement des expressions, cette refactorisation permet une transition aisée des `switch` instructions traditionnelles.

## <a name="how-to"></a>Procédures

1. Dans votre fichier de projet, [définissez la version du langage sur préversion](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file), car les expressions `switch` sont une nouvelle fonctionnalité de C# 8.0.
2. Placez votre curseur dans le `switch` mot clé et appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Convert l’instruction switch en expression**.

   ![Convertir l’instruction switch en expression switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
