---
title: Conversion entre la propriété auto et la propriété full
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour effectuer une conversion entre une propriété implémentée automatiquement et une propriété complète.
ms.custom: SEO-VS-2020
ms.date: 03/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b53f337b538ff1c0aef84272eea7d9e032eb2c1d
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040834"
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
