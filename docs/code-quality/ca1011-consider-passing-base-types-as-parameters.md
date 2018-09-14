---
title: 'CA1011 : Si possible, transmettez les types de base en tant que paramètres'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5d44077dbe839fe6ce6b369f8d8b3b828bdb982a
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549428"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011 : Si possible, transmettez les types de base en tant que paramètres

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|CheckId|CA1011|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une déclaration de méthode inclut un paramètre formel est un type dérivé, et la méthode appelle uniquement les membres du type de base du paramètre.

## <a name="rule-description"></a>Description de la règle
 Lorsqu’un type de base est spécifié en tant que paramètre dans une déclaration de méthode, tout type dérivé du type de base peut être passé en tant qu’argument correspondant à la méthode. Lorsque l’argument est utilisé à l’intérieur du corps de méthode, la méthode spécifique qui est exécutée dépend du type de l’argument. Si la fonctionnalité supplémentaire fournie par le type dérivé n’est pas obligatoire, utilisation du type de base permet une utilisation plus large de la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifier le type du paramètre à son type de base.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle

- Si la méthode requiert la fonctionnalité spécifique fournie par le type dérivé

     \- ou -

- Pour mettre en œuvre que seul le type dérivé, ou un type plus dérivé, est passé à la méthode.

 Dans ce cas, le code sera plus robuste en raison de la vérification de type fort fourni par le compilateur et le runtime.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode, `ManipulateFileStream`, qui peut être utilisé uniquement avec un <xref:System.IO.FileStream> objet, ce qui enfreint cette règle. Une deuxième méthode, `ManipulateAnyStream`, satisfait la règle en remplaçant le <xref:System.IO.FileStream> paramètre en utilisant un <xref:System.IO.Stream>.

 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Règles associées
 [CA1059 : Les membres ne doivent pas exposer certains types concrets](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)