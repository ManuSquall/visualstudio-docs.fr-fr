---
title: "CA1041 : Fournir un message ObsoleteAttribute | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5d6c0ac4d5972e06768306be51a92e93da763ce0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041 : Fournir un message ObsoleteAttribute
|||  
|-|-|  
|TypeName|ProvideObsoleteAttributeMessage|  
|CheckId|CA1041|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type ou un membre est marqué avec un <xref:System.ObsoleteAttribute?displayProperty=fullName> attribut qui n’a pas son <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> propriété spécifiée.  
  
## <a name="rule-description"></a>Description de la règle  
 <xref:System.ObsoleteAttribute>est utilisé pour marquer les membres et les types de bibliothèque déconseillés. Les consommateurs de bibliothèque doivent éviter l’utilisation de tout type ou membre qui est marqué comme obsolète. Il s’agit, car il ne peut pas être pris en charge et elles sont supprimée des versions ultérieures de la bibliothèque. Lorsqu’un type ou membre marquée à l’aide de <xref:System.ObsoleteAttribute> est compilé, la <xref:System.ObsoleteAttribute.Message%2A> la propriété de l’attribut est affichée. Cela fournit à l'utilisateur des informations sur le type ou le membre obsolète. Ces informations comprennent généralement la durée pendant laquelle le type obsolète ou membre sera être pris en charge par les concepteurs de bibliothèque et le remplacement par défaut à utiliser.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez le `message` paramètre à la <xref:System.ObsoleteAttribute> constructeur.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle, car le <xref:System.ObsoleteAttribute.Message%2A> propriété fournit des informations essentielles sur le type ou membre obsolète.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un membre obsolète qui a correctement déclaré <xref:System.ObsoleteAttribute>.  
  
 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ObsoleteAttribute?displayProperty=fullName>