---
title: Ajouter des contrôles de valeurs null pour tous les paramètres
ms.date: 09/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 573a9e56d3aedd55bc571eaaa363b42a53019566
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74782306"
---
# <a name="add-null-checks-for-all-parameters"></a>Ajouter des contrôles de valeurs Null pour tous les paramètres 

Cette refactorisation s’applique à : 

- C# 

**Quoi :** Crée et `if` ajoute des déclarations qui vérifient la nullité de tous les paramètres non vérifiés. 

**Quand :** Vous souhaitez ajouter rapidement des contrôles nuls pour tous les paramètres de méthode applicables.

**Pourquoi:** L’écriture de vérifications nulles pour de nombreux paramètres peut prendre beaucoup de temps et répétitive. L’utilisation de cette refactorisation est rapide et rend le programme plus robuste.  

## <a name="how-to"></a>Procédures 

1. Placez votre curseur sur n’importe quel paramètre de la méthode.

2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Actions rapides et refactorisations](media/add-null-checks-for-all-parameters.png)
   
3. Sélectionnez l’option permettant d’**ajouter des contrôles de valeurs null pour tous les paramètres**.

   ![Ajouter des contrôles de valeurs null pour tout](media/add-null-checks-for-all.png) 

## <a name="see-also"></a>Voir aussi 

- [Refactorisation](../refactoring-in-visual-studio.md)
