---
title: "System DLL &lt;name&gt; could not be loaded. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_TERRSYSDLLNOTLOADED"
  - "vs.message.0x800A0085"
ms.assetid: d4ccb3b1-fbc3-4395-a9b1-be50a4d7bf44
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# System DLL &lt;name&gt; could not be loaded.
Un fichier .DLL fourni par le système d'exploitation, tel que DDEML.DLL, VERSION.DLL ou WINSPOOL.DRV est introuvable.  Cette erreur se produit généralement dans l'un des cas suivants : le fichier ne se trouve pas dans le chemin approprié, la DLL est endommagée ou a été supprimée ou la mémoire est insuffisante.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que la DLL se trouve dans le chemin du répertoire système de Windows.  
  
     \- ou \-  
  
     Rechargez la DLL.  
  
     \- ou \-  
  
     Essayez de libérer de la mémoire en fermant d'autres applications.