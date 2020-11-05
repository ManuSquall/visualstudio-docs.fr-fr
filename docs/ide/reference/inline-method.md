---
title: Inline, méthode
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0cc619ea61a7fd4d7f4bc542b946e298933a8f73
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402300"
---
# <a name="inline-method"></a>Inline, méthode

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** Refactorisation de méthode Inline. 

Dans les **cas suivants :** Vous souhaitez remplacer les utilisations d’une méthode statique, d’instance et d’extension dans un corps d’instruction unique avec une option pour supprimer la déclaration de méthode d’origine.

**Pourquoi :**  Cette refactorisation fournit une syntaxe plus claire.

## <a name="how-to"></a>Procédures

1. Placez le signe insertion sur l’utilisation de la méthode.

2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

3. Sélectionnez l’une des options suivantes : 
    
   Sélectionnez **`<QualifiedMethodName>` inline** pour supprimer la déclaration de la méthode inline : 

    ![Rendre la classe abstraite](media/inline-method-remove-declaration.png)

   Sélectionnez **Inline et conserver `<QualifiedMethodName>`** pour conserver la déclaration de la méthode d’origine : 

    ![Rendre la classe abstraite](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
