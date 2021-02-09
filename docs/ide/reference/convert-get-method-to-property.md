---
title: Convertir une méthode de récupération vers ou à partir d’une propriété
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour convertir une méthode d’obtention (et éventuellement votre méthode Set) en propriété.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
ms.devlang: csharp
author: mikadumont
ms.author: midumont
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d86a9c42fbd1c54e7bef409cc6d61d9aca751436
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919657"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Convertir la méthode Get en propriété/convertir une propriété en méthode Get (refactorisations)

Ces refactorisations s’appliquent à :

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>Convertir la méthode Get en propriété

**Quoi :** vous permet de convertir une méthode Get en une propriété (et éventuellement votre méthode Set).

**Quand :** vous avez une méthode Get qui ne contient aucune logique.

### <a name="how-to"></a>Procédures

1. Placez votre curseur dans le nom de votre méthode Get.

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **CTRL** + **.** pour afficher le menu **actions rapides et refactorisations** , puis sélectionnez **remplacer la méthode par la propriété** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Cliquez avec le bouton droit sur le code, sélectionnez le menu **actions rapides et refactorisations** , puis sélectionnez **remplacer la méthode par la propriété** dans la fenêtre contextuelle d’aperçu.

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

**Quoi :** vous permet de convertir une propriété en une méthode Get

**Quand :** vous disposez d’une propriété qui implique plus que la définition et l’obtention immédiates d’une valeur

### <a name="how-to"></a>Procédures

1. Placez votre curseur dans le nom de votre méthode Get.

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Remplacer une propriété par des méthodes** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Remplacer une propriété par des méthodes** dans la fenêtre contextuelle d’aperçu.

1. Si vous êtes satisfait de la modification dans l’aperçu du code, appuyez sur **Entrée** ou cliquez sur le correctif dans le menu pour valider les modifications.

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
