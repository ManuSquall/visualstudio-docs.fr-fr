---
title: "CA2006&#160;: Utilisez SafeHandle pour encapsuler les ressources natives | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2006"
  - "UseSafeHandleToEncapsulateNativeResources"
helpviewer_keywords: 
  - "UseSafeHandleToEncapsulateNativeResources"
  - "CA2006"
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2006&#160;: Utilisez SafeHandle pour encapsuler les ressources natives
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseSafeHandleToEncapsulateNativeResources|  
|CheckId|CA2006|  
|Catégorie|Microsoft.Reliability|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Le code managé utilise <xref:System.IntPtr> pour accéder aux ressources natives.  
  
## Description de la règle  
 L'utilisation de `IntPtr` dans du code managé peut être le signe d'un problème potentiel de sécurité et de fiabilité.  Toute utilisation de `IntPtr` doit être passée en revue pour déterminer s'il est nécessaire de recourir à un <xref:System.Runtime.InteropServices.SafeHandle> ou une technologie similaire à la place.  Des problèmes surviennent si `IntPtr` désigne une ressource native, par exemple la mémoire, un handle de fichier ou un socket, considérée comme appartenant au code managé.  Si le code managé est propriétaire de la ressource, il doit également libérer les ressources natives associées, parce que dans le cas contraire cela peut provoquer une fuite de ressource.  
  
 Dans ces scénarios, des problèmes de sécurité et de fiabilité se présentent également si l'accès multithread est accordé au `IntPtr`, tout comme la possibilité de libérer la ressource représentée par `IntPtr`.  Ces problèmes impliquent le recyclage de la valeur `IntPtr` sur la version finale des ressources tandis que l'utilisation simultanée de la ressource s'effectue dans un autre thread.  Cela peut provoquer des conditions de concurrence dans lesquelles un thread peut lire ou écrire des données associées à la mauvaise ressource.  Par exemple, si votre type stocke un handle de système d'exploitation comme `IntPtr` et autorise les utilisateurs à appeler à la fois la méthode **Close** et toute autre méthode utilisant ce handle en même temps \(avec un degré de synchronisation\), votre code est confronté un problème du recyclage du handle  
  
 Ce problème de recyclage des handles provoque des données endommagées et, fréquemment, une faille de sécurité.  `SafeHandle` et ses classes de mêmes parents <xref:System.Runtime.InteropServices.CriticalHandle> fournissent un mécanisme pour l'encapsulation d'un handle natif à une ressource afin que de tels problèmes de threading puissent être évités.  En outre, vous pouvez utiliser `SafeHandle` et sa classe sœur `CriticalHandle` pour d'autres problèmes de thread, notamment la nécessité de contrôler avec soin la durée de vie des objets managés contenant une copie du handle natif par rapport aux appels aux méthodes natives.  Dans cette situation, vous pouvez souvent supprimer des appels à `GC.KeepAlive`.  La surcharge de performance subie lorsque vous utilisez `SafeHandle` et, à un degré moindre, `CriticalHandle`, peut être minimisée avec une conception rigoureuse.  
  
## Comment corriger les violations  
 Convertissez l'utilisation de `IntPtr` en `SafeHandle` pour gérer sans risque l'accès aux ressources natives.  Consultez la rubrique de référence <xref:System.Runtime.InteropServices.SafeHandle> pour des exemples.  
  
## Quand supprimer les avertissements  
 Vous ne devez pas supprimer cet avertissement.  
  
## Voir aussi  
 <xref:System.IDisposable>