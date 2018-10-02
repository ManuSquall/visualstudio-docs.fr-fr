---
title: 'CA1041 : Fournir un message ObsoleteAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: 298f6d3cbfc8b71443fe9e8e9733e5729963cea8
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590336"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041 : Fournir un message ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1041 : un message ObsoleteAttribute fournir](https://docs.microsoft.com/visualstudio/code-quality/ca1041-provide-obsoleteattribute-message).

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



