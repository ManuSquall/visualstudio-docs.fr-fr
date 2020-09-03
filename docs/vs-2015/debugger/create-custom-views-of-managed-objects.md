---
title: Créer des vues personnalisées d’objets gérés | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb5b56404c7ddc99b7999b47cf3c2a899f915efd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72578054"
---
# <a name="create-custom-views-of-managed-objects"></a>Créer des vues personnalisées d’objets gérés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez personnaliser la façon dont Visual Studio affiche les types de données dans les fenêtres de variables du débogueur.  
  
## <a name="attributes"></a>Attributs  
 En C# et Visual Basic, il est possible d'ajouter des expansions aux données personnalisées à l'aide de <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> et <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 Dans le code [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], Visual Basic ne prend pas en charge l'attribut DebuggerBrowsable. Cette limitation a été supprimée dans les versions récentes de .NET Framework.  
  
## <a name="visualizers"></a>Visualiseurs  
 Vous pouvez écrire un visualiseur pour afficher les types de données managées. Pour plus d’informations, consultez [Comment : écrire un visualiseur](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Code natif  
 En code natif, vous pouvez ajouter des expansions de type de données personnalisées au fichier autoexp.dat, situé dans le répertoire Programmes\Microsoft Visual Studio 11.0\Common7\Packages\Debugger. Ce fichier contient des instructions sur la façon d'écrire les règles `autoexp`.  
  
> [!CAUTION]
> La structure de ce fichier et la syntaxe des règles autoexp peuvent varier d’une mise en production à l’autre de Visual Studio.  
  
 Les vues de type natives peuvent également être personnalisées en écrivant un complément Évaluateur d'expression. Pour plus d’informations, consultez [exemple EEAddIn : débogage du complément Évaluateur d’expression](https://msdn.microsoft.com/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de l’attribut DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Fenêtres espion et espion Express](../debugger/watch-and-quickwatch-windows.md)   
 [Amélioration du débogage avec les attributs d'affichage de débogueur](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
