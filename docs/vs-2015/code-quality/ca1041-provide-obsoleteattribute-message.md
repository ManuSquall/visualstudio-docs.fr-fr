---
title: 'CA1041 : fournir un message ObsoleteAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dd1799f67036ab55de5b136d746ce938835de87f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668324"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041 : Fournir un message ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type ou un membre est marqué à l’aide d’un attribut <xref:System.ObsoleteAttribute?displayProperty=fullName> dont la propriété <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> n’est pas spécifiée.

## <a name="rule-description"></a>Description de la règle
 <xref:System.ObsoleteAttribute> est utilisé pour marquer les membres et les types de bibliothèque déconseillés. Les consommateurs de bibliothèque doivent éviter l’utilisation de n’importe quel type ou membre marqué comme obsolète. Cela est dû au fait qu’il n’est peut-être pas pris en charge et sera finalement supprimé des versions ultérieures de la bibliothèque. Lorsqu’un type ou membre marqué à l’aide de <xref:System.ObsoleteAttribute> est compilé, la propriété <xref:System.ObsoleteAttribute.Message%2A> de l’attribut est affichée. Cela fournit à l'utilisateur des informations sur le type ou le membre obsolète. Ces informations incluent généralement la durée pendant laquelle le type ou le membre obsolète sera pris en charge par les concepteurs de bibliothèques et le remplacement par défaut à utiliser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez le paramètre `message` au constructeur <xref:System.ObsoleteAttribute>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle, car la propriété <xref:System.ObsoleteAttribute.Message%2A> fournit des informations critiques sur le type ou le membre obsolète.

## <a name="example"></a>Exemple
 L’exemple suivant montre un membre obsolète qui a une <xref:System.ObsoleteAttribute> correctement déclarée.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
