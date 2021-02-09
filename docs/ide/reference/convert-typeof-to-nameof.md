---
title: Convertir typeof en nameof
description: Découvrez comment utiliser le menu actions rapides et refactorisations dans Visual Studio pour convertir typeof en nameof en C# et GetType en NameOf dans Visual Basic.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: f93c5232f852e1390eac9e2ebb57235abc5e1f6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919700"
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
      <br>Sélectionnez **convertir « typeof » en « nameof »**: ![ capture d’écran du menu actions rapides et refactorisations dans Visual Studio avec convertir « typeof » en « nameof » sélectionné, et modifications du code C# affichées.](media/convert-type-of.PNG)

    - Visual Basic
      <br>Sélectionnez **convertir « GetType » en « NameOf »**: ![ capture d’écran du menu actions rapides et refactorisations dans Visual Studio avec convertir « GetType » en « NameOf » sélectionné et Visual Basic modifications du code affichées.](media/convert-get-type.PNG)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
