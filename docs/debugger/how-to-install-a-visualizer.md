---
title: Installer un visualiseur | Microsoft Docs
description: Découvrez comment installer un visualiseur afin qu’il soit disponible pour le débogage à l’aide de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 611347acfe48e561653d644097d56d029b6a4fa6
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298255"
---
# <a name="how-to-install-a-visualizer"></a>Comment : installer un visualiseur
Après avoir créé un visualiseur, vous devez l'installer de sorte qu'il soit disponible dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. L'installation d'un visualiseur est un processus simple.

> [!NOTE]
> Dans les applications UWP, seuls les visualiseurs de texte, HTML, XML et JSON standard sont pris en charge. Les visualiseurs personnalisés (créés par l'utilisateur) ne sont pas pris en charge.

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>pour installer un visualiseur pour Visual Studio 2019

1. Recherchez la DLL qui contient le visualiseur que vous avez généré.

   En règle générale, il est préférable que la DLL côté débogueur et la DLL côté programme débogué spécifient **Any CPU** comme plateforme cible. La DLL côté débogueur doit être **Any CPU** ou **32 bits**. La plateforme cible de la DLL côté programme débogué doit correspondre au processus du programme débogué.

   >[!NOTE]
   > le visualiseur côté débogueur est chargé dans le processus de Visual Studio. il doit donc s’agir d’une .NET Framework DLL. le côté programme débogué peut être .NET Framework ou .NET Standard selon le processus qui est débogué dans Visual Studio.

2. Copiez la dll [côté débogueur](create-custom-visualizers-of-data.md#to-create-the-debugger-side) (et toutes les dll dont elle dépend) à l’un des emplacements suivants :

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Copiez la dll du [côté débogué](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) dans l’un des emplacements suivants :

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\` *Infrastructure*

    - `My Documents\`*VisualStudioVersion* `\Visualizers\` *Infrastructure*

    où *Framework* est l’un des éléments suivants :
    - `net2.0` pour les débogueurs exécutant le `.NET Framework` Runtime.
    - `netstandard2.0` pour les débogueurs utilisant un Runtime qui prend en charge `netstandard 2.0` ( `.NET Framework v4.6.1+` ou `.NET Core 2.0+` ).
    - `netcoreapp` pour les débogueurs exécutant le `.NET Core` Runtime. (prend en charge `.NET Core 2.0+` )

   Une DLL côté programme débogué est nécessaire si vous souhaitez créer un visualiseur autonome. Cette DLL contient le code de l’objet de données, qui peut implémenter des méthodes de <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> .

   Si vous multiciblez le code côté débogué, la DLL côté programme débogué doit être placée dans le dossier pour les TFM avec un minimum pris en charge.

4. Redémarrez la session de débogage.

> [!NOTE]
> la procédure est différente dans Visual Studio 2017 et les versions antérieures. Consultez la [version précédente](how-to-install-a-visualizer.md?view=vs-2017&preserve-view=true) de cet article.
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>pour installer un visualiseur pour Visual Studio 2017 et versions antérieures

> [!IMPORTANT]
> seuls les visualiseurs .NET Framework sont pris en charge dans Visual Studio 2017 et les versions antérieures.

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
