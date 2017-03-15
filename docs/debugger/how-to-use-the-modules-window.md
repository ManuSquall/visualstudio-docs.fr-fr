---
title: "Comment&#160;: utiliser la fen&#234;tre Modules | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.modules"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogueur, fenêtre Modules"
  - "Modules (fenêtre)"
  - "fichiers exécutables, affichage pendant le débogage"
  - "débogage (Visual Studio), affichage des modules"
  - "DLL, affichage pendant le débogage"
  - "modules, affichage"
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 36
caps.handback.revision: 36
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: utiliser la fen&#234;tre Modules
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

> [!NOTE]
>  Cette fonctionnalité n'est pas disponible pour le débogage de script ou SQL.  
  
 La fenêtre **Modules** répertorie les fichiers DLL et EXE utilisés par votre programme et affiche des informations pertinentes sur ces fichiers.  
  
### Pour afficher la fenêtre Modules en mode arrêt ou en mode exécution  
  
-   Dans le menu **Déboguer**, cliquez sur **Fenêtres**, puis sur **Modules**.  
  
     Par défaut, la fenêtre **Modules** trie les modules dans l'ordre de chargement.  Cependant, vous pouvez choisir d'effectuer le tri en fonction d'une autre colonne.  
  
### Pour trier selon une colonne  
  
-   Cliquez sur le bouton en haut de la colonne.  
  
     Vous pouvez charger des symboles ou spécifier un chemin d'accès aux symboles depuis la fenêtre **Modules** à l'aide du menu contextuel.  
  
## Chargement de symboles  
 La fenêtre **Modules** vous permet de connaître les modules pour lesquels des symboles de débogage sont chargés.  Pour cela, il suffit de consulter la colonne **État du symbole**.  Si l'état indique **Chargement des symboles ignoré**, **Impossible de trouver ou d'ouvrir le fichier PDB** ou **Chargement désactivé par le paramètre Include\/Exclude**, vous pouvez demander au débogueur de télécharger des symboles à partir des serveurs de symboles publics Microsoft ou de charger des symboles à partir d'un répertoire de symboles sur votre ordinateur.  Pour plus d’informations, consultez [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### Pour charger manuellement les symboles  
  
1.  Dans la fenêtre **Modules**, cliquez avec le bouton droit sur un module pour lequel des symboles n'ont pas été chargés.  
  
2.  Pointez sur **Charger les symboles depuis** et cliquez sur **Serveur de symboles publics Microsoft** ou sur **Chemin d'accès aux symboles**.  
  
#### Pour modifier les paramètres de chargement de symboles  
  
1.  Dans la fenêtre **Modules**, cliquez avec le bouton droit sur un module.  
  
2.  Cliquez sur **Paramètres des symboles**.  
  
     Vous pouvez désormais modifier les paramètres de chargement des symboles, comme indiqué dans [Spécifier les emplacements de symboles et le comportement de chargement](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).  Les modifications seront appliquées lorsque vous redémarrerez la session de débogage.  
  
#### Pour modifier le chargement des symboles pour un module spécifique  
  
1.  Dans la fenêtre **Modules**, cliquez avec le bouton droit sur le module.  
  
2.  Pointez sur **Paramètres de chargement des symboles automatique**, puis cliquez sur **Toujours charger manuellement** ou **Par défaut**.  Les modifications seront appliquées lorsque vous redémarrerez la session de débogage.  
  
## Voir aussi  
 [Breaking Execution](http://msdn.microsoft.com/fr-fr/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)