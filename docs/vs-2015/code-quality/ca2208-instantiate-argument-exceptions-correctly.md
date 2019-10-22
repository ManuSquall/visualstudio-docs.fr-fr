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
ms.openlocfilehash: 5b5e1525d1ee706f9cd46a58c022763d2ed234bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662685"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208 : Instanciez les exceptions d’argument comme il se doit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
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

 Les signatures des constructeurs de chaîne un et deux de <xref:System.ArgumentException> et de ses types dérivés ne sont pas cohérentes par rapport aux paramètres de `message` et de `paramName`. Assurez-vous que ces constructeurs sont appelés avec les arguments de chaîne corrects. Les signatures sont les suivantes :

 <xref:System.ArgumentException> (chaîne `message`)

 <xref:System.ArgumentException> (chaîne `message`, chaîne `paramName`)

 <xref:System.ArgumentNullException> (chaîne `paramName`)

 <xref:System.ArgumentNullException> (chaîne `paramName`, chaîne `message`)

 <xref:System.ArgumentOutOfRangeException> (chaîne `paramName`)

 <xref:System.ArgumentOutOfRangeException> (chaîne `paramName`, chaîne `message`)

 <xref:System.DuplicateWaitObjectException> (chaîne `parameterName`)

 <xref:System.DuplicateWaitObjectException> (chaîne `parameterName`, chaîne `message`)

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez un constructeur qui prend un message, un nom de paramètre, ou les deux, et assurez-vous que les arguments sont corrects pour le type de <xref:System.ArgumentException> qui est appelé.

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
