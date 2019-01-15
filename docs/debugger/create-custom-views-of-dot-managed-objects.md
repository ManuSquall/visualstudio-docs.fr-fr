---
title: Créer des vues personnalisées d’objets gérés | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 389deb0b6504ca5c7a3716399429f176e5dc7870
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53861434"
---
# <a name="create-custom-views-of-managed-objects"></a>Créer des vues personnalisées d’objets gérés
Vous pouvez personnaliser la façon dont Visual Studio affiche les types de données dans les fenêtres de variables du débogueur.  
  
## <a name="attributes"></a>Attributs  
 En C# et Visual Basic, il est possible d'ajouter des expansions aux données personnalisées à l'aide de <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> et <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 Dans le code [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], Visual Basic ne prend pas en charge l'attribut DebuggerBrowsable. Cette limitation a été supprimée dans les versions récentes de .NET Framework.  
  
## <a name="visualizers"></a>Visualiseurs  
 Vous pouvez écrire un visualiseur pour afficher les types de données managées. Pour plus d'informations, voir [Procédure : Écrire un visualiseur](/visualstudio/debugger/create-custom-visualizers-of-data).  
  
## <a name="native-code"></a>Code natif  
 En code natif, vous pouvez ajouter des expansions de type de données personnalisées au fichier autoexp.dat, situé dans le répertoire Programmes\Microsoft Visual Studio 11.0\Common7\Packages\Debugger. Ce fichier contient des instructions sur la façon d'écrire les règles `autoexp`.  
  
> [!CAUTION]
>  La structure de ce fichier et la syntaxe des règles autoexp peuvent varier d'une version à l'autre de Visual Studio.  
  
 Les vues de type natives peuvent également être personnalisées en écrivant un complément Évaluateur d'expression. Pour plus d’informations, consultez [exemple EEAddIn : Débogage Expression complément Évaluateur](https://msdn.microsoft.com/library/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de l’attribut DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Utilisation de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)   
 [Amélioration du débogage avec les attributs d’affichage de débogueur](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)