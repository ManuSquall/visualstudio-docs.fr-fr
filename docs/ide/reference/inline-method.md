---
title: Méthode inline
description: Découvrez comment utiliser le menu actions rapides et refactorisations dans Visual Studio pour Refactoriser les déclarations de méthode inline et fournir une syntaxe plus claire.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 80313cf0dd9b828c9602fdf8ebff022342faa0fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852360"
---
# <a name="inline-method"></a>Méthode inline

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

    ![LinkedDataFormUpdated du menu actions rapides et refactorisations dans Visual Studio avec convertir’inline’CreateWidget () 'sélectionné et les modifications du code C# affichées.](media/inline-method-remove-declaration.png)

   Sélectionnez **Inline et conserver `<QualifiedMethodName>`** pour conserver la déclaration de la méthode d’origine : 

    ![LinkedDataFormUpdated du menu actions rapides et refactorisations dans Visual Studio à l’aide de l’option convertir’inline et conserver’CreateWidget () 'sélectionnée et les modifications du code C# affichées.](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
