---
title: Créer des vues personnalisées d’objets gérés | Microsoft Docs
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
ms.openlocfilehash: 3d75193368188efc660391d1e80c562ed881324b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578040"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Créer des vues personnalisées d’objetsC#gérés (, F#Visual Basic C++,,/CLI)
Vous pouvez personnaliser la façon dont Visual Studio affiche les types de données dans les fenêtres de variables du débogueur.

## <a name="attributes"></a>Attributs

Dans C#, Visual Basic, F#et C++ (C++code/CLI uniquement), vous pouvez ajouter des expansions pour les données personnalisées à l’aide de <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> et <xref:System.Diagnostics.DebuggerBrowsableAttribute>.

Dans .NET Framework code 2,0, Visual Basic ne prend pas en charge l’attribut DebuggerBrowsable. Cette limitation est supprimée dans les versions plus récentes de .NET.

## <a name="visualizers"></a>Visualiseurs

Vous pouvez écrire un visualiseur pour afficher les types de données managées. Pour plus d’informations, consultez [Comment : écrire un visualiseur](/visualstudio/debugger/create-custom-visualizers-of-data).

> [!NOTE]
> Pour C++ le code, vous pouvez ajouter des expansions de type de données personnalisées à l’aide de l’infrastructure Natvis, comme décrit dans [créer des vues personnalisées d' C++ objets dans le débogueur](/visualstudio/debugger/create-custom-views-of-native-objects).

## <a name="see-also"></a>Voir aussi

- [Indiquer au débogueur ce qui doit être affiché à l’aide de l’attribut DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Indiquer au débogueur le type à afficher à l’aide de l’attribut DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Espion et Espion express, fenêtres](../debugger/watch-and-quickwatch-windows.md)
- [Amélioration du débogage avec les attributs d’affichage de débogueur](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
