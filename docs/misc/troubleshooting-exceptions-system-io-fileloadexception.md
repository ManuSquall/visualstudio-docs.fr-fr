---
title: "D&#233;pannage des exceptions&#160;: System.IO.FileLoadException | Microsoft Docs"
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
  - "FileLoadException (classe)"
ms.assetid: 6b4519e3-4d29-4031-8aec-c2735b4ee16d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.IO.FileLoadException
Une exception <xref:System.IO.FileLoadException> est levée lorsqu'un assembly managé est trouvé, mais qu'il ne peut pas être chargé.  
  
## Conseils associés  
 **Assurez\-vous que le fichier est un assembly .NET Framework valide.**  
 Cette exception est levée si le fichier n'est pas un assembly .NET Framework valide. Pour plus d'informations, consultez <xref:System.Reflection.Assembly>.  
  
 **Vérifiez qu'un assembly ou qu'un module n'a pas été chargé à deux reprises avec deux preuves différentes.**  
 La preuve est le jeu d'informations qui alimente les décisions de stratégie de sécurité, telles que les autorisations qui peuvent être accordées au code. Pour plus d'informations, voir <xref:System.EnterpriseServices.Internal.Publish.GacRemove%2A> et <xref:System.Reflection.Assembly.Evidence%2A>.  
  
 **Si vous utilisez la méthode RegisterAssembly ou UnregisterAssembly, vérifiez que le nom de l'assembly ne dépasse pas MAX\_PATH caractères.**  
 La longueur du nom de l'assembly ne peut pas dépasser MAX\_PATH. Pour plus d’informations, consultez <xref:System.EnterpriseServices.Internal.IComSoapPublisher.RegisterAssembly%2A> et <xref:System.EnterpriseServices.Internal.IComSoapPublisher.UnRegisterAssembly%2A>.  
  
 **Lors du chargement d'un assembly satellite, assurez\-vous que le CultureInfo spécifié correspond au CultureInfo du fichier.**  
 Les assemblys satellites contiennent des ressources localisées, contrairement aux autres assemblys d'application principaux qui contiennent du code exécutable et des ressources non localisables pour une culture unique utilisée comme culture neutre ou par défaut. Pour plus d'informations, consultez <xref:System.Reflection.Assembly.GetSatelliteAssembly%2A>.  
  
## Voir aussi  
 <xref:System.IO.FileLoadException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)