---
title: 'CA1724 : Les noms de types ne doivent pas correspondre aux espaces de noms | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
helpviewer_keywords:
- TypeNamesShouldNotMatchNamespaces
- CA1724
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 39e6b539d0259f83475e3e3a685bed7ffe6a7c87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1724-type-names-should-not-match-namespaces"></a>CA1724 : les noms de types ne doivent pas être identiques aux espaces de noms
|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un nom de type correspond à un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] noms d’espace de noms dans une comparaison respectant la casse.  
  
## <a name="rule-description"></a>Description de la règle  
 Les noms de types ne doivent pas correspondre aux noms d'espaces de noms définis dans la bibliothèque de classes [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Enfreindre cette règle peut réduire la facilité d'utilisation de la bibliothèque.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Sélectionnez un nom de type qui ne correspond pas à celui d’un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] espace de noms de bibliothèque.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Pour un nouveau développement, aucun autre scénarios se produisent lorsque vous devez supprimer un avertissement de cette règle. Avant de pouvoir supprimer l’avertissement, étudiez attentivement la façon dont les utilisateurs de votre bibliothèque peuvent être perdus par le nom correspondant. Pour livrer des bibliothèques, vous devrez peut-être supprimer un avertissement de cette règle.