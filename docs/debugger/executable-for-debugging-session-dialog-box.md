---
title: Exécutable de la session de débogage, boîte de dialogue | Microsoft Docs
description: Pour déboguer une DLL, vous devez spécifier un exécutable pour appeler la DLL. En savoir plus sur la boîte de dialogue qui s’affiche quand aucun fichier exécutable n’est spécifié.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 20f97c7597dc266fbb4334daf27d3660b351f35a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870829"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Exécutable pour la session de débogage (boîte de dialogue)

Cette boîte de dialogue s'affiche lorsque vous essayez de déboguer une DLL pour laquelle aucun exécutable n'est spécifié. Visual Studio ne peut pas lancer une DLL directement. Au lieu de cela, Visual Studio lance l’exécutable spécifié. Vous pouvez déboguer la DLL quand elle est appelée par l’exécutable.

 **Nom du fichier exécutable** Entrez le nom du chemin d’accès à un fichier exécutable qui appelle la DLL que vous déboguez.

 **URL où le projet est accessible (ATL Server uniquement)** Si vous déboguez une DLL ATL Server, entrez l’URL où se trouve le projet.

 Une fois entrés, ces paramètres sont stockés dans les pages de propriétés du projet, vous n’avez donc pas besoin de les entrer à nouveau pour les sessions de débogage suivantes. Si vous devez les modifier, ouvrez les Pages de propriétés et apportez les changements voulus. Pour plus d’informations sur la spécification d’un exécutable pour la session de débogage, consultez [débogage de dll](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../debugger/index.yml)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)