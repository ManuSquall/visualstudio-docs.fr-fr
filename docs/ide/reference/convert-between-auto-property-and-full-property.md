---
title: Conversion entre la propriété auto et la propriété full
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8950ce27e95a59f5425419dcac5bd807193d51b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395411"
---
# <a name="convert-between-auto-property-and-full-property"></a>Conversion entre la propriété auto et la propriété full

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Effectue la conversion entre une propriété implémentée automatiquement en une propriété complète.

Dans les **cas suivants :** La logique de la propriété a été modifiée.

**Pourquoi :** Vous pouvez effectuer une conversion manuelle d’une propriété implémentée automatiquement en une propriété complète, mais cette fonctionnalité effectue automatiquement le travail pour vous. 

## <a name="how-to"></a>Procédures

1. Placez le curseur sur le nom de la propriété.
2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez l’une des deux options suivantes : 

    Sélectionnez **convertir en propriété complète**.

   ![Convertir une propriété automatique en propriété complète](media/convert-auto-property-to-full-property.png) 

    Sélectionnez **utiliser auto Property**. 

    ![Convertir la propriété Full en propriété auto](media/convert-full-property-to-auto-property.png) 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
