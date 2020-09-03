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
ms.openlocfilehash: d738cf15ebe734cb74e553f38f6eb26af17e8cfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542309"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041 : Fournir un message ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|CheckId|CA1041|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Un type ou un membre est marqué à l’aide d’un <xref:System.ObsoleteAttribute?displayProperty=fullName> attribut dont la propriété n’est pas <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> spécifiée.

## <a name="rule-description"></a>Description de la règle
 <xref:System.ObsoleteAttribute> est utilisé pour marquer les membres et les types de bibliothèque déconseillés. Les consommateurs de bibliothèque doivent éviter l’utilisation de n’importe quel type ou membre marqué comme obsolète. Cela est dû au fait qu’il n’est peut-être pas pris en charge et sera finalement supprimé des versions ultérieures de la bibliothèque. Lorsqu’un type ou membre marqué à l’aide de <xref:System.ObsoleteAttribute> est compilé, la <xref:System.ObsoleteAttribute.Message%2A> propriété de l’attribut est affichée. Cela fournit à l'utilisateur des informations sur le type ou le membre obsolète. Ces informations incluent généralement la durée pendant laquelle le type ou le membre obsolète sera pris en charge par les concepteurs de bibliothèques et le remplacement par défaut à utiliser.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez le `message` paramètre au <xref:System.ObsoleteAttribute> constructeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle, car la <xref:System.ObsoleteAttribute.Message%2A> propriété fournit des informations critiques sur le type ou le membre obsolète.

## <a name="example"></a>Exemple
 L’exemple suivant montre un membre obsolète qui a un déclaré correctement <xref:System.ObsoleteAttribute> .

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
