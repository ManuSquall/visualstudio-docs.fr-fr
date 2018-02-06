---
title: "Convertir la méthode Get en propriété et convertir une propriété en une méthode Get en C# | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: a23af31c5099908ed0b6fed07404216a57975f75
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>Convertir la méthode Get en propriété/convertir une propriété en méthode Get

## <a name="convert-get-method-to-property"></a>Convertir la méthode Get en propriété

**Quoi :** vous permet de convertir une méthode Get en une propriété (et éventuellement votre méthode Set) et vice versa.

**Quand :** vous avez une méthode Get qui ne contient aucune logique.

**Comment :**

1. Placez votre curseur dans le nom de votre méthode Get.

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Remplacer une méthode par une propriété** dans la fenêtre contextuelle d’aperçu. Si vous avez une méthode Set, vous pouvez également convertir votre méthode Set à cette étape en sélectionnant **Remplacer la méthode Get et la méthode Set par une propriété**.
   * **Souris**
     * Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Remplacer une méthode par une propriété** dans la fenêtre contextuelle d’aperçu. Si vous avez une méthode Set, vous pouvez également convertir votre méthode Set à cette étape en sélectionnant **Remplacer la méthode Get et la méthode Set par une propriété**.

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

**Comment :**

1. Placez votre curseur dans le nom de votre méthode Get.

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Remplacer une propriété par des méthodes** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Remplacer une propriété par des méthodes** dans la fenêtre contextuelle d’aperçu.

1. Si vous êtes satisfait de la modification dans l’aperçu du code, appuyez sur **Entrée** ou cliquez sur le correctif dans le menu pour valider les modifications.

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)