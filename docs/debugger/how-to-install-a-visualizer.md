---
title: 'Comment : Installer un Visualisateur Microsoft Docs'
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
ms.openlocfilehash: 499d644cc8374b070cedaf058b0e4dc17d155bdc
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880258"
---
# <a name="how-to-install-a-visualizer"></a>Comment : installer un visualiseur
Après avoir créé un visualiseur, vous devez l'installer de sorte qu'il soit disponible dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. L'installation d'un visualiseur est un processus simple.

> [!NOTE]
> Dans les applications UWP, seuls les visualisateurs standard de texte, HTML, XML et JSON sont pris en charge. Les visualiseurs personnalisés (créés par l'utilisateur) ne sont pas pris en charge.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>Installer un visualiseur pour Visual Studio 2019
  
1. Localisez le DLL qui contient le visualiseur que vous avez construit.

   Typiquement, il est préférable si à la fois le DLL debugger-côté et le DLL debuggee-côté spécifier **n’importe quel processeur** comme la plate-forme cible. Le DLL debugger-côté doit être soit **n’importe quel processeur** ou **32-bit**. La plate-forme cible pour le DLL debuggee-côté devrait correspondre au processus de débagé.

2. Copiez le [DLL de Côté Debugger](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (et tous les DLL dont il dépend) à l’un ou l’autre des endroits suivants :

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. Copiez le [DLL de Debuggee Side](create-custom-visualizers-of-data.md#to-create-the-debuggee-side) à l’un ou l’autre des endroits suivants :

    - *Cadre VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Framework*

    - `My Documents\`*Cadre VisualStudioVersion* `\Visualizers\` *Framework*

    où *le Cadre* est soit :
    - `net2.0`pour les débagés `.NET Framework` en cours d’exécution de l’heure d’exécution.
    - `netstandard2.0`pour les débogés à l’aide d’un runtime qui prend en charge `netstandard 2.0` (`.NET Framework v4.6.1+` ou `.NET Core 2.0+`).
    - `netcoreapp`pour les débagés `.NET Core` en cours d’exécution de l’heure d’exécution. (soutiens `.NET Core 2.0+`)

4. Redémarrez la session de débogage.

> [!NOTE]
> La procédure est différente dans Visual Studio 2017 et plus. Voir la [version précédente](how-to-install-a-visualizer.md?view=vs-2017) de cet article.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>Installer un visualiseur pour Visual Studio 2017 et plus

> [!IMPORTANT]
> Seuls les visualisateurs cadre .NET sont pris en charge dans Visual Studio 2017 et plus.

1. Recherchez la DLL qui contient le visualiseur que vous avez créé.

2. Copiez la DLL dans l'un ou l'autre des emplacements suivants :

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Redémarrez la session de débogage.

> [!NOTE]
> Si vous souhaitez utiliser un visualiseur géré pour un débogage distant, copiez la DLL vers le même chemin d'accès sur l'ordinateur distant.
::: moniker-end

## <a name="see-also"></a>Voir aussi
- [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)
- [Comment : écrire un visualiseur](create-custom-visualizers-of-data.md)
