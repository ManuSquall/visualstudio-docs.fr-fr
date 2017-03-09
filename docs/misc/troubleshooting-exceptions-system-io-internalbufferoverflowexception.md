---
title: "D&#233;pannage des exceptions&#160;: System.IO.InternalBufferOverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "InternalBufferOverflowException (classe)"
ms.assetid: 1f58ca15-c4e4-4af9-9a3d-42d2cf919cbe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.IO.InternalBufferOverflowException
Une exception <xref:System.IO.InternalBufferOverflowException> est levée en cas de dépassement de la mémoire tampon interne.  
  
## Conseils associés  
 **Lorsque vous utilisez FileSystemWatcher, filtrez les notifications de modifications indésirables afin de les exclure.**  
 Dans un observateur de système de fichiers \(FileSystemWatcher\), lorsque le système vous notifie des modifications apportées au fichier, il stocke ces modifications dans une mémoire tampon que le composant crée et passe aux API. Si plusieurs modifications sont apportées en un court laps de temps, la mémoire tampon risque de déborder, ce qui provoque la levée d'une exception <xref:System.IO.InternalBufferOverflowException> et entraîne la perte de toutes les modifications. Pour éviter un dépassement de la mémoire tampon, utilisez les propriétés <xref:System.IO.FileSystemWatcher.NotifyFilter%2A> et <xref:System.IO.FileSystemWatcher.IncludeSubdirectories%2A> pour filtrer les notifications de modifications inutiles. Pour plus d'informations, consultez <xref:System.IO.FileSystemWatcher>.  
  
## Notes  
 Vous pouvez également augmenter la taille de la mémoire tampon interne via la propriété <xref:System.IO.FileSystemWatcher.InternalBufferSize%2A>. Toutefois, augmenter la taille de la mémoire tampon affecte les performances, il est donc préférable de la limiter au maximum.  
  
## Voir aussi  
 <xref:System.IO.InternalBufferOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)