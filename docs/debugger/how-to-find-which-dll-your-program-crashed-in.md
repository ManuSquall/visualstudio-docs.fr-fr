---
title: Rechercher la DLL dans laquelle votre programme s’est bloqué dans | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4432378e10590c2ba930edf0920b9146e450f96
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852072"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Comment : Rechercher la DLL en panne dans votre programme (C#, C++, Visual Basic, F #)

 Si votre application tombe en panne pendant un appel à une DLL système ou au code de quelqu'un d'autre, vous devez rechercher la DLL active au moment de l'incident. Si une panne survient dans une DLL en dehors de votre programme, vous pouvez identifier l’emplacement en utilisant la fenêtre **Modules**.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Pour savoir où une panne s'est produite à l'aide de la fenêtre Modules

1. Notez l'adresse où la panne s'est produite.

    Si l’adresse n’est pas affichée dans le message d’erreur, vous devrez peut-être utiliser d’autres méthodes pour identifier la DLL. Si vous pensez qu’il s’agit d’une DLL système, vous pouvez [charger des symboles](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) à partir des serveurs de symboles Microsoft lors du débogage. Dans le cas contraire, vous devrez peut-être [créer un fichier dump](../debugger/using-dump-files.md) avec des informations de tas à la place. Différents [Outils](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) sont disponibles pour créer des fichiers de vidage.

2. Dans le menu **Déboguer**, sélectionnez **Fenêtres**, puis cliquez sur **Modules**.

3. Dans la fenêtre **Modules**, trouvez la colonne **Adresse**. Faites défiler la fenêtre à l'aide de la barre de défilement, si nécessaire.

4. Cliquez sur le bouton **Adresse** en haut de la colonne pour trier les DLL par adresse.

5. Recherchez dans la liste triée la DLL dont la plage d'adresse contient l'emplacement de la panne.

6. Les colonnes **Nom** et **Chemin d’accès** vous indiquent le nom et le chemin de la DLL.

## <a name="see-also"></a>Voir aussi
- [Débogage de projets DLL](../debugger/debugging-dll-projects.md)
- [Comment : utiliser la fenêtre Modules](../debugger/how-to-use-the-modules-window.md)