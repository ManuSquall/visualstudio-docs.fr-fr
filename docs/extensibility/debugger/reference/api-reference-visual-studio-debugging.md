---
title: "R&#233;f&#233;rence des API (d&#233;bogage de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "débogage (débogage SDK), la référence de l'API"
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# R&#233;f&#233;rence des API (d&#233;bogage de Visual Studio)
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

La section de référence contient une vue d'ensemble conceptuelle de l'API, un guide qui affiche la syntaxe et le mode d'utilisation pour tous les éléments d'API, et d'un ensemble d'exemples de code.  Toutes les références sont classées par ordre alphabétique par catégorie.  
  
 Le tableau suivant affiche les valeurs d' `HRESULT` courante retournées par les méthodes.  
  
|Nom|Description|Valeur|  
|---------|-----------------|------------|  
|S\_OK|Succès.|0x00000000|  
|E\_UNEXPECTED|Défaillance inattendue.|0x8000FFFF|  
|E\_NOTIMPL|Non implémenté.|0x80004001|  
|E\_OUTOFMEMORY|Pas assez de mémoire pour terminer l'opération.|0x8007000E|  
|E\_INVALIDARG|Un ou plusieurs arguments ne sont pas valides.|0x80070057|  
|E\_NOINTERFACE|Aucun ces interface prise en charge.|0x80004002|  
|E\_POINTER|Pointeur non valide.|0x80004003|  
|E\_HANDLE|handle valide.|0x80070006|  
|E\_ABORT|opération interrompue.|0x80004004|  
|E\_FAIL|Défaillance inattendue.|0x80004005|  
|E\_ACCESSDENIED|erreur générale d'accès refusé.|0x80070005|  
  
> [!NOTE]
>  Lorsque [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] déboguer la méthode retourne `S_OK`, on suppose que tous les pointeurs de paramètre de sortie sont valides, c. autrement dit., aucune validation n'est conduite sur les pointeurs de paramètre de sortie lorsque `S_OK` est retourné.  
  
> [!NOTE]
>  Les paramètres valides ou \[out\] d' `NULL` peuvent provoquer l'IDE à l'incident.  
  
## Voir aussi  
 [Interfaces](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [« Helpers » du Kit de développement logiciel pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Extensibilité du débogueur de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)