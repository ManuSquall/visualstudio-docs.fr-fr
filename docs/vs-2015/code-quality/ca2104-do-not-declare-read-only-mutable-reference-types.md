---
title: 'CA2104 : Ne déclarez pas les types référence mutables uniquement en lecture | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f8e8ce2c8c6ac780dc3233fdac5c668576ac7b35
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49279342"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104 : Ne déclarez pas les types référence mutables en lecture seule
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type visible de l’extérieur contient un champ en lecture seule visible de l’extérieur qui constitue un type référence mutable.

## <a name="rule-description"></a>Description de la règle
 Un type mutable est un type dont les données d’instance peuvent être modifiées. Le <xref:System.Text.StringBuilder?displayProperty=fullName> classe est un exemple d’un type référence mutable. Il contient des membres qui peuvent modifier la valeur d’une instance de la classe. Un exemple d’un type référence immuable est le <xref:System.String?displayProperty=fullName> classe. Une fois qu’il a été instancié, sa valeur ne peut jamais changer.

 Le modificateur en lecture seule ([readonly](http://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) en c#, [ReadOnly](http://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], et [const](http://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) en C++) sur un type référence de champ (pointeur en C++) empêche le champ remplacée par une autre instance du type référence. Toutefois, le modificateur n’empêche pas les données d’instance du champ d’être modifiées par le type de référence.

 Champs de tableau en lecture seule sont exemptés de cette règle, mais au lieu de cela provoque une violation de la [CA2105 : les champs de tableau ne doivent pas être en lecture seule](../code-quality/ca2105-array-fields-should-not-be-read-only.md) règle.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le modificateur en lecture seule ou, si une modification avec rupture est acceptable, remplacez le champ par un type immuable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si le type de champ est immuable.

## <a name="example"></a>Exemple
 L’exemple suivant montre une déclaration de champ qui provoque une violation de cette règle.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]



