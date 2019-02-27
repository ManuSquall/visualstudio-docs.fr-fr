---
title: 'Procédure : Référencer les informations de symboles Windows | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, symbol servers
- servers, symbol servers
- profiling tools, symbol servers
- symbol servers
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 347b35a1ed47236c0d6e6c187224ee50fd79852c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619886"
---
# <a name="how-to-reference-windows-symbol-information"></a>Procédure : Référencer les informations de symboles Windows
Les Outils de profilage Visual Studio utilisent des fichiers de symboles (.*pdb*) pour résoudre les noms symboliques, par exemple les noms de fonctions dans les fichiers binaires d’un programme. Vous pouvez effectuer les étapes suivantes pour télécharger et mettre à jour automatiquement les fichiers .*pdb* correspondant à la version de Windows installée sur l’ordinateur local.

> [!NOTE]
>  Ce paramètre n’affecte pas les rapports existants. Seuls ceux créés après la spécification du serveur de symboles auront les informations de symboles.

 Pour plus d’informations, consultez [Spécifier les fichiers de symboles (.*pdb*) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-use-the-microsoft-symbol-server"></a>Pour utiliser le serveur de symboles Microsoft

1.  Créez un dossier destiné à contenir les informations du fichier de symboles (par exemple, C:\SymbolCache).

2.  Dans le menu **Outils** , cliquez sur **Options**.

     La boîte de dialogue **Options** s'affiche.

3.  Développez l’arborescence **Débogage**, puis cliquez sur **Symboles**.

4.  Dans **Emplacements du fichier de symboles (.pdb)**, sélectionnez **Serveurs de symboles Microsoft**.

5.  Dans **Mettre en cache les symboles à partir du serveur de symboles vers ce répertoire**, tapez le chemin du dossier créé à l’étape 1 ; par exemple :

     **C:\SymbolCache**

     Vous pouvez également cliquer sur le bouton de sélection (**...**), puis sélectionner un répertoire dans la boîte de dialogue **Rechercher un dossier**.

## <a name="see-also"></a>Voir aussi
- [Configurer des sessions de performances](../profiling/configuring-performance-sessions.md)
- [Guide pratique pour sérialiser les informations de symbole](../profiling/how-to-serialize-symbol-information.md)