---
title: Générer une substitution de méthode
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 075c7dc49ffba1d67bbb5b62d313f50b5d09e956
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668442"
---
# <a name="generate-an-override-in-visual-studio"></a>Générer une substitution dans Visual Studio

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de générer immédiatement le code pour toute méthode pouvant être substituée à partir d’une classe de base.

**Quand :** vous souhaitez substituer une méthode de classe de base et générer automatiquement la signature.

**Pourquoi :** vous pouvez écrire la signature de la méthode vous-même, mais cette fonctionnalité générera automatiquement la signature.

## <a name="how-to"></a>Procédure

1. Tapez `override` en C# ou `Overrides` en Visual Basic, suivi d’un espace, à l’emplacement où vous souhaitez insérer une méthode override.

   - C# :

      ![Override IntelliSense C#](media/override-intellisense-cs.png)

   - Visual Basic :

      ![Override IntelliSense VB](media/override-intellisense-vb.png)

2. Sélectionnez la méthode à substituer à partir de la classe de base.

   > [!TIP]
   > - Utilisez l’icône Propriété ![Icône Propriété](media/override-property-cs.png) pour afficher ou masquer les propriétés dans la liste.
   > - Utilisez l’icône Méthode ![Icône Méthode](media/override-method-cs.png) pour afficher ou masquer les méthodes dans la liste.

   La méthode ou la propriété sélectionnée est ajoutée à la classe comme substitution, prête à être implémentée.

   - C# :

       ![Résultat de la substitution (C#)](media/override-result-cs.png)

   - Visual Basic :

       ![Résultat de la substitution (VB)](media/override-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)