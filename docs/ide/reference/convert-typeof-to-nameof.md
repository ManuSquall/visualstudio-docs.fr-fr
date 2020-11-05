---
title: Convertir typeof en nameof
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 96bd4d67302fb09e5c1cb7837ad73b345ad88c81
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400322"
---
# <a name="convert-typeof-to-nameof"></a>Convertir `typeof` en `nameof`

Cette refactorisation s’applique à :

- C#
- Visual Basic

**Ce qui suit :** Vous permet de convertir une instance de en `typeof(<QualifiedType>).Name` `nameof(<QualifiedType>)` en C# et une instance de en `GetType(<QualifiedType>).Name` `NameOf(<QualifiedType>)` dans Visual Basic.

Dans les **cas suivants :**  Toutes les instances de `typeof(<QualifiedType>).Name` où `someType` n’est pas un type générique. Cette exclusion est nécessaire, car ce cas de figure ne retourne pas la même valeur de chaîne que `nameof(<QualifiedType>)` . Il en va de même pour l’instance Visual Basic.

**Pourquoi :** L’utilisation `nameof` de plutôt que le nom de la `type` méthode évite la réflexion impliquée dans la récupération d’un `type` objet et constitue un moyen plus pragmatique de l’écrire.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans l' `typeof(<QualifiedType>).Name` instance pour C# ou `GetType(<QualifiedType>).Name` dans Visual Basic.

2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

3. Sélectionnez l’une des options suivantes :

    - C#
      <br>Sélectionnez **convertir’typeof’en’nameof'** : ![ Convert typeof en nameof](media/convert-type-of.PNG)

    - Visual Basic
      <br>Sélectionnez **convertir « GetType » en « NameOf »** : ![ Convert typeof en NameOf](media/convert-get-type.PNG)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
