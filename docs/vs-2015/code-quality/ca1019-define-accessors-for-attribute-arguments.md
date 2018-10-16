---
title: 'CA1019 : Définir des accesseurs pour les arguments d’attribut | Microsoft Docs'
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
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8c635555dd0378334c899a9d80de9bb3205dcc71
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260871"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019 : Définir des accesseurs pour les arguments d'attribut
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Dans son constructeur, un attribut définit des arguments qui n’ont pas de propriétés correspondantes.

## <a name="rule-description"></a>Description de la règle
 Les attributs peuvent définir des arguments obligatoires qui doivent être spécifiés lorsque vous appliquez l’attribut à une cible. Ceux-ci sont également appelés arguments positionnels parce qu’ils sont fournis aux constructeurs d’attributs en tant que paramètres positionnels. Pour chaque argument obligatoire, l’attribut doit également fournir une propriété en lecture seule correspondante afin que la valeur de l’argument puisse être récupérée au moment de l’exécution. Cette règle vérifie que, pour chaque paramètre de constructeur, vous avez défini la propriété correspondante.

 Les attributs peuvent également définir des arguments facultatifs, qui sont également appelés arguments nommés. Ces arguments sont fournis aux constructeurs d'attributs par noms et doivent disposer d'une propriété en lecture/écriture correspondante.

 Pour les arguments obligatoires et facultatifs, les propriétés correspondantes et les paramètres du constructeur doivent utiliser le même nom mais une casse différente. Propriétés utilisent Pascal casse et les paramètres la casse.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez une propriété en lecture seule pour chaque paramètre de constructeur qui n’en a pas.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle si vous ne souhaitez pas la valeur de l’argument obligatoire soit récupérable.

## <a name="custom-attributes-example"></a>Exemple d’attributs personnalisés

### <a name="description"></a>Description
 L’exemple suivant montre deux attributs qui définissent un paramètre obligatoire (positionnel). La première implémentation de l’attribut est définie incorrectement. La seconde implémentation est correcte.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Arguments nommés et positionnels

### <a name="description"></a>Description
 Arguments nommés et positionnels rendre clairement aux consommateurs de votre bibliothèque quels sont les arguments obligatoires pour l’attribut et les arguments sont facultatifs.

 L’exemple suivant illustre une implémentation d’un attribut qui a des arguments nommés et positionnels.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Commentaires
 L’exemple suivant montre comment appliquer l’attribut personnalisé à deux propriétés.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1813 : Évitez les attributs unsealed](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Voir aussi
 [Attributs](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



