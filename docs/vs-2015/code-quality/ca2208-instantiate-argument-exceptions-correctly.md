---
title: 'CA2208 : instanciez les exceptions d’argument correctement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a63ebb7f3946926864c4dd882c281b5dcd7c6c5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535835"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208 : Instanciez les exceptions d'argument comme il se doit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Les causes possibles sont les suivantes :

- Un appel est passé au constructeur par défaut (sans paramètre) d’un type d’exception qui est ou dérive de [System. ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

- Un argument de chaîne incorrect est passé à un constructeur paramétrable d’un type d’exception qui est ou dérive de [System. ArgumentException.] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Description de la règle
 Au lieu d’appeler le constructeur par défaut, appelez l’une des surcharges de constructeur qui permet de fournir un message d’exception plus explicite. Le message d’exception doit cibler le développeur et expliquer clairement la condition d’erreur et comment corriger ou éviter l’exception.

 Les signatures des constructeurs de chaîne un et deux de <xref:System.ArgumentException> et de ses types dérivés ne sont pas cohérentes par rapport aux `message` `paramName` paramètres et. Assurez-vous que ces constructeurs sont appelés avec les arguments de chaîne corrects. Les signatures sont les suivantes :

 <xref:System.ArgumentException>(chaîne `message` )

 <xref:System.ArgumentException>(String `message` , String `paramName` )

 <xref:System.ArgumentNullException>(chaîne `paramName` )

 <xref:System.ArgumentNullException>(String `paramName` , String `message` )

 <xref:System.ArgumentOutOfRangeException>(chaîne `paramName` )

 <xref:System.ArgumentOutOfRangeException>(String `paramName` , String `message` )

 <xref:System.DuplicateWaitObjectException>(chaîne `parameterName` )

 <xref:System.DuplicateWaitObjectException>(String `parameterName` , String `message` )

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez un constructeur qui accepte un message, un nom de paramètre, ou les deux, et assurez-vous que les arguments sont corrects pour le type d' <xref:System.ArgumentException> appel.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle uniquement si un constructeur paramétré est appelé avec les arguments de chaîne appropriés.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un constructeur qui instancie de manière incorrecte une instance du type ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Exemple
 L’exemple suivant résout la violation ci-dessus en basculant les arguments du constructeur.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]
