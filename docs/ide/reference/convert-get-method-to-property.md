---
title: Convertir la méthode Get en propriété et convertir une propriété en méthode Get
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
ms.devlang: csharp
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0af901ed6a51b962b7b2999b04909136bbb0f3e9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861145"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Convertir la méthode Get en propriété/convertir une propriété en méthode Get (refactorisations)

Ces refactorisations s’appliquent à :

- C#

## <a name="convert-get-method-to-property"></a>Convertir la méthode Get en propriété

**Quoi :** Vous permet de convertir une méthode Get en une propriété (et éventuellement votre méthode Set).

**Quand :** Vous avez une méthode Get qui ne contient aucune logique.

### <a name="how-to"></a>Procédure

1. Placez votre curseur dans le nom de votre méthode Get.

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Remplacer une méthode par une propriété** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Cliquez avec le bouton droit sur le code, sélectionnez le menu **Actions rapides et refactorisations**, puis **Remplacer une méthode par une propriété** dans la fenêtre contextuelle d’aperçu.

1. (Facultatif) Si vous avez une méthode Set, vous pouvez également convertir votre méthode Set à cette étape en sélectionnant **Remplacer la méthode Get et la méthode Set par une propriété**.

1. Si vous êtes satisfait de la modification dans l’aperçu du code, appuyez sur **Entrée** ou cliquez sur le correctif dans le menu pour valider les modifications.

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

## <a name="convert-property-to-get-method"></a>Convertir la propriété en méthode Get

**Quoi :** Vous permet de convertir une propriété en une méthode Get

**Quand :** Vous disposez d’une propriété qui implique plus que la définition et l’obtention immédiates d’une valeur

### <a name="how-to"></a>Procédure

1. Placez votre curseur dans le nom de votre méthode Get.

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Remplacer une propriété par des méthodes** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Remplacer une propriété par des méthodes** dans la fenêtre contextuelle d’aperçu.

1. Si vous êtes satisfait de la modification dans l’aperçu du code, appuyez sur **Entrée** ou cliquez sur le correctif dans le menu pour valider les modifications.

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)