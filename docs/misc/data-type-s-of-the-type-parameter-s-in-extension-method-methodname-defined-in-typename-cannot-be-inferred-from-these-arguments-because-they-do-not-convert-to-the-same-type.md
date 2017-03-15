---
title: "Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type dans la m&#233;thode d&#39;extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;typename&#39; &#224; partir de ces arguments, car ils ne sont pas convertis vers le m&#234;me type | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36658"
  - "bc36661"
  - "vbc36661"
  - "bc36658"
helpviewer_keywords: 
  - "BC36661"
  - "BC36658"
ms.assetid: 0bff97fd-cbe9-4433-8192-6498c6fb5d04
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type dans la m&#233;thode d&#39;extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;typename&#39; &#224; partir de ces arguments, car ils ne sont pas convertis vers le m&#234;me type
Impossible de déduire le ou les types de données du ou des paramètres de type dans la méthode d'extension '\<nom\_méthode\>' définie dans 'typename' à partir de ces arguments, car ils ne sont pas convertis vers le même type. La spécification explicite du ou des types de données peut permettre de corriger cette erreur.  
  
 Une tentative a été faite d’utiliser l’inférence de type pour déterminer le ou les types de données du ou des paramètres de type pendant l’évaluation d’un appel à une méthode d’extension générique. Le compilateur n’a pas pu trouvé un type de données qui satisfait aux contraintes de tous les arguments. Par conséquent, il a signalé cette erreur.  
  
> [!NOTE]
>  Quand la spécification des arguments n’est pas une option \(par exemple pour les opérateurs de requête dans les expressions de requête\), le message d’erreur apparaît sans la deuxième phrase.  
  
 Le code suivant illustre cette erreur.  
  
```vb#  
Option Strict Off Module Module3 Sub Main() Dim c1 As New Class1 '' Not valid. Integer and Date do not convert to the same type. 'c1.targetMethod(19, #3/4/2007#) End Sub <System.Runtime.CompilerServices.Extension()> _ Sub targetMethod(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **ID d’erreur :** BC36661 et BC36658  
  
### Pour corriger cette erreur  
  
-   Vous pourrez peut\-être convertir explicitement un ou plusieurs arguments en type compatible, comme indiqué dans le code suivant :  
  
    ```  
    c1.targetMethod(19, #3/4/2007#.ToOADate)  
    ```  
  
-   Vous pourrez peut\-être spécifier un type de données pour le ou les paramètres de type dans lesquels les arguments se convertissent, comme indiqué dans le code suivant :  
  
    ```  
    c1.targetMethod(Of String)(19, #3/4/2007#)  
    ```  
  
## Voir aussi  
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type Conversion Functions](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)