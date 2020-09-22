---
title: 'Comment : installer un visualiseur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726cea8b2e81c53b5f3fff963357946f26b199f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839549"
---
# <a name="how-to-install-a-visualizer"></a>Comment : installer un visualiseur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Après avoir créé un visualiseur, vous devez l'installer de sorte qu'il soit disponible dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. L'installation d'un visualiseur est un processus simple.  
  
> [!NOTE]
> Dans les applications du Windows **Store** , seuls les visualiseurs de texte, html, XML et JSON standard sont pris en charge. Les visualiseurs personnalisés (créés par l'utilisateur) ne sont pas pris en charge.  
  
### <a name="to-install-a-visualizer"></a>Pour installer un visualiseur  
  
1. Recherchez la DLL qui contient le visualiseur que vous avez créé.  
  
2. Copiez la DLL dans l'un ou l'autre des emplacements suivants :  
  
    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    - `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3. Si vous souhaitez utiliser un visualiseur géré pour un débogage distant, copiez la DLL vers le même chemin d'accès sur l'ordinateur distant.  
  
4. Redémarrez la session de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)   
 [Comment : écrire un visualiseur](../debugger/how-to-write-a-visualizer.md)
