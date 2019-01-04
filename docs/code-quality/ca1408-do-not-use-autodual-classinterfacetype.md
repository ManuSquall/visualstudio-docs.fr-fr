---
title: 'CA1408 : Ne pas utiliser AutoDual ClassInterfaceType'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8711ed43749d7bea2c69cee4dd4cb0f0160996a3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844286"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408 : Ne pas utiliser AutoDual ClassInterfaceType

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type visible de composant COM (Object Model) est marqué avec le <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribut défini sur le `AutoDual` valeur <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Description de la règle
 Les types qui utilisent une interface double permettent aux clients de se lier à une disposition d'interface spécifique. Les modifications apportées à une version future de la disposition du type ou des types de base bloquent les clients COM qui se lient à l'interface. Par défaut, si le <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribut n’est pas spécifié, une interface de répartition uniquement est utilisée.

 Sauf mention contraire, tous les types non génériques publics sont visibles par COM ; tous les types non publics et génériques ne sont pas visibles par COM.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la valeur de la <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribut le `None` valeur <xref:System.Runtime.InteropServices.ClassInterfaceType> et définissez explicitement l’interface.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas d’avertissement de cette règle, sauf si vous êtes certain que la disposition du type et ses types de base ne changera pas dans une future version.

## <a name="example"></a>Exemple
 L’exemple suivant montre une classe qui enfreint la règle et une nouvelle déclaration de la classe à utiliser une interface explicite.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Règles associées
 [CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412 : Marquer les Interfaces ComSource comme IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Voir aussi

- [Qualifier des types .NET pour l'interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interopération avec du code non managé](/dotnet/framework/interop/index)