---
title: "Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type dans la m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;&lt;nom_type&gt;&#39; &#224; partir de ces arguments, car plusieurs types sont possibles | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36655"
  - "vbc36652"
  - "vbc36655"
  - "bc36652"
helpviewer_keywords: 
  - "BC36655"
  - "BC36652"
ms.assetid: 49836f20-c877-4267-8bdc-6f6d108fb8c0
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type dans la m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;&lt;nom_type&gt;&#39; &#224; partir de ces arguments, car plusieurs types sont possibles
Impossible de déduire le ou les types de données du ou des paramètres de type dans la méthode d’extension '\<nom\_méthode\>' définie dans '\<nom\_type\>' à partir de ces arguments, car plusieurs types sont possibles. La spécification explicite du ou des types de données peut permettre de corriger cette erreur.  
  
 L’utilisateur a tenté d’utiliser l’inférence de type pour déterminer le ou les types du ou des paramètres de type dans un appel à une méthode d’extension générique. Le compilateur détecte plusieurs types de données possibles pour un ou plusieurs des paramètres de type, et il signale cette erreur.  
  
> [!NOTE]
>  Quand la spécification des arguments n’est pas une option \(par exemple pour les opérateurs de requête dans les expressions de requête\), le message d’erreur apparaît sans la deuxième phrase.  
  
 Le code suivant illustre cette erreur.  
  
```vb#  
Option Strict Off Imports System.Runtime.CompilerServices Module Module1 Sub Main() Dim caller As New Class1 '' Not valid. 'caller.targetExtension(1, "2") End Sub <Extension()> _ Sub targetExtension(Of T)(ByVal p0 As Class1, ByVal p1 As T, ByVal p2 As T) End Sub Class Class1 End Class End Module  
```  
  
 **ID d’erreur :** BC36655 \(dans les requêtes [!INCLUDE[vbteclinq](../misc/includes/vbteclinq_md.md)]\) et BC36652 \(en dehors des requêtes\)  
  
### Pour corriger cette erreur  
  
-   Si l’erreur s’affiche en dehors d’une requête, essayez de spécifier le type de données du ou des paramètres de type de manière explicite :  
  
    ```  
    caller.targetExtension(Of Integer)(1, "2") caller.targetExtension(Of String)(1, "2")  
    ```  
  
## Voir aussi  
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)