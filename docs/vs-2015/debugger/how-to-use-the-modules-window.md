---
title: 'Comment : utiliser la fenêtre Modules | Microsoft Docs'
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
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f7a5c71a95c0e4c366b7001a3adf86d5bacc9c8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500949"
---
# <a name="how-to-use-the-modules-window"></a>Comment : utiliser la fenêtre Modules
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [afficher les Modules, les DLL et les exécutables dans le débogueur](https://docs.microsoft.com/visualstudio/debugger/how-to-use-the-modules-window).  
  
REMARQUE]
>  Cette fonctionnalité n’est pas disponible pour le débogage de script ou SQL.  
  
 Le **Modules** fenêtre répertorie les fichiers DLL et EXE utilisés par votre programme et affiche les informations pertinentes pour chacun.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Pour afficher la fenêtre Modules en mode arrêt ou en mode exécution  
  
-   Sur le **déboguer** menu, choisissez **Windows**, puis cliquez sur **Modules**.  
  
     Par défaut, le **Modules** fenêtre trie les modules par ordre de chargement. Cependant, vous pouvez choisir d'effectuer le tri en fonction d'une autre colonne.  
  
### <a name="to-sort-by-any-column"></a>Pour trier selon une colonne  
  
-   Cliquez sur le bouton en haut de la colonne.  
  
     Vous pouvez charger des symboles ou spécifier un chemin d’accès de symboles à partir de la **Modules** fenêtre en utilisant le menu contextuel.  
  
## <a name="loading-symbols"></a>Chargement de symboles  
 Dans le **Modules** fenêtre, vous pouvez voir les modules qui possèdent des symboles chargés de débogage. Cette information s’affiche dans le **état du symbole** colonne. Si l’état indique que **ignoré loadingCannot trouver ou d’ouvrir le fichier PDB**, ou **chargement désactivé par le paramètre include/exclude**, vous pouvez demander au débogueur de télécharger des symboles à partir des symboles publics Microsoft serveurs ou pour charger des symboles à partir d’un répertoire de symboles sur votre ordinateur. Pour plus d’informations, consultez [spécifier le symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Pour charger manuellement les symboles  
  
1.  Dans le **Modules** fenêtre, avec le bouton droit un module pour lequel les symboles n’ont pas chargés.  
  
2.  Pointez sur **charger les symboles depuis** puis cliquez sur **serveurs de symboles Microsoft** ou **chemin des symboles**.  
  
#### <a name="to-change-symbol-load-settings"></a>Pour modifier les paramètres de chargement de symboles  
  
1.  Dans le **Modules** fenêtre, avec le bouton droit n’importe quel module.  
  
2.  Cliquez sur **paramètres des symboles**.  
  
     Vous pouvez maintenant modifier les paramètres de chargement de symboles, comme décrit dans [spécifier des emplacements de symboles et le comportement de chargement](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Les modifications seront appliquées lorsque vous redémarrerez la session de débogage.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Pour modifier le chargement des symboles pour un module spécifique  
  
1.  Dans le **Modules** fenêtre, cliquez sur le module.  
  
2.  Pointez sur **paramètres de chargement des symboles automatique** puis cliquez sur **toujours charger manuellement** ou **par défaut**. Les modifications seront appliquées lorsque vous redémarrerez la session de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Interruption de l’exécution](http://msdn.microsoft.com/en-us/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)





