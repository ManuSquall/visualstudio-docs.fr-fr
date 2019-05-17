---
title: Exécutable pour la boîte de dialogue de Session de débogage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41b93ae19afd54b6e22458d1ba12029d5bb93cf3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62849963"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Exécutable pour la session de débogage (boîte de dialogue)

Cette boîte de dialogue s'affiche lorsque vous essayez de déboguer une DLL pour laquelle aucun exécutable n'est spécifié. Visual Studio ne peut pas lancer une DLL directement. Au lieu de cela, Visual Studio lance l’exécutable spécifié. Vous pouvez déboguer la DLL lorsqu’elle est appelée par l’exécutable.

 **Nom du fichier exécutable** Entrez le nom de chemin d’accès à un fichier exécutable qui appelle la DLL que vous déboguez.

 **URL où le projet peut être accessible (ATL Server uniquement)** si vous déboguez une DLL ATL Server, entrez l’URL où se trouve le projet.

 Une fois entrées, ces paramètres sont stockés dans le projet de Pages de propriétés, donc vous n’aurez pas à les entrer à nouveau lors des sessions de débogage suivantes. Si vous devez les modifier, ouvrez les Pages de propriétés et apportez les changements voulus. Pour plus d’informations sur la spécification d’un exécutable pour la session de débogage, consultez [Débogage de DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.md)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)