---
title: 'Comment : utiliser la fenêtre Modules | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b592515692e23dce49c125c7895bd158904b653f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696127"
---
# <a name="how-to-use-the-modules-window"></a>Comment : utiliser la fenêtre Modules
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
> Cette fonctionnalité n'est pas disponible pour le débogage de script ou SQL.  
  
 La fenêtre **modules** répertorie les dll et exe utilisés par votre programme et affiche des informations pertinentes pour chacune d’elles.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Pour afficher la fenêtre Modules en mode arrêt ou en mode exécution  
  
- Dans le menu **Déboguer** , choisissez **fenêtres**, puis cliquez sur **modules**.  
  
     Par défaut, la fenêtre **Modules** trie les modules dans l’ordre de chargement. Cependant, vous pouvez choisir d'effectuer le tri en fonction d'une autre colonne.  
  
### <a name="to-sort-by-any-column"></a>Pour trier selon une colonne  
  
- Cliquez sur le bouton en haut de la colonne.  
  
     Vous pouvez charger des symboles ou spécifier un chemin d’accès aux symboles à partir de la fenêtre **modules** à l’aide du menu contextuel.  
  
## <a name="loading-symbols"></a>Chargement de symboles  
 Dans la fenêtre **modules** , vous pouvez voir quels modules ont des symboles de débogage chargés. Ces informations s’affichent dans la colonne **État du symbole** . Si l’état indique **ignoré loadingCannot Rechercher ou ouvrir le fichier PDB**, ou **chargement désactivé par le paramètre include/Exclude**, vous pouvez demander au débogueur de télécharger des symboles à partir des serveurs de symboles publics Microsoft ou de charger des symboles à partir d’un répertoire de symboles sur votre ordinateur. Pour plus d’informations, consultez [spécifier les fichiers de symboles (. pdb) et les fichiers sources.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Pour charger manuellement les symboles  
  
1. Dans la fenêtre **modules** , cliquez avec le bouton droit sur un module pour lequel les symboles n’ont pas été chargés.  
  
2. Pointez sur **charger les symboles à partir de** , puis cliquez sur **serveurs de symboles Microsoft** ou **chemin d’accès**aux symboles.  
  
#### <a name="to-change-symbol-load-settings"></a>Pour modifier les paramètres de chargement de symboles  
  
1. Dans la fenêtre **Modules**, cliquez avec le bouton droit sur un module.  
  
2. Cliquez sur **paramètres des symboles**.  
  
     Vous pouvez maintenant modifier les paramètres de chargement des symboles, comme décrit dans [spécifier les emplacements de symboles et le comportement de chargement](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Les modifications seront appliquées lorsque vous redémarrerez la session de débogage.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Pour modifier le chargement des symboles pour un module spécifique  
  
1. Dans la fenêtre **Modules**, cliquez avec le bouton droit sur le module.  
  
2. Pointez sur **paramètres de chargement automatique des symboles** , puis cliquez sur **toujours charger manuellement** ou **par défaut**. Les modifications seront appliquées lorsque vous redémarrerez la session de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Interruption de l’exécution](https://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Spécifier les fichiers de symboles (.pdb) et les fichiers source](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
