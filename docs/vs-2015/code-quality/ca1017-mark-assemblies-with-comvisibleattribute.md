---
title: 'CA1017 : Marquer les assemblys avec ComVisibleAttribute | Microsoft Docs'
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
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b5ce7d8a6bd63bc49a03661323ef17d131201cce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206945"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017 : Marquer les assemblys avec ComVisibleAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un assembly n’a pas la <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> attribut appliqué à ce dernier.

## <a name="rule-description"></a>Description de la règle
 Le <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribut détermine comment les clients COM accèdent à du code managé. Un bon design stipule que les assemblys indiquent explicitement la visibilité COM. Visibilité COM peut être définie pour un assembly entier et puis être substituée pour des types et membres de type. Si l’attribut n’est pas présent, le contenu de l’assembly est visible aux clients COM.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez l’attribut à l’assembly. Si vous ne souhaitez pas que l’assembly soit visible par les clients COM, appliquez l’attribut et définissez sa valeur sur `false`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Si vous souhaitez que l’assembly soit visible, appliquez l’attribut et définissez sa valeur sur `true`.

## <a name="example"></a>Exemple
 L’exemple suivant montre un assembly qui a le <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribut appliqué pour empêcher les clients COM.

 [!code-cpp[FxCop.Design.AssembliesCom#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cpp/FxCop.Design.AssembliesCom.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/cs/FxCop.Design.AssembliesCom.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCom/vb/FxCop.Design.AssembliesCom.vb#1)]

## <a name="see-also"></a>Voir aussi
 [Interopérabilité avec du Code non managé](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [qualification des Types .NET pour l’interopérabilité](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)



