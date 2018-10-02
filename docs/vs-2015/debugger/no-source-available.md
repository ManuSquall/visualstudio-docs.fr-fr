---
title: Aucune Source disponible | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.nosource
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fd7643dd7334a220d1e5c78ef12bddf07af11f8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494924"
---
# <a name="no-source-available"></a>Aucune source disponible
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [aucune Source disponible](https://docs.microsoft.com/visualstudio/debugger/no-source-available).  
  
Votre projet ne contient pas de code source pour le code que vous essayez d'afficher. La cause habituelle sur un module qui n’a pas de code source dans le **fenêtre Pile des appels** ou **fenêtre Threads**. Vous pouvez poursuivre le débogage, mais vous ne pouvez pas utiliser la fenêtre source pour définir les points d'arrêt et accomplir d'autres actions à cet emplacement. Si vous devez définir un point d’arrêt, utilisez la **fenêtre code machine** à la place.  
  
 Dans les pages de propriétés de la solution, vous pouvez changer les répertoires dans lesquels le débogueur recherche des fichiers sources et demander au débogueur d'ignorer les fichiers sources sélectionnés. Consultez [déboguer la boîte de dialogue Pages de propriété de Source des fichiers, les propriétés communes, Solution](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Cliquez sur Parcourir pour rechercher du code source**  
 Cliquez sur ce lien pour ouvrir une boîte de dialogue où vous pouvez rechercher le code source.  
  
 **Afficher le code machine**  
 Lance le **fenêtre code machine**.  
  
 **Toujours afficher le code machine pour les fichiers sources manquants**  
 Sélectionnez cette option pour afficher le **fenêtre code machine** automatiquement quand aucune source n’est disponible. Ce paramètre peut également être modifié dans le **Options** boîte de dialogue, **débogage** catégorie, **général** page, en activant ou désactivant **afficher le code machine si source n’est pas disponible**.  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Pages de propriété de Source des fichiers, les propriétés communes, Solution de débogage](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Spécifier les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (extension de débogage SOS)](http://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)



