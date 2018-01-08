---
title: "Exécutable de débogage, boîte de dialogue Session | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.exefordebug
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
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c52d66d0a2e71b96a907fc73b16d42fa13b080bb
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2018
---
# <a name="executable-for-debugging-session-dialog-box"></a>Exécutable pour la session de débogage (boîte de dialogue)
Cette boîte de dialogue s'affiche lorsque vous essayez de déboguer une DLL pour laquelle aucun exécutable n'est spécifié. Visual Studio ne peut pas lancer une DLL directement. Il lance d'abord l'exécutable spécifié. Vous pouvez déboguer la DLL après l'avoir appelée dans l'exécutable.  
  
 **Nom du fichier exécutable**  
 Entrez le chemin d’accès d’un exécutable qui appelle la DLL à déboguer.  
  
 **Accéder à l’URL où le projet peut être (ATL Server uniquement)**  
 Si vous déboguez une DLL ATL Server, entrez l'URL permettant d'accéder au projet.  
  
 Les paramètres que vous entrez sont stockés dans les Pages de propriétés du projet, de sorte que vous n'avez pas à les entrer à nouveau lors des sessions de débogage suivantes. Si vous devez les modifier, ouvrez les Pages de propriétés et apportez les changements voulus. Pour plus d’informations sur la spécification d’un exécutable pour la session de débogage, consultez [débogage de DLL](../debugger/how-to-debug-from-a-dll-project.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/index.md)  
 [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)