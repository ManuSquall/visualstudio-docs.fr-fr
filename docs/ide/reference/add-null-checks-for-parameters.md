---
title: Ajouter des contrôles de valeurs null pour tous les paramètres
description: Découvrez comment créer et ajouter des instructions If à votre code pour vérifier la valeur null de tous les paramètres non activés et Nullable.
ms.custom: SEO-VS-2020
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5828a2bb28f7b3085cd5d43c452c520a730b8175
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95870961"
---
# <a name="add-null-checks-for-all-parameters"></a>Ajouter des contrôles de valeurs Null pour tous les paramètres 

Cette refactorisation s’applique à : 

- C# 

**Ce qui suit :** Crée et ajoute des `if` instructions qui vérifient la valeur null de tous les paramètres non activés et Nullable. 

Dans les **cas suivants :** Vous souhaitez ajouter rapidement des vérifications de valeur null pour tous les paramètres de méthode applicables.

**Pourquoi :** L’écriture de vérifications de valeurs NULL pour un grand nombre de paramètres peut être longue et répétitive. L’utilisation de cette refactorisation est rapide et rend le programme plus robuste.  

## <a name="how-to"></a>Procédures 

1. Placez votre curseur sur n’importe quel paramètre de la méthode.

2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Actions rapides et refactorisations](media/add-null-checks-for-all-parameters.png)
   
3. Sélectionnez l’option permettant d' **Ajouter des contrôles de valeur null pour tous les paramètres**.

   ![Ajouter des contrôles de valeurs null pour tout](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Voir aussi 

- [Refactorisation](../refactoring-in-visual-studio.md)
