---
title: 'Comment : installer un visualiseur | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1df72c6978f5ab34a86c74dbc1ea349db5aa4457
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491307"
---
# <a name="how-to-install-a-visualizer"></a>Comment : installer un visualiseur
Après avoir créé un visualiseur, vous devez l'installer de sorte qu'il soit disponible dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. L'installation d'un visualiseur est un processus simple.

> [!NOTE]
> Dans les applications UWP, seuls les visualiseurs de texte, HTML, XML et JSON standard sont pris en charge. Les visualiseurs personnalisés (créés par l'utilisateur) ne sont pas pris en charge.

### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Pour installer un visualiseur pour Visual Studio 2019
  
1. Recherchez la DLL qui contient le visualiseur que vous avez créé.

2. Copiez la dll [côté débogueur](create-custom-visualizers-of-data.md#to-create-the-debugger-side) dans l’un des emplacements suivants :

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Copiez la dll du [côté débogué](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) dans l’un des emplacements suivants :

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\` *Framework*

    Où *Framework* est l’un des éléments suivants :
    - `net2.0` pour les débogueurs qui exécutent le `.NET Framework` Runtime.
    - `netstandard2.0` pour les débogueurs à l’aide d’un Runtime qui prend en charge `netstandard 2.0` (`.NET Framework v4.6.1+` ou `.NET Core 2.0+`).
    - `netcoreapp` pour les débogueurs qui exécutent le `.NET Core` Runtime. (prend en charge `.NET Core 2.0+`)

4. Redémarrez la session de débogage.

### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Pour installer un visualiseur pour Visual Studio 2017 et versions antérieures

> [!IMPORTANT]
> Seuls les visualiseurs .NET Framework sont pris en charge dans Visual Studio 2017 et versions antérieures

1. Recherchez la DLL qui contient le visualiseur que vous avez créé.

2. Copiez la DLL dans l'un ou l'autre des emplacements suivants :

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Redémarrez la session de débogage.

> [!NOTE]
> Si vous souhaitez utiliser un visualiseur géré pour un débogage distant, copiez la DLL vers le même chemin d'accès sur l'ordinateur distant.

## <a name="see-also"></a>Voir aussi
- [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)
- [Guide pratique pour écrire un visualiseur](create-custom-visualizers-of-data.md)
