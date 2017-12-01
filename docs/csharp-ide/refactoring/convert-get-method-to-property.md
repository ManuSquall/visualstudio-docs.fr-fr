---
title: "Convertir la méthode Get pour la propriété - (refactorisation c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.openlocfilehash: d034b8835caf0a5e56a9ef32599cf9197f1e3e16
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2017
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>Convertir la méthode Get pour la propriété / convertir propriété Get (méthode)
## <a name="convert-get-method-to-property"></a>Convertir la méthode Get pour la propriété
**Ce que :** vous permet de convertir une méthode Get dans une propriété (et éventuellement votre méthode Set) et vice versa.

**Quand :** vous avez une méthode Get qui ne contient-elle pas de logique.

**Comment faire :**

1. Placez votre curseur dans votre nom de la méthode Get.

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **Replace (méthode) avec la propriété** à partir du message de fenêtre d’aperçu. Si vous avez une méthode Set, vous pouvez également convertir votre méthode Set pour l’instant, en sélectionnant **méthode remplacer Get et Set (méthode) avec la propriété**.
   * **Souris**
     * Cliquez sur le code, sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **Replace (méthode) avec la propriété** à partir du message de fenêtre d’aperçu. Si vous avez une méthode Set, vous pouvez également convertir votre méthode Set pour l’instant, en sélectionnant **méthode remplacer Get et Set (méthode) avec la propriété**.

1. Si vous êtes satisfait de la modification de l’aperçu du code, appuyez sur **entrée** ou cliquez sur le correctif à partir du menu et les modifications seront validées.

Exemple :

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Convertir la propriété à la méthode Get
**Ce que :** vous permet de convertir une propriété à une méthode Get

**Quand :** vous disposez d’une propriété qui implique plusieurs immédiatement et l’obtention d’une valeur 

**Comment faire :**

1. Placez votre curseur dans votre nom de la méthode Get.

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **remplacer la propriété avec les méthodes** à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Cliquez sur le code, sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **remplacer la propriété avec les méthodes** à partir du message de fenêtre d’aperçu.

1. Si vous êtes satisfait de la modification de l’aperçu du code, appuyez sur **entrée** ou cliquez sur le correctif à partir du menu et les modifications seront validées.

## <a name="see-also"></a>Voir aussi  
[Refactorisation (C#)](../refactoring-csharp.md)  
[Aperçu des modifications](../../ide/preview-changes.md)