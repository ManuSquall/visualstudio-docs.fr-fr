---
title: "Avertissements li&#233;s &#224; l’interop&#233;rabilit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.Interoperabilityrules"
helpviewer_keywords: 
  - "avertissements liés à l’analyse du code managé, avertissements liés à l’interopérabilité"
  - "avertissements liés à l’interopérabilité"
  - "avertissements, interopérabilité"
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# Avertissements li&#233;s &#224; l’interop&#233;rabilit&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les avertissements relatifs à l'interopérabilité prennent en charge l'interaction avec les clients COM.  
  
## Dans cette section  
  
|Règle|Description|  
|-----------|-----------------|  
|[CA1400 : Des points d'entrée P\/Invoke doivent exister](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)|Une méthode publique ou protégée est marquée avec l'attribut System.Runtime.InteropServices.DllImportAttribute.  La bibliothèque non managée n'a pas pu être localisée, ou la méthode n'a pu être mise en correspondance avec aucune fonction de la bibliothèque.|  
|[CA1401 : Les P\/Invoke ne doivent pas être visibles](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)|Une méthode publique ou protégée dans un type public a l'attribut System.Runtime.InteropServices.DllImportAttribute \(également implémenté par le mot clé Declare en Visual Basic\).  De telles méthodes ne doivent pas être exposées.|  
|[CA1402 : Éviter les surcharges dans les interfaces COM visibles](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Lorsque les méthodes surchargées sont exposées aux clients COM, seule la première surcharge de méthode conserve son nom.  Les surcharges suivantes sont renommées de manière unique par l'ajout d'un trait de soulignement \(\_\) au nom et d'un entier qui correspond à l'ordre de déclaration de la surcharge.|  
|[CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Un type valeur visible par COM est marqué avec l'attribut System.Runtime.InteropServices.StructLayoutAttribute qui a la valeur LayoutKind.Auto.  La disposition de ces types peut varier suivant les versions du [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], ce qui bloque les clients COM qui attendent une disposition spécifique.|  
|[CA1404 : Appeler GetLastError immédiatement après P\/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|La méthode Marshal.GetLastWin32Error ou la fonction [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] GetLastError équivalente est appelée, et l'appel immédiatement avant ne constitue pas une méthode d'appel de code non managé.|  
|[CA1405 : Les types de base type visibles par COM doivent être visibles par COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Un type visible par COM dérive d'un type qui n'est pas visible par COM.|  
|[CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Les clients COM Visual Basic 6 ne peuvent pas accéder aux entiers de 64 bits.|  
|[CA1407 : Éviter les membres statiques dans les types visibles par COM](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)|COM ne prend pas en charge les méthodes statiques.|  
|[CA1408 : Ne pas utiliser le paramètre AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Les types qui utilisent une interface double permettent aux clients de se lier à une disposition d'interface spécifique.  Les modifications apportées à une version future de la disposition du type ou des types de base bloquent les clients COM qui se lient à l'interface.  Par défaut, si l'attribut ClassInterfaceAttribute n'est pas spécifié, une interface de répartition uniquement est utilisée.|  
|[CA1409 : Les types visibles par COM doivent pouvoir être créés](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Un type référence marqué spécifiquement comme visible par des clients COM contient un constructeur public paramétré, mais ne contient pas de constructeur public par défaut \(sans paramètre\).  Les clients COM ne peuvent pas créer de type sans constructeur public par défaut.|  
|[CA1410 : Les méthodes d'inscription COM doivent être mises en correspondance](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Un type déclare une méthode marquée avec l'attribut <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> mais ne déclare pas une méthode marquée avec l'attribut <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>, ou vice versa.|  
|[CA1411 : Les méthodes d'inscription COM ne doivent pas être visibles](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Une méthode marquée avec l'attribut System.Runtime.InteropServices.ComRegisterFunctionAttribute ou System.Runtime.InteropServices.ComUnregisterFunctionAttribute est visible de l'extérieur.|  
|[CA1412 : Marquer les interfaces ComSource comme IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Un type est marqué avec l'attribut System.Runtime.InteropServices.ComSourceInterfacesAttribute et au moins une des interfaces spécifiées n'est pas marquée avec l'attribut System.Runtime.InteropServices.InterfaceTypeAttribute ayant la valeur ComInterfaceType.InterfaceIsIDispatch.|  
|[CA1413 : Éviter les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Les champs d'instance non publics des types valeur visibles par COM sont visibles par les clients COM.  Passez en revue le contenu des champs pour voir les informations qui ne doivent pas être exposées, sinon vous aurez une conception imprévue ou des conséquences sur la sécurité.|  
|[CA1414 : Marquer les arguments P\/Invoke booléens comme MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Le type de données booléen contient plusieurs représentations dans le code non managé.|  
|[CA1415 : Déclarer correctement les méthodes P\/Invoke](../code-quality/ca1415-declare-p-invokes-correctly.md)|Cette règle recherche des déclarations de méthode d'appel de code non managé qui ciblent des fonctions [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] présentant un pointeur vers un paramètre de structure OVERLAPPED, et le paramètre managé correspondant n'est pas un pointeur vers une structure <xref:System.Threading.NativeOverlapped?displayProperty=fullName> .|