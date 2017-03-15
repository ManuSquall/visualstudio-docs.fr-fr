---
title: "CA1414&#160;: Marquer les arguments P/Invoke bool&#233;ens comme MarshalAs | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
helpviewer_keywords: 
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1414&#160;: Marquer les arguments P/Invoke bool&#233;ens comme MarshalAs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|CheckId|CA1414|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une déclaration de méthode d'appel de code non managé contient un paramètre <xref:System.Boolean?displayProperty=fullName> ou une valeur de retour, mais l'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> n'est pas appliqué au paramètre ou à la valeur de retour.  
  
## Description de la règle  
 Une méthode d'appel de code non managé accède à un code non managé et est définie à l'aide du mot clé `Declare` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou de l'attribut <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>.  <xref:System.Runtime.InteropServices.MarshalAsAttribute> spécifie le comportement de marshaling utilisé pour convertir des types de données entre codes managé et non managé.  Plusieurs types de données simples, par exemple <xref:System.Byte?displayProperty=fullName> et <xref:System.Int32?displayProperty=fullName>, ont une représentation unique dans le code non managé et leur comportement de marshaling ne doit pas être spécifié ; le Common Language Runtime fournit automatiquement le comportement correct.  
  
 Le type de données <xref:System.Boolean> contient plusieurs représentations dans le code non managé.  Lorsque <xref:System.Runtime.InteropServices.MarshalAsAttribute> n'est pas spécifié, le comportement de marshaling par défaut pour le type de données <xref:System.Boolean> est <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>.  Il s'agit d'un entier de 32 bits, qui ne convient pas dans toutes les situations.  La représentation Boolean requise par la méthode non managée doit être déterminée et mise en correspondance avec le <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> approprié.  UnmanagedType.Bool est le type Win32 BOOL, qui est toujours de 4 octets.  UnmanagedType.U1 doit être utilisé pour C\+\+`bool` ou d'autres types de 1 octet.  Pour plus d’informations, consultez [Default Marshaling for Boolean Types](http://msdn.microsoft.com/fr-fr/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, appliquez <xref:System.Runtime.InteropServices.MarshalAsAttribute> au paramètre <xref:System.Boolean> ou à la valeur de retour.  Affectez le <xref:System.Runtime.InteropServices.UnmanagedType> approprié à la valeur de l'attribut.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Même si le comportement de marshaling par défaut est approprié, le code est géré plus facilement lorsque le comportement est spécifié explicitement.  
  
## Exemple  
 L'exemple suivant présente deux méthodes d'appel de code non managé marquées avec les attributs <xref:System.Runtime.InteropServices.MarshalAsAttribute> appropriés.  
  
 [!code-cs[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## Règles connexes  
 [CA1901 : Les déclarations P\/Invoke doivent être portables](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [CA2101 : Spécifiez le marshaling pour les arguments de chaîne P\/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [Default Marshaling for Boolean Types](http://msdn.microsoft.com/fr-fr/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)