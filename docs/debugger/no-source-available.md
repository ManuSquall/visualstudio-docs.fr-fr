---
title: Aucune Source disponible | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d1d1307a119fa23bf7ba015130ab9c7b6f69d5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56703693"
---
# <a name="no-source-available"></a>Aucune source disponible
Votre projet ne contient pas de code source pour le code que vous essayez d'afficher. La cause habituelle est le double-clic sur un module qui n’a pas de code source dans la **Fenêtre Pile des appels** ou la **Fenêtre Threads**. Vous pouvez poursuivre le débogage, mais vous ne pouvez pas utiliser la fenêtre source pour définir les points d'arrêt et accomplir d'autres actions à cet emplacement. Si vous avez besoin de définir un point d’arrêt, utilisez plutôt la **Fenêtre Code Machine**.

 Dans les pages de propriétés de la solution, vous pouvez changer les répertoires dans lesquels le débogueur recherche des fichiers sources et demander au débogueur d'ignorer les fichiers sources sélectionnés. Consultez [déboguer la boîte de dialogue Pages de propriété de Source des fichiers, les propriétés communes, Solution](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Cliquez sur Parcourir pour rechercher du code source** cliquez sur ce lien pour ouvrir une boîte de dialogue où vous pouvez rechercher le code source.

 **Afficher le code machine** lance le **fenêtre code machine**.

 **Toujours afficher le code machine pour les fichiers sources manquants** Sélectionnez cette option pour afficher le **fenêtre code machine** automatiquement quand aucune source n’est disponible. Ce paramètre peut également être modifié dans la boîte de dialogue **Options**, catégorie **Débogage**, page **Général**, en activant ou en désactivant **Afficher le code machine si la source n’est pas disponible**.

## <a name="see-also"></a>Voir aussi
- [Fichiers sources pour le débogage, Propriétés communes, boîte de dialogue Pages de propriétés de solution](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (extension de débogage SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)