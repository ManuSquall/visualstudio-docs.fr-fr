---
title: "CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6 | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ed47a2ccea76ce9cb6e2a1ef6dd73d53c961544c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6
|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|Category|Microsoft.Interoperability|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type qui est marqué spécifiquement comme visible pour COM Component Object Model () déclare un membre qui accepte un <xref:System.Int64?displayProperty=fullName> argument.  
  
## <a name="rule-description"></a>Description de la règle  
 Les clients COM Visual Basic 6 ne peuvent pas accéder aux entiers de 64 bits.  
  
 Par défaut, les éléments suivants sont visibles par COM : assemblys, types publics, membres d’instance publics dans des types publics et tous les membres de types valeur publics. Toutefois, pour réduire les faux positifs, cette règle requiert que la visibilité COM du type à être défini explicitement ; l’assembly conteneur doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> la valeur `false` et le type doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute> la valeur `true`.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle pour un paramètre dont la valeur peut toujours être exprimée comme un entier 32 bits, modifiez le type de paramètre <xref:System.Int32?displayProperty=fullName>. Si la valeur du paramètre peut être plus grande que peut être exprimée comme un entier 32 bits, modifier le type de paramètre pour <xref:System.Decimal?displayProperty=fullName>. Notez que les deux <xref:System.Single?displayProperty=fullName> et <xref:System.Double?displayProperty=fullName> perte de précision dans les plages supérieures de le <xref:System.Int64> type de données. Si le membre n’est pas destiné à être visible par COM, marquez-le avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute> la valeur `false`.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle s’il est certain que les clients COM Visual Basic 6 n’accèdent pas le type.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui enfreint la règle.  
  
 [!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1413 : Évitez les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407 : Éviter les membres statiques dans les types visibles par COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017 : Marquez les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Interopération avec du code non managé](/dotnet/framework/interop/index)   
 [Long (type de données)](/dotnet/visual-basic/language-reference/data-types/long-data-type)