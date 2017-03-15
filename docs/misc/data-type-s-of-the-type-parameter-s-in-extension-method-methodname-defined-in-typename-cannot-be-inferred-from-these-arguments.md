---
title: "Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type dans la m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;&lt;nom_type&gt;&#39; &#224; partir de ces arguments | Microsoft Docs"
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
  - "bc36649"
  - "vbc36646"
  - "bc36646"
  - "vbc36649"
helpviewer_keywords: 
  - "BC36649"
  - "BC36649"
ms.assetid: 55274b01-6d78-4950-861e-07d9273ef76e
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de d&#233;duire le ou les types de donn&#233;es du ou des param&#232;tres de type dans la m&#233;thode d’extension &#39;&lt;nom_m&#233;thode&gt;&#39; d&#233;finie dans &#39;&lt;nom_type&gt;&#39; &#224; partir de ces arguments
Impossible de déduire le ou les types de données du ou des paramètres de type dans la méthode d’extension '\<nom\_méthode\>' définie dans '\<nom\_type\>' à partir de ces arguments. La spécification explicite du ou des types de données peut permettre de corriger cette erreur.  
  
 L’utilisateur a tenté d’utiliser l’inférence de type pour déterminer le ou les types de données du ou des paramètres de type pendant l’évaluation d’un appel à une méthode d’extension générique. Cependant, le compilateur ne parvenant pas à trouver un type de données pour les paramètres de type de cette méthode, il signale l’erreur.  
  
> [!NOTE]
>  Quand la spécification des arguments n’est pas une option \(par exemple, pour les opérateurs de requête dans les expressions de requête\), le message d’erreur apparaît sans la deuxième phrase.  
  
 Le code suivant illustre cette erreur.  
  
```vb#  
Module Module1 Sub Main() Dim classInstance As ClassExample '' Not valid. 'classInstance.GenericExtensionMethod("Hello", "World") End Sub <System.Runtime.CompilerServices.Extension()> _ Sub GenericExtensionMethod(Of T)(ByVal classEx As ClassExample, _ ByVal x As String, ByVal y As _ InterfaceExample(Of T)) End Sub End Module Interface InterfaceExample(Of T) End Interface Class ClassExample End Class  
```  
  
 **ID d’erreur :** BC36649 et BC36646  
  
### Pour corriger cette erreur  
  
-   Vous pourrez peut\-être spécifier un type de données pour le ou les paramètres de type au lieu de compter sur l’inférence de type.  
  
## Voir aussi  
 [Relaxed Delegate Conversion](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [méthodes d'extension.](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)