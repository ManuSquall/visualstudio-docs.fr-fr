---
title: "Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type dans la m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; &#224; partir de ces arguments | Microsoft Docs"
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
  - "vbc36648"
  - "bc36645"
  - "bc36648"
  - "vbc36645"
helpviewer_keywords: 
  - "BC36648"
  - "BC36645"
ms.assetid: cc8c67bb-6cbb-4d7c-ba26-fe1d38908434
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type dans la m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; &#224; partir de ces arguments
Impossible de déduire le ou les types de données du ou des paramètres de type dans la méthode '\<nom\_méthode\>' à partir de ces arguments. La spécification explicite du ou des types de données peut permettre de corriger cette erreur.  
  
 Une tentative a été faite d’utiliser l’inférence de type pour déterminer le ou les types de données du ou des paramètres de type pendant l’évaluation d’un appel à une procédure générique. Toutefois, le compilateur n’est pas en mesure de trouver un type de données pour les paramètres de type dans cette méthode et il signale l’erreur.  
  
> [!NOTE]
>  Quand la spécification des arguments n’est pas une option \(par exemple pour les opérateurs de requête dans les expressions de requête\), le message d’erreur apparaît sans la deuxième phrase.  
  
 Par exemple, le code suivant illustre cette erreur.  
  
```vb#  
Module Module1 Sub Main() '' Not valid. 'GenericMethod("Hello", "World") End Sub Sub GenericMethod(Of T)(ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface  
```  
  
 **ID d’erreur :** BC36648 et BC36645  
  
### Pour corriger cette erreur  
  
-   Vous pourrez peut\-être spécifier un type de données pour le ou les paramètres de type au lieu de compter sur l’inférence de type.  
  
## Voir aussi  
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)