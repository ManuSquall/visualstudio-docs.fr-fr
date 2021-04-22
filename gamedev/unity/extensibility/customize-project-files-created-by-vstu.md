---
title: Personnaliser les fichiers projet créés par VSTU | Microsoft Docs
description: Découvrez comment personnaliser les fichiers projet créés par Outils Visual Studio pour Unity (VSTU). Passez en revue un exemple de code C#.
ms.custom: ''
ms.date: 04/19/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 60b8cc1d-cacc-404d-b768-77e81bc354f8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: a4a5973863877db2d071f9be8d4689928b21a689
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879315"
---
# <a name="customize-project-files-created-by-vstu"></a>Personnaliser les fichiers projet créés par VSTU
Unity fournit des rappels pendant la génération du fichier projet. Implémentez `OnGeneratedSlnSolution` `OnGeneratedCSProject` les méthodes et à l’aide d’un [`AssetPostprocessor`](https://docs.unity3d.com/ScriptReference/AssetPostprocessor.html) pour modifier le fichier projet ou solution chaque fois qu’il est régénéré.

## <a name="demonstrates"></a>Illustre le
Comment personnaliser les fichiers projet Visual Studio générés par Visual Studio Tools pour Unity.

## <a name="example"></a>Exemple

```csharp
using System;
using UnityEditor;
using UnityEngine;

public class ProjectFilePostprocessor : AssetPostprocessor
{
  public static string OnGeneratedSlnSolution(string path, string content)
  {
    // TODO: process solution content
    return content;
  }

  public static string OnGeneratedCSProject(string path, string content)
  {
    // TODO: process project content
    return content;
  }
}
```
