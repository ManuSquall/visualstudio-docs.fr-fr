---
title: "Affichez les DLL et les exécutables dans le débogueur | Documents Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: "36"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: caaa710f0fc34a4e6a24038a7e65e5670bebd6ea
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Afficher les DLL et les exécutables à l’aide de la fenêtre Modules dans le débogueur Visual Studio
 
Le **Modules** fenêtre répertorie les DLL et les fichiers exécutables (EXE) qui sont utilisés par votre programme et affiche des informations pertinentes pour chacun. 

> [!NOTE]
>  Cette fonctionnalité n’est pas disponible pour le débogage de script ou SQL. 
  
### <a name="to-display-the-modules-window"></a>Pour afficher la fenêtre Modules  
  
-   Pendant le débogage, sélectionnez **Déboguer > Windows** puis cliquez sur **Modules**.  
  
     Par défaut, le **Modules** fenêtre trie les modules dans l’ordre de chargement. Cependant, vous pouvez choisir d'effectuer le tri en fonction d'une autre colonne.  
  
### <a name="to-sort-by-any-column"></a>Pour trier selon une colonne  
  
-   Cliquez sur le bouton en haut de la colonne.  
  
     Vous pouvez charger des symboles ou spécifier un chemin d’accès des symboles à partir de la **Modules** fenêtre en utilisant le menu contextuel.  
  
## <a name="loading-symbols"></a>Chargement de symboles  
 Dans le **Modules** fenêtre, vous pouvez voir quels modules ont chargé des symboles de débogage. Ces informations s’affichent dans le **état du symbole** colonne. Si l’état indique **ignoré loadingCannot trouver ou ouvrir le fichier PDB**, ou **chargement désactivé par le paramètre include/exclude**, vous pouvez demander au débogueur de télécharger des symboles à partir des symboles publics Microsoft serveurs ou pour charger des symboles à partir d’un répertoire de symboles sur votre ordinateur. Pour plus d’informations, consultez [spécifier de symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Pour charger manuellement les symboles  
  
1.  Dans le **Modules** fenêtre, avec le bouton droit un module pour lequel les symboles n’ont pas chargés.  
  
2.  Pointez sur **charger les symboles depuis** puis cliquez sur **serveurs de symboles Microsoft** ou **chemin des symboles**.  
  
#### <a name="to-change-symbol-load-settings"></a>Pour modifier les paramètres de chargement de symboles  
  
1.  Dans le **Modules** fenêtre, avec le bouton droit n’importe quel module.  
  
2.  Cliquez sur **symbole paramètres**.  
  
     Vous pouvez maintenant modifier les paramètres de chargement de symboles, comme décrit dans [comportement de chargement et de spécifier des emplacements de symboles](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Les modifications seront appliquées lorsque vous redémarrerez la session de débogage.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Pour modifier le chargement des symboles pour un module spécifique  
  
1.  Dans le **Modules** fenêtre, cliquez sur le module.  
  
2.  Pointez sur **paramètres de chargement des symboles automatique** puis cliquez sur **toujours charger manuellement** ou **par défaut**. Les modifications seront appliquées lorsque vous redémarrerez la session de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Interruption de l’exécution](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Spécifiez les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)