---
title: Exécutable pour la boîte de dialogue de Session de débogage | Microsoft Docs
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
- vs.debug.exefordebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31190bf669d11929aed8127d8433d86c8fc75c4b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495489"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Exécutable pour la session de débogage (boîte de dialogue)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [exécutable pour la boîte de dialogue de Session de débogage](https://docs.microsoft.com/visualstudio/debugger/executable-for-debugging-session-dialog-box).  
  
Cette boîte de dialogue s'affiche lorsque vous essayez de déboguer une DLL pour laquelle aucun exécutable n'est spécifié. Visual Studio ne peut pas lancer une DLL directement. Il lance d'abord l'exécutable spécifié. Vous pouvez déboguer la DLL après l'avoir appelée dans l'exécutable.  
  
 **Nom du fichier exécutable**  
 Entrez le chemin d’accès d’un exécutable qui appelle la DLL à déboguer.  
  
 **URL où le projet peut être accessible (ATL Server uniquement)**  
 Si vous déboguez une DLL ATL Server, entrez l'URL permettant d'accéder au projet.  
  
 Les paramètres que vous entrez sont stockés dans les Pages de propriétés du projet, de sorte que vous n'avez pas à les entrer à nouveau lors des sessions de débogage suivantes. Si vous devez les modifier, ouvrez les Pages de propriétés et apportez les changements voulus. Pour plus d’informations sur la spécification d’un exécutable pour la session de débogage, consultez [débogage de DLL](../debugger/how-to-debug-native-dlls.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)



