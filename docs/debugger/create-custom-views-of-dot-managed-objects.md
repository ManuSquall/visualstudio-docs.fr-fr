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
ms.openlocfilehash: 36e875bc8101bc8a1b0eb1bec6671c76e3b0c9b2
ms.sourcegitcommit: 8a3545329a58e446672181cfed2083f850e1ad14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71814297"
---
# <a name="create-custom-views-of-objects-c-visual-basic-f-ccli"></a>Créer des vues personnalisées d'C#objets (, F#Visual Basic C++,,/CLI)
Vous pouvez personnaliser la façon dont Visual Studio affiche les types de données dans les fenêtres de variables du débogueur.

## <a name="attributes"></a>Attributs

Dans C#, Visual Basic, F#et C++ (C++code/CLI uniquement), vous pouvez ajouter des expansions pour les données personnalisées à l’aide de <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> et <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

Dans .NET Framework code 2,0, Visual Basic ne prend pas en charge l’attribut DebuggerBrowsable. Cette limitation a été supprimée dans les versions récentes de .NET Framework.

## <a name="visualizers"></a>Visualiseurs

Vous pouvez écrire un visualiseur pour afficher les types de données managées. Pour plus d'informations, voir [Procédure : Écrire un visualiseur](/visualstudio/debugger/create-custom-visualizers-of-data).

> [!NOTE]
> Pour C++ le code, vous pouvez ajouter des expansions de type de données personnalisées à l’aide de l’infrastructure Natvis, comme décrit dans [créer des vues personnalisées d' C++ objets dans le débogueur](/visualstudio/debugger/create-custom-views-of-native-objects).

## <a name="see-also"></a>Voir aussi

- [Indiquer au débogueur ce qui doit être affiché à l’aide de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Indiquer au débogueur le type à afficher à l’aide de l’attribut DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)
- [Amélioration du débogage avec les attributs d’affichage de débogueur](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)