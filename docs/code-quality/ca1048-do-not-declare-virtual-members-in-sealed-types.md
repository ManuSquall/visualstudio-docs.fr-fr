---
title: "CA1048 : Ne déclarez pas les membres virtuels dans les types sealed | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cb13b2b74ca86101949275e418968e577ca2b7c5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048 : Ne pas déclarer les membres virtuels dans les types sealed
|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|Category|Microsoft.Design|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type public est sealed et déclare une méthode qui est à la fois `virtual` (`Overridable` en Visual Basic) et non finale. Cette règle ne signale pas les violations pour les types délégués qui doivent suivre ce modèle.  
  
## <a name="rule-description"></a>Description de la règle  
 Les types déclarent des méthodes comme étant virtuelles afin d'hériter de types en mesure de substituer l'implémentation de la méthode virtuelle. Par définition, vous ne peut pas hériter d’un type sealed, en apportant une méthode virtuelle sur un type sealed sans signification.  
  
 Les compilateurs c# et Visual Basic .NET n’autorisent pas les types de violation de cette règle.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, rendez la méthode non virtuelle ou rendez le type héritable.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Laisser le type dans son état actuel peut entraîner des problèmes de maintenance et ne fournit pas d’avantages.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui viole cette règle.  
  
 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]