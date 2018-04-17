---
title: 'CA1048 : Ne déclarez pas les membres virtuels dans les types sealed | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad16335502394d46eade760ba365b6dcf7ed529c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
 Les compilateurs c# et Visual Basic n’autorisent pas les types de violation de cette règle.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, rendez la méthode non virtuelle ou rendez le type héritable.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Laisser le type dans son état actuel peut entraîner des problèmes de maintenance et ne fournit pas d’avantages.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui viole cette règle.  
  
 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]