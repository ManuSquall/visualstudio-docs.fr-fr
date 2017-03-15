---
title: "Affichage des types de donn&#233;es personnalis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.data.elements"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "autoexp.dat (fichier)"
  - "types de données personnalisés"
  - "types de données (C#), personnalisé"
  - "débogueur, étendre les types de données"
  - "code managé, types de données personnalisés"
  - "mcee_cs.dat (fichier)"
  - "mcee_mc.dat (fichier)"
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Affichage des types de donn&#233;es personnalis&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez personnaliser la façon dont Visual Studio affiche les types de données dans les fenêtres de variables du débogueur.  
  
## Attributs  
 En C\# et Visual Basic, il est possible d'ajouter des expansions aux données personnalisées à l'aide de <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> et <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 Dans le code [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], Visual Basic ne prend pas en charge l'attribut DebuggerBrowsable.  Cette limitation a été supprimée dans les versions récentes de .NET Framework.  
  
## Visualiseurs  
 Vous pouvez écrire un visualiseur pour afficher les types de données managées.  Pour plus d'informations, consultez [Comment : écrire un visualiseur](../debugger/how-to-write-a-visualizer.md).  
  
## Code natif  
 En code natif, vous pouvez ajouter des expansions de type de données personnalisées au fichier autoexp.dat, situé dans le répertoire Programmes\\Microsoft Visual Studio 11.0\\Common7\\Packages\\Debugger.  Ce fichier contient des instructions sur la façon d'écrire les règles `autoexp`.  
  
> [!CAUTION]
>  La structure de ce fichier et la syntaxe des règles autoexp peuvent varier d'une version à l'autre de Visual Studio.  
  
 Les vues de type natives peuvent également être personnalisées en écrivant un complément Évaluateur d'expression.  Pour plus d'informations, consultez [EEAddIn Sample: Debugging Expression Evaluator Add\-In](http://msdn.microsoft.com/fr-fr/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## Voir aussi  
 [Utilisation de l'attribut DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)   
 [Enhancing Debugging with the Debugger Display Attributes](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)