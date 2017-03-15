---
title: "CA1404&#160;: Appeler GetLastError imm&#233;diatement apr&#232;s P/Invoke | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
helpviewer_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1404&#160;: Appeler GetLastError imm&#233;diatement apr&#232;s P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 La méthode <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> ou la fonction `GetLastError` équivalente est appelée, et l'appel immédiatement avant ne constitue pas une méthode d'appel de code non managé.  
  
## Description de la règle  
 Une méthode d'appel de code non managé accède à un code non managé et est définie à l'aide du mot clé `Declare` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou de l'attribut <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  En général, en cas de défaillance, les fonctions non managées appellent la fonction de Win32 `SetLastError` pour définir un code d'erreur associé à la défaillance.  L'appelant de la fonction qui a échoué appelle la fonction Win32 `GetLastError` pour récupérer le code d'erreur et déterminer la cause de la défaillance.  Le code d'erreur est conservé "par thread" et remplacé par l'appel suivant à `SetLastError`.  À la suite d'une méthode d'appel de code non managé qui a échoué, le code managé peut récupérer le code d'erreur en appelant la méthode <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>.  Sachant que le code d'erreur peut être remplacé par des appels internes émanant d'autres méthodes de la bibliothèque de classes managée, la méthode `GetLastError` ou <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> doit être appelée immédiatement après l'appel de la méthode d'appel de code non managé.  
  
 La règle ignore les appels aux membres managés suivants lorsqu'ils se produisent entre l'appel à la méthode d'appel de code non managé et l'appel à <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>.  Ces membres ne modifient pas le code d'erreur et sont utiles pour déterminer la réussite de certains appels de méthode d'appel de code non managé.  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, redirigez l'appel vers <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> afin qu'il suive immédiatement l'appel à la méthode d'appel de code non managé.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si le code exécuté entre l'appel à la méthode d'appel de code non managé et l'appel à la méthode <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> ne peut pas explicitement ou implicitement provoquer la modification du code d'erreur.  
  
## Exemple  
 L'exemple suivant présente une méthode qui viole la règle et une autre qui satisfait à la règle.  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-cs[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## Règles connexes  
 [CA1060 : Déplacer les P\/Invoke vers une classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400 : Des points d'entrée P\/Invoke doivent exister](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)  
  
 [CA1401 : Les P\/Invoke ne doivent pas être visibles](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)  
  
 [CA2101 : Spécifiez le marshaling pour les arguments de chaîne P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205 : Utilisez des équivalents managés de l'API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)