---
title: "CA1708 : Les identificateurs doivent pas différer uniquement par leur casse | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5ed0b47255fb34f50b79913e8ce417c29302f10b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708 : Les identificateurs ne doivent pas différer que par leur casse
|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Les noms des deux types, membres, paramètres ou espaces de noms qualifiés complets sont identiques lorsqu’ils sont convertis en minuscules.  
  
## <a name="rule-description"></a>Description de la règle  
 Les identificateurs des espaces de noms, types, membres et paramètres ne peuvent pas différer uniquement par la casse car les langages qui ciblent le Common Language Runtime ne sont pas tenus de respecter celle-ci. Par exemple, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] est un langage de non-respect de la casse largement utilisé.  
  
 Cette règle se déclenche sur uniquement les membres visibles publiquement.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Sélectionnez un nom qui est unique lorsqu’elle est comparée à d’autres identificateurs sans respecter la casse.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. La bibliothèque ne peut pas être utilisable dans toutes les langues disponibles dans le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## <a name="example-of-a-violation"></a>Exemple de Violation  
 L’exemple suivant montre une violation de cette règle.  
  
 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)