---
title: Méthode inline
description: Découvrez comment utiliser le menu actions rapides et refactorisations dans Visual Studio pour Refactoriser les déclarations de méthode inline et fournir une syntaxe plus claire.
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
ms.openlocfilehash: 655c6dad03b05b257aec3d92199321a0e0e93d22
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761418"
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
