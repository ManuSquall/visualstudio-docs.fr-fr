---
title: Conversion entre la propriété auto et la propriété full
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour effectuer une conversion entre une propriété implémentée automatiquement et une propriété complète.
ms.custom: SEO-VS-2020
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 3680444c07658da8e77b6058f5a71b9dcf119193
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907596"
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
