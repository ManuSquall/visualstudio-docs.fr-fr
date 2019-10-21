---
title: 'Ca1017 : marquer les assemblys avec ComVisibleAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 505e5780b8a50113aaf98ea7dbac767d280bebb6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662068"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017 : Marquer les assemblys avec ComVisibleAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Aucun attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> n’est appliqué à un assembly.

## <a name="rule-description"></a>Description de la règle
 L’attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> détermine la façon dont les clients COM accèdent au code managé. Un bon design stipule que les assemblys indiquent explicitement la visibilité COM. La visibilité COM peut être définie pour un assembly entier, puis substituée pour des types et des membres de type individuels. Si l’attribut n’est pas présent, le contenu de l’assembly est visible par les clients COM.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez l’attribut à l’assembly. Si vous ne souhaitez pas que l’assembly soit visible par les clients COM, appliquez l’attribut et affectez-lui la valeur `false`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Si vous souhaitez que l’assembly soit visible, appliquez l’attribut et affectez-lui la valeur `true`.

## <a name="example"></a>Exemple
 L’exemple suivant montre un assembly dont l’attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> est appliqué pour empêcher qu’il soit visible par les clients COM.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>Voir aussi
 Interopérabilité [avec du code non managé](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [qualifiant les types .net pour l’interopérabilité](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
