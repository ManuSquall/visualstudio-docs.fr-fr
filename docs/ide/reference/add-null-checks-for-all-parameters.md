---
title: Ajouter des contrôles de valeurs null pour tous les paramètres
ms.date: 07/24/2019
ms.topic: reference
author: stcahlon
ms.author: t-shzach
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: da3a616844dbe914cfe796ec35d1501bf83dd1ef
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68712731"
---
# <a name="add-null-checks-for-all-parameters"></a>Ajouter des contrôles de valeurs Null pour tous les paramètres 

Cette refactorisation s’applique à : 

- C# 

**Quoi :** Crée et ajoute des instructions `if` qui vérifient s’il existe des valeurs null pour tous les paramètres non contrôlés pouvant accepter une valeur null. 

**Quand :** Vous souhaitez ajouter rapidement des contrôles de valeurs null pour tous les paramètres de méthode applicables.

**Pourquoi :** L’écriture de contrôles de valeurs null pour de nombreux paramètres peut être longue et répétitive. L’utilisation de cette refactorisation est rapide et rend le programme plus robuste.  

## <a name="how-to"></a>Procédure 

1. Placez votre curseur sur n’importe quel paramètre de la méthode.

2. Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Actions rapides et refactorisations](media/add-null-checks-for-all-parameters.png)
   
3. Sélectionnez l’option permettant d’**ajouter des contrôles de valeurs null pour tous les paramètres**.

   ![Ajouter des contrôles de valeurs null pour tout](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Voir aussi 

- [Refactorisation](../refactoring-in-visual-studio.md) 
