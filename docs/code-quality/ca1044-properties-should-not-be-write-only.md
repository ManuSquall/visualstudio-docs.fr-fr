---
title: "CA1044 : Les propriétés ne doivent pas être écriture seule | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cdb3ac5479193236b146c7c2607e5a27727695a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044 : Les propriétés ne doivent pas être en écriture seule
|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|Category|Microsoft.Design|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 La propriété publique ou protégée a un accesseur set, mais elle n’a pas d’accesseur get.  
  
## <a name="rule-description"></a>Description de la règle  
 Obtenir les accesseurs fournissent un accès en lecture à une propriété et accesseurs set fournissent l’accès en écriture. Bien qu'il soit acceptable et souvent nécessaire de disposer d'une propriété en lecture seule, les règles de conception interdisent l'utilisation de propriétés en écriture seule. Il s’agit, car un utilisateur vous permettant de définir une valeur et empêcher ensuite l’affichage de la valeur de l’utilisateur ne fournit pas toute la sécurité. De plus, sans accès en lecture, l'état des objets partagés ne peut s'afficher, ce qui limite leur utilité.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez un accesseur get pour la propriété. Vous pouvez également, si le comportement d’une propriété en écriture seule est nécessaire, convertissez cette propriété à une méthode.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est fortement recommandé que vous ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, `BadClassWithWriteOnlyProperty` est un type avec une propriété en écriture seule. `GoodClassWithReadWriteProperty`contient le code corrigé.  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]