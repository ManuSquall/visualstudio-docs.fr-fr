---
title: "Comment : installer un visualiseur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 71b1d5cda498f42383e430a505296b2c4e074b73
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-a-visualizer"></a>Comment : installer un visualiseur
Après avoir créé un visualiseur, vous devez l'installer de sorte qu'il soit disponible dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. L'installation d'un visualiseur est un processus simple.  
  
> [!NOTE]
>  Dans **magasin** applications, seul le texte standard, les visualiseurs HTML, XML et JSON sont pris en charge. Les visualiseurs personnalisés (créés par l'utilisateur) ne sont pas pris en charge.  
  
### <a name="to-install-a-visualizer"></a>Pour installer un visualiseur  
  
1.  Recherchez la DLL qui contient le visualiseur que vous avez créé.  
  
2.  Copiez la DLL dans l'un ou l'autre des emplacements suivants :  
  
    -   *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3.  Si vous souhaitez utiliser un visualiseur géré pour un débogage distant, copiez la DLL vers le même chemin d’accès sur l’ordinateur distant.  
  
4.  Redémarrez la session de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)   
 [Guide pratique pour écrire un visualiseur](../debugger/how-to-write-a-visualizer.md)