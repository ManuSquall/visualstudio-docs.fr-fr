---
title: Aucune Source disponible | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e02c91f5e5a55e82633d89aa7209321126271e8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="no-source-available"></a>Aucune source disponible
Votre projet ne contient pas de code source pour le code que vous essayez d'afficher. La cause habituelle est double-clic sur un module qui n’a pas de code source dans le **fenêtre Pile des appels** ou **fenêtre Threads**. Vous pouvez poursuivre le débogage, mais vous ne pouvez pas utiliser la fenêtre source pour définir les points d'arrêt et accomplir d'autres actions à cet emplacement. Si vous devez définir un point d’arrêt, utilisez la **fenêtre code machine** à la place.  
  
 Dans les pages de propriétés de la solution, vous pouvez changer les répertoires dans lesquels le débogueur recherche des fichiers sources et demander au débogueur d'ignorer les fichiers sources sélectionnés. Consultez [déboguer la boîte de dialogue Pages de propriété de Source, propriétés communes, les fichiers Solution](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Cliquez sur Parcourir pour rechercher du code source**  
 Cliquez sur ce lien pour ouvrir une boîte de dialogue où vous pouvez rechercher le code source.  
  
 **Afficher le code machine**  
 Lance le **fenêtre code machine**.  
  
 **Toujours afficher le code machine pour les fichiers sources manquants**  
 Sélectionnez cette option pour afficher le **fenêtre code machine** automatiquement lorsque aucune source n’est disponible. Ce paramètre peut également être modifié dans le **Options** boîte de dialogue, **débogage** catégorie, **général** page, en activant ou désactivant **afficher le code machine si source n’est pas disponible**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer la boîte de dialogue Pages de propriété de Source, propriétés communes, les fichiers Solution](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Spécifiez les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (extension de débogage SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)