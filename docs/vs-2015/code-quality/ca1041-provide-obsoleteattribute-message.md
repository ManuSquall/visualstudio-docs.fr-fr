---
title: 'CA1041 : Fournir un message ObsoleteAttribute | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fe14ca0c0e917896a2ed5a31a03a8c1a7057d613
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559829"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041 : Fournir un message ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type ou un membre est marqué à l’aide un <xref:System.ObsoleteAttribute?displayProperty=fullName> attribut qui n’a pas son <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> propriété spécifiée.

## <a name="rule-description"></a>Description de la règle
 <xref:System.ObsoleteAttribute> est utilisé pour marquer les membres et les types de bibliothèque déconseillés. Les consommateurs de bibliothèque doivent éviter l’utilisation de tout type ou membre qui est marqué comme obsolète. Il s’agit, car il ne peut pas être pris en charge et elles sont supprimée dans les versions ultérieures de la bibliothèque. Lorsqu’un type ou membre marquée à l’aide de <xref:System.ObsoleteAttribute> est compilé, le <xref:System.ObsoleteAttribute.Message%2A> propriété de l’attribut s’affiche. Cela fournit à l'utilisateur des informations sur le type ou le membre obsolète. Ces informations comprennent généralement la durée pendant laquelle le type obsolète ou membre sera être pris en charge par les concepteurs de bibliothèque et le remplacement par défaut à utiliser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez le `message` paramètre à la <xref:System.ObsoleteAttribute> constructeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas d’avertissement de cette règle, car le <xref:System.ObsoleteAttribute.Message%2A> propriété fournit des informations critiques sur le type ou membre obsolète.

## <a name="example"></a>Exemple
 L’exemple suivant montre un membre obsolète qui a correctement déclaré <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
