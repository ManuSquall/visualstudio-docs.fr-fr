---
title: "D&#233;pannage des exceptions&#160;: System.IO.FileNotFoundException | Microsoft Docs"
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
  - "FileNotFoundException (classe)"
  - "System.IO.FileNotFoundException (exception)"
ms.assetid: 6e5ab395-7c81-434e-835f-0fc792b9149d
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.IO.FileNotFoundException
Une exception <xref:System.IO.FileNotFoundException> est levée lors d'une tentative d'accès à un fichier ou répertoire qui n'existe pas sur le disque.  
  
## Conseils associés  
 **Vérifiez que le fichier existe à l'emplacement spécifié.**  
 Si le fichier n'existe pas, l'exception est levée. Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A>.  
  
 **Lorsque vous utilisez des chemins d'accès relatifs, assurez\-vous que le répertoire actif est correct.**  
 Si le répertoire actif est incorrect, les chemins d'accès relatifs le seront également.  
  
## Voir aussi  
 <xref:System.IO.FileNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)