---
title: "CA1307 : Spécifier StringComparison | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1307
- SpecifyStringComparison
helpviewer_keywords:
- CA1307
- SpecifyStringComparison
ms.assetid: 9b0d5e71-1683-4a0d-bc4a-68b2fbd8af71
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 61d8ca557bfc55e3488a35e82f0242f931c51ed4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1307-specify-stringcomparison"></a>CA1307 : Spécifier StringComparison
|||  
|-|-|  
|TypeName|SpecifyStringComparison|  
|CheckId|CA1307|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas un <xref:System.StringComparison> paramètre.  
  
## <a name="rule-description"></a>Description de la règle  
 Plusieurs opérations de chaîne, la plus importantes du <xref:System.String.Compare%2A> et <xref:System.String.Equals%2A> méthodes, fournissent une surcharge qui accepte un <xref:System.StringComparison> valeur d’énumération en tant que paramètre.  
  
 Chaque fois qu’une surcharge existe qui prend un <xref:System.StringComparison> paramètre, il doit être utilisé au lieu d’une surcharge qui n’accepte pas ce paramètre. En définissant ce paramètre explicitement, votre code est souvent plus clair et plus facile à gérer.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, substituez les méthodes de comparaison de chaîne pour les surcharges qui acceptent le <xref:System.StringComparison> énumération en tant que paramètre. Par exemple : modifier `String.Compare(str1, str2)` à `String.Compare(str1, str2, StringComparison.Ordinal)`.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle lorsque la bibliothèque ou l’application est destinée à une audience locale limitée et ne sera donc pas localisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Avertissements de globalisation](../code-quality/globalization-warnings.md)   
 [CA1309 : Utilisez StringComparison avec la valeur Ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md)