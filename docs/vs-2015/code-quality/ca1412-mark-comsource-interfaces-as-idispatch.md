---
title: 'CA1412 : marquer les interfaces ComSource comme IDispatch | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5685ad7a760e00392b5f9684cdf399ee320d4a0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540255"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412 : Marquer les interfaces ComSource comme IDispatch
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Un type est marqué avec l' <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> attribut et au moins une interface spécifiée n’est pas marquée avec l' <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attribut défini sur la `InterfaceIsDispatch` valeur.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> est utilisé pour identifier les interfaces d’événement qu’une classe expose aux clients COM (Component Object Model). Ces interfaces doivent être exposées comme `InterfaceIsIDispatch` pour permettre à Visual Basic 6 clients com de recevoir des notifications d’événements. Par défaut, si une interface n’est pas marquée avec l' <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attribut, elle est exposée en tant qu’interface double.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez ou modifiez l' <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attribut afin que sa valeur soit définie sur InterfaceIsIDispatch pour toutes les interfaces spécifiées avec l' <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une classe dans laquelle l’une des interfaces enfreint la règle.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1408 : Ne pas utiliser le paramètre AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Voir aussi
 [Comment : déclencher des événements gérés par un récepteur com](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [qui interopèrent avec du code non managé](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
