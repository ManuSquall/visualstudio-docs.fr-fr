---
title: Créer des vues personnalisées d’objets | Microsoft Docs
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 733f3ec7573287e934f8a5f0167db89c0683759a
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59537476"
---
# <a name="create-custom-views-of-objects-c-visual-basic-c"></a>Créer des vues personnalisées d’objets (C#, Visual Basic, C++)
Vous pouvez personnaliser la façon dont Visual Studio affiche les types de données dans les fenêtres de variables du débogueur.

## <a name="native-code"></a>Code natif

Pour C++ code, vous pouvez ajouter des expansions de type de données personnalisées à l’aide de l’infrastructure Natvis, comme décrit dans [créer des vues personnalisées de C++ objets dans le débogueur](/visualstudio/debugger/create-custom-views-of-native-objects). Pour C++/code de l’interface CLI, vous pouvez également utiliser les attributs, décrits ici dans cet article.

## <a name="attributes"></a>Attributs

Dans C#, Visual Basic, et C++ (C++code /CLI uniquement), vous pouvez ajouter des expansions aux données personnalisées à l’aide <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute>, et <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

Dans le code [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], Visual Basic ne prend pas en charge l'attribut DebuggerBrowsable. Cette limitation a été supprimée dans les versions récentes de .NET Framework.

## <a name="visualizers"></a>Visualiseurs

Vous pouvez écrire un visualiseur pour afficher les types de données managées. Pour plus d'informations, voir [Procédure : Écrire un visualiseur](/visualstudio/debugger/create-custom-visualizers-of-data).

## <a name="see-also"></a>Voir aussi

- [Demander au débogueur les éléments à afficher à l’aide de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Demander au débogueur le type à afficher à l’aide de l’attribut DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)
- [Amélioration du débogage avec les attributs d’affichage de débogueur](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)