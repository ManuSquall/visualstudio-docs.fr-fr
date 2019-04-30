---
title: 'CA1001 : Types qui possèdent des champs supprimables doivent être supprimables | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 98be3bafb582e4d48560108625be911e53acf664
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562313"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001 : Les types qui possèdent des champs supprimables doivent être supprimables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|Category|Microsoft.Design|  
|Modification avec rupture|Sans rupture - Si le type n’est pas visible en dehors de l’assembly.<br /><br /> Avec rupture - Si le type est visible en dehors de l’assembly.|  
  
## <a name="cause"></a>Cause  
 Une classe déclare et implémente un champ d’instance qui est un <xref:System.IDisposable?displayProperty=fullName> type et la classe n’implémente pas <xref:System.IDisposable>.  
  
## <a name="rule-description"></a>Description de la règle  
 Une classe implémente la <xref:System.IDisposable> interface pour supprimer les ressources non managées qu’il possède. Un champ d’instance qui est un <xref:System.IDisposable> type indique que le champ possède une ressource non managée. Une classe qui déclare un <xref:System.IDisposable> champ indirectement possède une ressource non managée et doit implémenter le <xref:System.IDisposable> interface. Si la classe ne possède pas directement les ressources non managées, il ne doit pas implémenter un finaliseur.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, implémentez <xref:System.IDisposable> et à partir de la <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> appel de méthode le <xref:System.IDisposable.Dispose%2A> méthode du champ.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une classe qui viole la règle et une classe qui satisfait la règle en implémentant <xref:System.IDisposable>. La classe n’implémente pas de finaliseur, car la classe ne possède pas directement les ressources non managées.  
  
 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216 : Les types supprimables doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215 : Méthodes Dispose doivent appeler dispose de la classe de base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049 : Les types qui possèdent des ressources natives doivent être supprimables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
