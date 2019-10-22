---
title: 'CA1011 : envisagez de passer des types de base en tant que paramètres | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3968d81e8ee18b4b0a56bed50f7aa1f121e1c074
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663244"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011 : Si possible, transmettez les types de base en tant que paramètres
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une déclaration de méthode comprend un paramètre formel qui est un type dérivé, et la méthode appelle uniquement les membres du type de base du paramètre.

## <a name="rule-description"></a>Description de la règle
 Lorsqu'un type de base est spécifié en tant que paramètre dans une déclaration de méthode, tout type dérivé du type de base peut être passé en tant qu'argument correspondant à la méthode. Lorsque l’argument est utilisé dans le corps de la méthode, la méthode spécifique qui est exécutée dépend du type de l’argument. Si les fonctionnalités supplémentaires fournies par le type dérivé ne sont pas requises, l’utilisation du type de base permet une utilisation plus étendue de la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez le type du paramètre par son type de base.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle

- Si la méthode requiert la fonctionnalité spécifique fournie par le type dérivé

   \- ou -

- pour garantir que seul le type dérivé, ou un type plus dérivé, est passé à la méthode.

  Dans ces cas, le code sera plus robuste en raison de la vérification de type fort fournie par le compilateur et le Runtime.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode, `ManipulateFileStream`, qui peut être utilisée uniquement avec un objet <xref:System.IO.FileStream>, ce qui viole cette règle. Une deuxième méthode, `ManipulateAnyStream`, répond à la règle en remplaçant le paramètre <xref:System.IO.FileStream> à l’aide d’un <xref:System.IO.Stream>.

 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cpp/FxCop.Design.ConsiderPassingBaseTypes.cpp#1)]
 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/cs/FxCop.Design.ConsiderPassingBaseTypes.cs#1)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ConsiderPassingBaseTypes/vb/FxCop.Design.ConsiderPassingBaseTypes.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1059 : Les membres ne doivent pas exposer certains types concrets](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)
