---
title: "Le type de &#39;&lt;nom_variable&gt;&#39; ne peut pas &#234;tre d&#233;duit &#224; partir d’une expression contenant &#39;&lt;nom_variable&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30980"
  - "bc30980"
helpviewer_keywords: 
  - "BC30980"
ms.assetid: 43a5d008-5362-481b-845b-b9bb00a61a83
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type de &#39;&lt;nom_variable&gt;&#39; ne peut pas &#234;tre d&#233;duit &#224; partir d’une expression contenant &#39;&lt;nom_variable&gt;&#39;
Le compilateur ne peut pas déduire le type de données d’une variable si celle\-ci est utilisée pour établir sa valeur initiale dans la déclaration.  
  
 Par exemple, quand `Option Infer` a la valeur `On`, les exemples suivants ne sont pas compilés :  
  
-   Déclarations  
  
    ```  
    ' Does not compile with Option Infer on. Dim m = m Dim d = someFunction(d)  
    ```  
  
-   Boucle `For`  
  
    ```  
    ' Does not compile with Option Infer on. For j = 1 To j Next  
    ```  
  
-   Boucle `For Each`  
  
    ```  
    ' Does not compile with Option Infer on. For Each customer In customer.Orders Next  
    ```  
  
 **ID d’erreur :** BC30980  
  
### Pour corriger cette erreur  
  
-   Si les deux variables sont censées faire référence à des valeurs différentes, modifiez le nom de la variable que vous déclarez.  
  
-   Utilisez une valeur littérale au lieu du nom de variable dans la valeur initiale, du côté droit de l’assignation.  
  
-   Utilisez une clause `As` pour spécifier le type de la variable que vous déclarez.  
  
## Voir aussi  
 [Dim Statement](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [For Each...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [For...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Local Type Inference](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement)