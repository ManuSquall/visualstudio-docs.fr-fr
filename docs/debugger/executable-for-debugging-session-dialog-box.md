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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 90278476b2530e80c33440ca6e2dc299be5e9be5
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269785"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Exécutable pour la session de débogage (boîte de dialogue)

Cette boîte de dialogue s'affiche lorsque vous essayez de déboguer une DLL pour laquelle aucun exécutable n'est spécifié. Visual Studio ne peut pas lancer une DLL directement. Au lieu de cela, Visual Studio lance l’exécutable spécifié. Vous pouvez déboguer la DLL lorsqu’elle est appelée par l’exécutable.  
  
 **Nom de fichier de l’exécutable**  
 Entrez le chemin d’accès d’un exécutable qui appelle la DLL à déboguer.  
  
 **URL d’accès au projet (ATL Server uniquement)**  
 Si vous déboguez une DLL ATL Server, entrez l'URL permettant d'accéder au projet.  
  
 Une fois entrées, ces paramètres sont stockés dans le projet de Pages de propriétés, donc vous n’aurez pas à les entrer à nouveau lors des sessions de débogage suivantes. Si vous devez les modifier, ouvrez les Pages de propriétés et apportez les changements voulus. Pour plus d’informations sur la spécification d’un exécutable pour la session de débogage, consultez [Débogage de DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
## <a name="see-also"></a>Voir aussi

 [Débogage dans Visual Studio](../debugger/index.md)  
 [Présentation du débogueur](../debugger/debugger-feature-tour.md)