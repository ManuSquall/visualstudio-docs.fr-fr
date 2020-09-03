---
title: 'CA1408 : ne pas utiliser le double-Dual ClassInterfaceType | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b953a97d557e28cce50f554acc03797d4be38220
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534873"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408 : Ne pas utiliser le paramètre AutoDual ClassInterfaceType
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Un type visible COM (Component Object Model) est marqué avec l' <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribut défini sur la `AutoDual` valeur de <xref:System.Runtime.InteropServices.ClassInterfaceType> .

## <a name="rule-description"></a>Description de la règle
 Les types qui utilisent une interface double permettent aux clients de se lier à une disposition d'interface spécifique. Les modifications apportées à une version future de la disposition du type ou des types de base bloquent les clients COM qui se lient à l'interface. Par défaut, si l' <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribut n’est pas spécifié, une interface de dispatch uniquement est utilisée.

 Sauf indication contraire, tous les types non génériques publics sont visibles par COM ; tous les types non publics et génériques sont invisibles pour COM.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez la valeur de l' <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribut par la `None` valeur de <xref:System.Runtime.InteropServices.ClassInterfaceType> et définissez explicitement l’interface.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle à moins qu’il ne soit certain que la disposition du type et de ses types de base ne changera pas dans une version ultérieure.

## <a name="example"></a>Exemple
 L’exemple suivant montre une classe qui enfreint la règle et une nouvelle déclaration de la classe pour utiliser une interface explicite.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412 : Marquer les interfaces ComSource comme IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Voir aussi
 [Présentation](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) des [types .net éligibles de l’interface de classe pour l’interopérabilité entre l’interopérabilité](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [et le code non managé](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
