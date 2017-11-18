---
title: "CA1407 : Éviter les membres statiques dans les types visibles par COM | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 43240b8969026a8bbec18528230d3ca97bcb2236
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407 : Éviter les membres statiques dans les types visibles par COM
|||  
|-|-|  
|TypeName|AvoidStaticMembersInComVisibleTypes|  
|CheckId|CA1407|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type qui est marqué spécifiquement comme visible pour COM Component Object Model () contient un `public``static` (méthode).  
  
## <a name="rule-description"></a>Description de la règle  
 COM ne prend pas en charge `static` méthodes.  
  
 Cette règle ignore la propriété et les accesseurs d’événement, les méthodes, ou des méthodes qui sont marquées à l’aide de la surcharge d’opérateur la <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> attribut ou <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attribut.  
  
 Par défaut, les éléments suivants sont visibles par COM : assemblys, types publics, membres d’instance publics dans des types publics et tous les membres de types valeur publics.  
  
 Pour cette règle se produise, de niveau assembly <xref:System.Runtime.InteropServices.ComVisibleAttribute> doit avoir la valeur `false` et la classe - <xref:System.Runtime.InteropServices.ComVisibleAttribute> doit avoir la valeur `true`, comme le montre le code suivant.  
  
```csharp  
using System;  
using System.Runtime.InteropServices;   
  
[assembly: ComVisible(false)]   
namespace Samples  
{      
    [ComVisible(true)]  
    public class MyClass  
    {  
        public static void DoSomething()  
        {  
        }  
    }  
}  
```  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez le design pour utiliser une méthode d’instance qui fournit les mêmes fonctionnalités que le `static` (méthode).  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si un client COM ne requiert pas l’accès à la fonctionnalité fournie par le `static` (méthode).  
  
## <a name="example-violation"></a>Exemple de Violation  
  
### <a name="description"></a>Description  
 L’exemple suivant montre un `static` méthode qui enfreint cette règle.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]  
  
### <a name="comments"></a>Commentaires  
 Dans cet exemple, le **Book.FromPages** méthode ne peut pas être appelée à partir de COM.  
  
## <a name="example-fix"></a>Exemple de correctif  
  
### <a name="description"></a>Description  
 Pour corriger la violation dans l’exemple précédent, vous pouvez modifier la méthode et une méthode d’instance, mais qui ne se justifie pas dans cette instance. Une meilleure solution consiste à appliquer explicitement `ComVisible(false)` à la méthode pour le rendre clairement aux autres développeurs que la méthode ne peut pas être visible à partir de COM.  
  
 L’exemple suivant applique <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> à la méthode.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1017 : Marquez les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
 [CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)  
  
 [CA1413 : Évitez les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Interopération avec du code non managé](/dotnet/framework/interop/index)