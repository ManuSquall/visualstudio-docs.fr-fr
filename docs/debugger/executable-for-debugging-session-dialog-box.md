---
title: Exécutable de la session de débogage, boîte de dialogue | Microsoft Docs
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
ms.openlocfilehash: 14d4ac95aae860e0750af66aec6adb2969434f11
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211045"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Exécutable pour la session de débogage (boîte de dialogue)

Cette boîte de dialogue s'affiche lorsque vous essayez de déboguer une DLL pour laquelle aucun exécutable n'est spécifié. Visual Studio ne peut pas lancer une DLL directement. Au lieu de cela, Visual Studio lance l’exécutable spécifié. Vous pouvez déboguer la DLL quand elle est appelée par l’exécutable.

 **Nom du fichier exécutable** Entrez le nom du chemin d’accès à un fichier exécutable qui appelle la DLL que vous déboguez.

 **URL où le projet est accessible (ATL Server uniquement)** Si vous déboguez une DLL ATL Server, entrez l’URL où se trouve le projet.

 Une fois entrés, ces paramètres sont stockés dans les pages de propriétés du projet, vous n’avez donc pas besoin de les entrer à nouveau pour les sessions de débogage suivantes. Si vous devez les modifier, ouvrez les Pages de propriétés et apportez les changements voulus. Pour plus d’informations sur la spécification d’un exécutable pour la session de débogage, consultez [Débogage de DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.yml)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)