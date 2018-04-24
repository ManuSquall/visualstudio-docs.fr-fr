---
title: 'CA1060 : Déplacer P-appelle vers une classe NativeMethods'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 806721f5d2d02752be539675571fbcef16696ebf
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060 : Déplacer les P/Invoke vers une classe NativeMethods
|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode utilise des Services d’appel de plateforme pour accéder au code non managé et n’est pas un membre de l’un de le **NativeMethods** classes.

## <a name="rule-description"></a>Description de la règle
 Méthodes d’appel de plateforme, telles que celles qui sont marquées à l’aide de la <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attribut, ou les méthodes qui sont définies à l’aide de la `Declare` mot clé dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], accéder au code non managé. Ces méthodes doivent être dans une des classes suivantes :

-   **NativeMethods** -cette classe ne supprime pas le parcours de pile pour l’autorisation de code non managé. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> ne doit pas être appliqué à cette classe.) Cette classe est pour les méthodes qui peuvent être utilisées partout, car un parcours de pile sera effectué.

-   **SafeNativeMethods** -cette classe supprime des parcours de pile pour l’autorisation de code non managé. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> est appliqué à cette classe.) Cette classe est pour les méthodes qui sont sécurisés pour tout le monde à appeler. Les appelants de ces méthodes ne sont pas requis pour effectuer une révision de sécurité complète pour vous assurer que l’utilisation est sécurisée, car les méthodes sont sans conséquence pour tout appelant.

-   **UnsafeNativeMethods** -cette classe supprime des parcours de pile pour l’autorisation de code non managé. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> est appliqué à cette classe.) Cette classe est pour les méthodes qui sont potentiellement dangereux. Tout appelant de ces méthodes doit effectuer une révision de sécurité complète pour vous assurer que l’utilisation est sécurisée, car aucun parcours de pile ne sera effectuée.

 Ces classes sont déclarées en tant que `internal` (`Friend`, en Visual Basic) et déclarer un constructeur privé pour empêcher la création de nouvelles instances. Les méthodes de ces classes doivent être `static` et `internal` (`Shared` et `Friend` en Visual Basic).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, placez la méthode dans les **NativeMethods** classe. La plupart des applications, déplacer les P/Invoke vers une nouvelle classe nommée **NativeMethods** est suffisant.

 Toutefois, si vous développez des bibliothèques pour une utilisation dans d’autres applications, vous devez envisager de définir deux autres classes qui sont appelées **SafeNativeMethods** et **UnsafeNativeMethods**. Ces classes ressemblent à la **NativeMethods** classe ; Toutefois, elles sont marquées à l’aide d’un attribut spécial appelé **SuppressUnmanagedCodeSecurityAttribute**. Lorsque cet attribut est appliqué, le runtime n’effectue pas un parcours de pile complet pour vous assurer que tous les appelants ont le **UnmanagedCode** autorisation. Le runtime vérifie habituellement cette autorisation au démarrage. Étant donné que le contrôle n’est pas effectué, elle peut améliorer considérablement les performances pour les appels à ces méthodes non managées, il permet également au code qui a des autorisations limitées pour appeler ces méthodes.

 Toutefois, vous devez utiliser cet attribut avec précaution. Il peut avoir des implications en matière de sécurité si elle est implémentée de manière incorrecte...

 Pour plus d’informations sur la façon d’implémenter les méthodes, consultez le **NativeMethods** exemple, **SafeNativeMethods** exemple, et **UnsafeNativeMethods** exemple.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant déclare une méthode qui viole cette règle. Pour corriger la violation, la **RemoveDirectory** P/Invoke vers une classe appropriée est conçue pour contenir uniquement P/Invoke doivent être déplacé.

 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]

## <a name="nativemethods-example"></a>Exemple de classe NativeMethods

### <a name="description"></a>Description
 Étant donné que la **NativeMethods** classe ne doit pas être marquée à l’aide de **SuppressUnmanagedCodeSecurityAttribute**, P/Invoke qui sont placées dans il nécessitera **UnmanagedCode** autorisation. Étant donné que la plupart des applications s’exécutent à partir de l’ordinateur local et s’exécuter avec une confiance totale, il s’agit généralement pas un problème. Toutefois, si vous développez des bibliothèques réutilisables, vous devez envisager de définir un **SafeNativeMethods** ou **UnsafeNativeMethods** classe.

 L’exemple suivant montre une **Interaction.Beep** méthode qui encapsule le **MessageBeep** fonction à partir de user32.dll. Le **MessageBeep** P/Invoke est placé dans le **NativeMethods** classe.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]

## <a name="safenativemethods-example"></a>Exemple SafeNativeMethods

### <a name="description"></a>Description
 Les méthodes P/Invoke qui peuvent être exposés en toute sécurité à n’importe quelle application et qui n’ont pas d’effets secondaires doivent être placées dans une classe nommée **SafeNativeMethods**. Vous n’avez pas à demander des autorisations et vous n’êtes pas obligé de trop attention à où elles sont appelées à partir de.

 L’exemple suivant montre une **Environment.TickCount** propriété qui encapsule le **GetTickCount** fonction à partir de kernel32.dll.

### <a name="code"></a>Code
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]

## <a name="unsafenativemethods-example"></a>Exemple UnsafeNativeMethods

### <a name="description"></a>Description
 Les méthodes P/Invoke qui ne peut pas être appelée en toute sécurité et qui peuvent provoquer des effets secondaires doivent être placées dans une classe nommée **UnsafeNativeMethods**. Ces méthodes doivent être vérifiées rigoureusement pour vous assurer qu’elles ne sont pas exposées à l’utilisateur par inadvertance. La règle [CA2118 : l’utilisation de SuppressUnmanagedCodeSecurityAttribute de révision](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) peut y contribuer. Les méthodes doivent également avoir une autre autorisation demandée au lieu de **UnmanagedCode** lors de leur utilisation.

 L’exemple suivant montre un **Cursor.Hide** méthode qui encapsule le **ShowCursor** fonction à partir de user32.dll.

### <a name="code"></a>Code
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]

## <a name="see-also"></a>Voir aussi
 [Avertissements liés à la conception](../code-quality/design-warnings.md)