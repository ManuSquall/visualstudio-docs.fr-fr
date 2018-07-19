---
title: 'Comment : savoir quelle DLL votre programme a causé l’arrêt | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 350cd8a78780eb8ddb2a197ed1e8920fda23bbf3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474825"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Comment : savoir quelle DLL a causé l'arrêt de votre programme
  
 Si votre application tombe en panne pendant un appel à une DLL système ou au code de quelqu'un d'autre, vous devez rechercher la DLL active au moment de l'incident. Si vous rencontrez un incident dans une DLL en dehors de votre propre programme, vous pouvez identifier l’emplacement en utilisant la **Modules** fenêtre.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Pour savoir où une panne s'est produite à l'aide de la fenêtre Modules  
  
1.  Notez l'adresse où la panne s'est produite.

    Si l’adresse n’est pas affiché dans le message d’erreur, vous devrez peut-être utiliser d’autres méthodes pour identifier la DLL. Si vous suspectez une DLL système, vous pouvez [charger les symboles](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) à partir des serveurs de symboles Microsoft lors du débogage. Dans le cas contraire, vous devrez peut-être [créer un fichier dump](../debugger/using-dump-files.md) avec segment de mémoire des informations à la place. Divers [outils](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) sont disponibles pour créer des fichiers de vidage.
  
2.  Sur le **déboguer** menu, choisissez **Windows**, puis cliquez sur **Modules**.  
  
3.  Dans le **Modules** fenêtre, recherchez le **adresse** colonne. Faites défiler la fenêtre à l'aide de la barre de défilement, si nécessaire.  
  
4.  Cliquez sur le **adresse** bouton en haut de la colonne pour trier les DLL par adresse.  
  
5.  Recherchez dans la liste triée la DLL dont la plage d'adresse contient l'emplacement de la panne.  
  
6.  Examinez le **nom** et **chemin d’accès** colonnes pour afficher le nom de la DLL et le chemin d’accès.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de projets DLL](../debugger/debugging-dll-projects.md)   
 [Guide pratique pour utiliser la fenêtre Modules](../debugger/how-to-use-the-modules-window.md)