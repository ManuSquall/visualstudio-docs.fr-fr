---
title: 'Procédure : Installer un visualiseur | Microsoft Docs'
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
ms.openlocfilehash: d5b27d52c1f390e6c9f60ef10a91d9a93f903f5c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104477"
---
# <a name="how-to-install-a-visualizer"></a>Procédure : Installer un visualiseur
Après avoir créé un visualiseur, vous devez l'installer de sorte qu'il soit disponible dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. L'installation d'un visualiseur est un processus simple.

> [!NOTE]
>  Dans les applications UWP, seul le texte standard, les visualiseurs HTML, XML et JSON sont pris en charge. Les visualiseurs personnalisés (créés par l'utilisateur) ne sont pas pris en charge.

### <a name="to-install-a-visualizer"></a>Pour installer un visualiseur

1. Recherchez la DLL qui contient le visualiseur que vous avez créé.

2. Copiez la DLL dans l'un ou l'autre des emplacements suivants :

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. Si vous souhaitez utiliser un visualiseur géré pour un débogage distant, copiez la DLL vers le même chemin d'accès sur l'ordinateur distant.

4. Redémarrez la session de débogage.

## <a name="see-also"></a>Voir aussi
- [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)
- [Guide pratique pour écrire un visualiseur](/visualstudio/debugger/create-custom-visualizers-of-data)