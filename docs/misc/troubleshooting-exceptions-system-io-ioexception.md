---
title: "D&#233;pannage des exceptions&#160;: System.IO.IOException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IOException (classe)"
ms.assetid: 87812daa-0784-43dc-b3dc-6652a960c362
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.IO.IOException
Une <xref:System.IO.IOException> est levée en cas d'erreur d'E\/S, telle qu'un échec de lecture ou d'écriture dans un fichier.  
  
## Conseils associés  
 **Assurez\-vous que le fichier et le répertoire existent.**  
 Vérifiez que le répertoire duquel vous tentez de lire\/dans lequel vous tentez d'écrire existe. Vérifiez que le fichier duquel vous tentez de lire existe.  
  
### Notes  
 <xref:System.IO.IOException> est la classe de base des exceptions levées lors de l'accès aux informations à l'aide de flux, de fichiers et de répertoires.  
  
 La bibliothèque des classes de base comprend les types suivants, chacun d'eux étant une classe dérivée de : <xref:System.IO.IOException>:  
  
-   <xref:System.IO.DirectoryNotFoundException>  
  
-   <xref:System.IO.EndOfStreamException>  
  
-   <xref:System.IO.FileNotFoundException>  
  
-   <xref:System.IO.FileLoadException>  
  
-   <xref:System.IO.PathTooLongException>  
  
## Voir aussi  
 <xref:System.IO.IOException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [NOTINBUILD Procédure : création d’applications console CLR](http://msdn.microsoft.com/fr-fr/b8af4197-e65f-4b17-b18e-b9e92965d026)