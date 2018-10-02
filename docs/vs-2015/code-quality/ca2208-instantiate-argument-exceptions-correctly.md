---
title: 'CA2208 : Instanciez les exceptions d’argument | Microsoft Docs'
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
- CA2208
- InstantiateArgumentExceptionsCorrectly
helpviewer_keywords:
- InstantiateArgumentExceptionsCorrectly
- CA2208
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ba99cddfe42e1b6699dba4fa665302581aa68cdc
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590018"
---
# <a name="ca2208-instantiate-argument-exceptions-correctly"></a>CA2208 : Instanciez les exceptions d’argument comme il se doit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2208 : Instanciez les exceptions d’argument](https://docs.microsoft.com/visualstudio/code-quality/ca2208-instantiate-argument-exceptions-correctly).

|||
|-|-|
|TypeName|InstantiateArgumentExceptionsCorrectly|
|CheckId|CA2208|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Les causes possibles incluent les situations suivantes :

-   Un appel est effectué au constructeur par défaut (sans paramètre) d’un type d’exception qui est ou dérive [System.ArgumentException] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException?qualifyHint=True&amp;autoUpgrade=True>  -->).

-   Un argument string incorrect est passé à un constructeur paramétrable d’un type d’exception qui est ou dérive [System.ArgumentException.] (<!-- TODO: review code entity reference <xref:assetId:///System.ArgumentException.?qualifyHint=True&amp;autoUpgrade=True>  -->)

## <a name="rule-description"></a>Description de la règle
 Au lieu d’appeler le constructeur par défaut, appelez une des surcharges de constructeur qui permet à un message d’exception plus explicite doit être fourni. Le message d’exception doit cibler le développeur et expliquer clairement la condition d’erreur et comment corriger ou éviter l’exception.

 Les signatures des constructeurs de chaîne un et deux de <xref:System.ArgumentException> et ses types dérivés ne sont pas cohérents par rapport à la `message` et `paramName` paramètres. Assurez-vous que ces constructeurs sont appelés avec les arguments de chaîne correcte. Les signatures sont les suivantes :

 <xref:System.ArgumentException>(chaîne `message`)

 <xref:System.ArgumentException>(chaîne `message`, chaîne `paramName`)

 <xref:System.ArgumentNullException>(chaîne `paramName`)

 <xref:System.ArgumentNullException>(chaîne `paramName`, chaîne `message`)

 <xref:System.ArgumentOutOfRangeException>(chaîne `paramName`)

 <xref:System.ArgumentOutOfRangeException>(chaîne `paramName`, chaîne `message`)

 <xref:System.DuplicateWaitObjectException>(chaîne `parameterName`)

 <xref:System.DuplicateWaitObjectException>(chaîne `parameterName`, chaîne `message`)

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appelez un constructeur qui accepte un message, un nom de paramètre ou les deux et assurez-vous que les arguments sont appropriées pour le type de <xref:System.ArgumentException> qui est appelée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle uniquement si un constructeur paramétrable est appelé avec les arguments de chaîne correcte.

## <a name="example"></a>Exemple
 L’exemple suivant montre un constructeur qui n’instancie pas correctement une instance du type ArgumentNullException.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#1)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#1)]

## <a name="example"></a>Exemple
 L’exemple suivant résout la violation ci-dessus en passant les arguments de constructeur.

 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cpp/FxCop.Usage.InheritedPublic.cpp#2)]
 [!code-csharp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/cs/FxCop.Usage.InheritedPublic.cs#2)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InstantiateArgumentExceptionsCorrectly/vb/FxCop.Usage.InstantiateArgumentExceptionsCorrectly.vb#2)]



