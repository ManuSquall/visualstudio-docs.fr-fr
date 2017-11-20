---
title: "Générer un remplacement - génération de Code (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8a7658ff8e2f573f2da6ff3197b6a11f3b3a0a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="generate-an-override-in-visual-basic"></a>Générer un remplacement dans Visual Basic
**Ce que :** vous permet d’immédiatement générer le code pour une toute méthode qui peut être substituée à partir d’une classe de base. 

**Quand :** vous souhaitez substituer une méthode de classe de base et de générer automatiquement de la signature.  

**Pourquoi :** vous pouvez écrire la signature de méthode vous-même, mais cette fonctionnalité génère automatiquement la signature. 

**Comment faire :**

1. Type de la **remplace** (mot clé), suivi d’un espace, où vous souhaitez insérer une signature de méthode substituée et une liste déroulante IntelliSense s’affiche.

   ![Remplacer IntelliSense](media/override_intellisense.png)

1. Sélectionnez la méthode que vous souhaitez remplacer à partir de la classe de base en cliquant dessus avec la souris, ou en naviguant vers elle avec le clavier et en appuyant sur **entrée**.

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override_property.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override_method.png) to show or hide Methods in the list.
-->

1. La méthode sélectionnée ou la propriété sera ajoutée à la classe comme un remplacement, prêt à être implémentée.

   ![Remplacer les résultats](media/override_result.png)

## <a name="see-also"></a>Voir aussi  
[Génération de code (Visual Basic)](../code-generation-vb.md) 