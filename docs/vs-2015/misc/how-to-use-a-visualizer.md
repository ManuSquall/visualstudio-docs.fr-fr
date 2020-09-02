---
title: 'Comment : utiliser un visualiseur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
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
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f981b76d471658fe82e874901ad784a17841891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778376"
---
# <a name="how-to-use-a-visualizer"></a>Comment : utiliser un visualiseur
Vous pouvez utiliser un visualiseur afin d'afficher le contenu d'une variable ou d'un objet de façon explicite pour le type de données. Vous pouvez utiliser des visualiseurs de **DataTips**, une fenêtre **Espion** , la fenêtre **automatique** ou la fenêtre **variables locales** .  
  
 Les visualiseurs ne sont pas pris en charge sur le Compact Framework.  
  
> [!NOTE]
> Dans les applications du Windows **Store** , seuls les visualiseurs de texte, html, XML et JSON standard sont pris en charge. Les visualiseurs personnalisés (créés par l'utilisateur) ne sont pas pris en charge.  
  
### <a name="to-open-a-visualizer"></a>Pour ouvrir un visualiseur  
  
1. Cliquez sur l’icône de loupe qui s’affiche en regard d’un nom de variable dans les **DataTips**, une fenêtre **Espion** ou dans la fenêtre **automatique**, **variables locales**ou **Espion express** .  
  
     Une liste de visualiseurs s'affiche.  
  
2. Cliquez sur le visualiseur à utiliser.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Pour utiliser un visualiseur pour le code managé pendant le débogage distant  
  
- Copiez la DLL de visualiseur vers l'ordinateur distant avant de démarrer la session de débogage.  
  
     Le chemin d’accès à la DLL doit être le même sur les ordinateurs local et distant. Ce chemin d'accès peut correspondre à l'un ou l'autre des emplacements suivants :  
  
     *Chemin d'accès de l'installation de Visual Studio* `\Common7\Packages\Debugger\Visualizers`  
  
     - ou -  
  
     `My Documents\Visual Studio 2010\Visualizers`*Version de Visual Studio*`\Visualizers`  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)   
 [Comment : installer un visualiseur](../debugger/how-to-install-a-visualizer.md)   
 [Comment : écrire un visualiseur](../debugger/how-to-write-a-visualizer.md)   
 [Afficher les valeurs de données dans les info-bulles](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)