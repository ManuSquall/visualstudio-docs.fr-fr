---
title: "Le type de &#39;&lt;nom_variable&gt;&#39; est ambigu car les limites de la boucle et la clause d’incr&#233;mentation ne sont pas converties en un m&#234;me type | Microsoft Docs"
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
  - "vbc30983"
  - "bc30983"
helpviewer_keywords: 
  - "BC30983"
ms.assetid: 6b97153c-dee3-4429-b92a-2e5a212c864b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type de &#39;&lt;nom_variable&gt;&#39; est ambigu car les limites de la boucle et la clause d’incr&#233;mentation ne sont pas converties en un m&#234;me type
Votre code contient une boucle `For...Next` dans laquelle le compilateur ne peut pas déduire un type de données pour la variable de contrôle de boucle, car les conditions suivantes sont remplies :  
  
-   Le type de données de la variable de contrôle de boucle n’est pas spécifié avec une clause `As`.  
  
-   Les limites de la boucle et l’incrémentation contiennent au moins deux types de données.  
  
-   Il existe plusieurs conversions possibles entre les types de données.  
  
-   Il n’existe aucun meilleur type parmi les candidats, si bien que le choix du type pour la variable de contrôle de boucle est ambigu.  
  
 Par exemple, la boucle suivante a une limite de boucle de type `Integer` et une autre de type `UInteger` :  
  
```vb#  
Dim m As Integer = 1 Dim n As UInteger = 10 ' Not valid. ' For i = m To n ' Loop processing. ' Next  
```  
  
 Il existe une conversion possible entre `Integer` et `UInteger`, et une conversion possible entre `UInteger` et `Integer`, mais les deux sont des conversions restrictives, donc aucune ne constitue le meilleur choix.  
  
 Dans l’exemple suivant, une troisième variable de type `Double` est ajoutée.`Integer` et `UInteger` ont des conversions étendues standard en `Double`, ce qui fait de la conversion en `Double` le meilleur choix. L’inférence de type assigne à la variable de contrôle de boucle `i` le type de données `Double`.  
  
```vb#  
Dim stepVar As Double = 1 ' Valid. For i = m To n Step stepVar ' Loop processing. Next  
```  
  
 **ID d’erreur :** BC30983  
  
### Pour corriger cette erreur  
  
-   Convertissez explicitement l’une des variables en un type vers lequel les autres ont une conversion étendue, par exemple :  
  
    ```  
    For i = m To CLng(n)  
    ```  
  
-   Utilisez une clause `As` pour spécifier le type de la variable de contrôle :  
  
    ```  
    For i As Double = m To n   
    ```  
  
## Voir aussi  
 [For...Next, instruction](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Local Type Inference](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)