---
title: "CA1060&#160;: D&#233;placer les P/Invoke vers une classe NativeMethods | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MovePInvokesToNativeMethodsClass"
  - "CA1060"
helpviewer_keywords: 
  - "CA1060"
  - "MovePInvokesToNativeMethodsClass"
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1060&#160;: D&#233;placer les P/Invoke vers une classe NativeMethods
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode utilise des services d'appel de code non managé pour accéder à du code non managé et n'est membre d'aucune des classes **NativeMethods**.  
  
## Description de la règle  
 Les méthodes d'appel de code non managé, telles que celles qui sont marquées avec l'attribut <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> \(ou les méthodes définies à l'aide du mot clé `Declare` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) accèdent à du code non managé.  Ces méthodes doivent se trouver dans l'une des classes suivantes :  
  
-   **NativeMethods** \- Cette classe ne supprime aucun parcours de pile pour l'autorisation de code non managé. \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> ne doit pas être appliqué à cette classe.\) Cette classe est destinée aux méthodes qui ne peuvent pas être utilisées n'importe où, du fait de l'exécution d'un parcours de pile.  
  
-   **SafeNativeMethods** \- Cette classe supprime des parcours de pile pour l'autorisation de code non managé. \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> est appliqué à cette classe.\) Cette classe est destinée aux méthodes qui garantissent la sécurité de tous les appelants.  Les appelants de ces méthodes ne sont pas contraints de procéder à une révision de sécurité complète pour garantir la sécurisation de leur utilisation car elles ne présentent de danger pour aucun appelant.  
  
-   **UnsafeNativeMethods** \- Cette classe supprime des parcours de pile pour l'autorisation de code non managé. \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> est appliqué à cette classe.\) Cette classe est destinée à des méthodes potentiellement dangereuses.  Tout appelant de ces méthodes doit procéder à une révision de sécurité complète pour garantir la sécurisation de leur utilisation, car aucun parcours de pile ne sera effectué.  
  
 Ces classes sont déclarées en tant que `internal` \(`Friend` en Visual Basic\) et déclarent un constructeur privé pour empêcher la création de nouvelles instances.  Les méthodes présentes dans ces classes doivent être `static` et `internal` \(`Shared` et `Friend` en Visual Basic\).  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, placez la méthode dans la classe **NativeMethods** appropriée.  Pour la plupart des applications, le fait de déplacer les P\/Invoke vers une classe nouvelle nommée **NativeMethods** est suffisant.  
  
 Toutefois, si vous développez des bibliothèques pour une utilisation dans d'autres applications, vous devez envisager de définir deux autres classes appelées **SafeNativeMethods** et **UnsafeNativeMethods**.  Ces classes ressemblent à la classe **NativeMethods**. Toutefois, elles sont marquées avec un attribut spécial appelé **SuppressUnmanagedCodeSecurityAttribute**.  Lorsque cet attribut est appliqué, l'exécution n'effectue pas de parcours complet de la pile afin de s'assurer que tous les appelants ont l'autorisation **UnmanagedCode**.  Le runtime vérifie habituellement la présence de cette autorisation au démarrage.  Dans la mesure où le contrôle n'est pas effectué, cela peut améliorer grandement la performance pour les appels à ces méthodes non managées, et permet également au code avec des autorisations limitées d'appeler ces méthodes.  
  
 Cependant, vous devez utiliser cet attribut avec précaution.  Les conséquences au niveau de la sécurité peuvent être sérieuses s'il est implémenté de manière incorrecte.  
  
 Pour plus d'informations sur l'implémentation de ces méthodes, consultez les exemples **NativeMethods**, **SafeNativeMethods** et **UnsafeNativeMethods**.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant déclare une méthode qui ne respecte pas cette règle.  Pour corriger la violation, le P\/Invoke **RemoveDirectory** doit être déplacé vers une classe appropriée destinée à contenir uniquement les P\/Invoke.  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-cs[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## Exemple NativeMethods  
  
### Description  
 Dans la mesure où la classe **NativeMethods** ne doit pas être marquée avec **SuppressUnmanagedCodeSecurityAttribute**, les P\/Invoke qui y sont placés nécessiteront l'autorisation **UnmanagedCode**.  Comme la plupart des applications s'exécutent ensemble à partir de l'ordinateur local et avec la confiance totale, ceci ne pose généralement pas problème.  Toutefois, si vous développez des bibliothèques réutilisables, vous devez envisager de définir une classe **SafeNativeMethods** ou **UnsafeNativeMethods**.  
  
 L'exemple suivant affiche une méthode **Interaction.Beep** qui encapsule la fonction **MessageBeep** à partir d'user32.dll.  P\/Invoke de **MessageBeep** est placé dans la classe **NativeMethods**.  
  
### Code  
 [!code-cs[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## Exemple SafeNativeMethods  
  
### Description  
 Les méthodes P\/Invoke qui peuvent être exposées sans risque à toute application et qui n'ont pas d'effets secondaires doivent être placées dans une classe nommée **SafeNativeMethods**.  Vous n'avez pas à demander des autorisations et vous n'avez pas à faire trop attention à l'emplacement à partir duquel elles sont appelées.  
  
 L'exemple suivant affiche une propriété **Environment.TickCount** qui encapsule la fonction **GetTickCount** à partir de kernel32.dll.  
  
### Code  
 [!CODE [FxCop.Design.NativeMethodsSafe#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe#1)]  
  
## Exemple UnsafeNativeMethods  
  
### Description  
 Les méthodes P\/Invoke qui ne peuvent pas être appelées sans risque et qui peuvent provoquer des effets secondaires doivent être placées dans une classe nommée **UnsafeNativeMethods**.  Ces méthodes doivent être vérifiées rigoureusement pour s'assurer qu'elles ne sont pas exposées involontairement à l'utilisateur.  La règle [CA2118 : Révision de l'utilisation de SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) peut y contribuer.  Les méthodes doivent également avoir une autre autorisation demandée à la place du **UnmanagedCode** lorsqu'elles les utilisent.  
  
 L'exemple suivant montre une méthode **Cursor.Hide** qui encapsule la fonction **ShowCursor** à partir d'user32.dll.  
  
### Code  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-cs[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## Voir aussi  
 [Avertissements liés au design](../code-quality/design-warnings.md)