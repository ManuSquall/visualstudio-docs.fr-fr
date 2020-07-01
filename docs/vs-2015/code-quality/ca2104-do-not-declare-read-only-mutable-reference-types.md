---
title: 'CA2104 : ne déclarez pas les types référence mutables en lecture seule | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ff42cc2b8543fe8e1cf980a3574ae15922febf9b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521041"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104 : Ne déclarez pas les types référence mutables en lecture seule
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type visible de l’extérieur contient un champ en lecture seule visible de l’extérieur qui constitue un type référence mutable.

## <a name="rule-description"></a>Description de la règle
 Un type mutable est un type dont les données d’instance peuvent être modifiées. La <xref:System.Text.StringBuilder?displayProperty=fullName> classe est un exemple de type référence mutable. Il contient des membres qui peuvent modifier la valeur d’une instance de la classe. La classe est un exemple de type de référence immuable <xref:System.String?displayProperty=fullName> . Une fois qu’elle a été instanciée, sa valeur ne peut jamais changer.

 Le modificateur en lecture seule ([ReadOnly](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) en C#, [ReadOnly](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] et [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) en c++) sur un champ de type référence (pointeur en c++) empêche le remplacement du champ par une autre instance du type référence. Toutefois, le modificateur n’empêche pas les données d’instance du champ d’être modifiées par le biais du type référence.

 Les champs de tableau en lecture seule sont exemptés de cette règle, mais provoquent une violation de la règle [CA2105 : les champs de tableau ne doivent pas être en lecture seule](../code-quality/ca2105-array-fields-should-not-be-read-only.md) .

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le modificateur en lecture seule ou, si une modification avec rupture est acceptable, remplacez le champ par un type immuable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si le type de champ est immuable.

## <a name="example"></a>Exemple
 L’exemple suivant montre une déclaration de champ qui provoque une violation de cette règle.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
