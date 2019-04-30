---
title: 'Procédure : Utiliser un visualiseur | Microsoft Docs'
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446433"
---
# <a name="how-to-use-a-visualizer"></a>Procédure : Utiliser un visualiseur
Vous pouvez utiliser un visualiseur afin d'afficher le contenu d'une variable ou d'un objet de façon explicite pour le type de données. Vous pouvez utiliser des visualiseurs depuis **DataTips**, un **espion** fenêtre, le **automatique** fenêtre, ou le **variables locales** fenêtre.  
  
 Les visualiseurs ne sont pas pris en charge sur le Compact Framework.  
  
> [!NOTE]
> Dans **Store** applications, seul le texte standard, les visualiseurs HTML, XML et JSON sont pris en charge. Les visualiseurs personnalisés (créés par l'utilisateur) ne sont pas pris en charge.  
  
### <a name="to-open-a-visualizer"></a>Pour ouvrir un visualiseur  
  
1. Cliquez sur l’icône de loupe qui apparaît en regard d’un nom de variable dans **DataTips**, un **espion** fenêtre, ou dans le **automatique**, **variables locales**, ou **Espion express** fenêtre.  
  
     Une liste de visualiseurs s'affiche.  
  
2. Cliquez sur le visualiseur à utiliser.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Pour utiliser un visualiseur pour le code managé pendant le débogage distant  
  
- Copiez la DLL de visualiseur vers l'ordinateur distant avant de démarrer la session de débogage.  
  
     Le chemin d’accès à la DLL doit être le même sur les ordinateurs local et distant. Ce chemin d'accès peut correspondre à l'un ou l'autre des emplacements suivants :  
  
     *Le chemin d’accès de Visual Studio Installer* `\Common7\Packages\Debugger\Visualizers`  
  
     - ou -  
  
     `My Documents\Visual Studio 2010\Visualizers` *Version de Visual Studio* `\Visualizers`  
  
## <a name="see-also"></a>Voir aussi  
 [Créer des visualiseurs personnalisés](../debugger/create-custom-visualizers-of-data.md)   
 [Guide pratique pour installer un visualiseur](../debugger/how-to-install-a-visualizer.md)   
 [Guide pratique pour écrire un visualiseur](../debugger/how-to-write-a-visualizer.md)   
 [Afficher les valeurs des données dans les conseils de données](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)