---
title: Référencer les informations de symboles Windows | Microsoft Docs
description: Découvrez comment Visual Studio Outils de profilage utiliser des fichiers de symboles (. pdb) pour résoudre des noms symboliques tels que les noms de fonctions dans les fichiers binaires de programme.
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c788be648b77a36b8da7027c89a7d9cb047b57d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907089"
---
# <a name="how-to-reference-windows-symbol-information"></a>Guide pratique pour référencer les informations de symboles Windows
Les Outils de profilage Visual Studio utilisent des fichiers de symboles (.*pdb*) pour résoudre les noms symboliques, par exemple les noms de fonctions dans les fichiers binaires d’un programme. Vous pouvez effectuer les étapes suivantes pour télécharger et mettre à jour automatiquement les fichiers .*pdb* correspondant à la version de Windows installée sur l’ordinateur local.

> [!NOTE]
> Ce paramètre n’affecte pas les rapports existants. Seuls ceux créés après la spécification du serveur de symboles auront les informations de symboles.

 Pour plus d’informations, consultez [Specify Symbol (.*PDB*) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-use-the-microsoft-symbol-server"></a>Pour utiliser le serveur de symboles Microsoft

1. Créez un dossier destiné à contenir les informations du fichier de symboles (par exemple, C:\SymbolCache).

2. Dans le menu **Outils** , cliquez sur **Options**.

     La boîte de dialogue **Options** s'affiche.

3. Développez l’arborescence **Débogage**, puis cliquez sur **Symboles**.

4. Dans **Emplacements du fichier de symboles (.pdb)**, sélectionnez **Serveurs de symboles Microsoft**.

5. Dans **Mettre en cache les symboles à partir du serveur de symboles vers ce répertoire**, tapez le chemin du dossier créé à l’étape 1 ; par exemple :

     **C:\SymbolCache**

     Vous pouvez également cliquer sur le bouton de sélection (**...**), puis sélectionner un répertoire dans la boîte de dialogue **Rechercher un dossier**.

## <a name="see-also"></a>Voir aussi
- [Configurer des sessions de performance](../profiling/configuring-performance-sessions.md)
- [Comment : sérialiser les informations de symboles](../profiling/how-to-serialize-symbol-information.md)
