---
title: "Générer une substitution - génération de code (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 3801d8ce60cf87126f8894bf44c77056f996cde1
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="generate-an-override-in-c"></a>Générer une substitution en C# #

**Quoi :** vous permet de générer immédiatement le code pour toute méthode pouvant être substituée à partir d’une classe de base.

**Quand :** vous souhaitez substituer une méthode de classe de base et générer automatiquement la signature.

**Pourquoi :** vous pouvez écrire la signature de la méthode vous-même, mais cette fonctionnalité générera automatiquement la signature.

**Comment :**

1. Tapez le mot clé **override**, suivi d’un espace, où vous souhaitez insérer une signature de méthode de substitution : une liste déroulante IntelliSense s’affichera.

   ![Substituer IntelliSense](media/override-intellisense-cs.png)

1. Sélectionnez la méthode que vous souhaitez substituer à partir de la classe de base en cliquant dessus avec la souris ou en naviguant vers elle avec le clavier puis en appuyant sur **Entrée**.

   >[!TIP]
   >* Utilisez l’icône Propriété ![Icône Propriété](media/override-property-cs.png) pour afficher ou masquer les propriétés dans la liste.
   >* Utilisez l’icône Méthode ![Icône Méthode](media/override-method-cs.png) pour afficher ou masquer les méthodes dans la liste.

1. La méthode ou la propriété sélectionnée sera ajoutée à la classe comme une substitution, prête à être implémentée.

   ![Résultat de l’action Substituer](media/override-result-cs.png)

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)
