---
title: Nouveau fichier, commande | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f3b469466080403122484a7b6259c099765edd7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="new-file-command"></a>Nouveau fichier, commande
Crée un fichier et l’ouvre. Le fichier s’affiche sous le dossier Fichiers divers.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
File.NewFile [filename] [/t:templatename] [/editor:editorname]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Facultatif. Nom du fichier. Si aucun nom n’est fourni, un nom par défaut est utilisé. Si aucun nom de modèle n’est indiqué, un fichier texte est créé.  
  
## <a name="switches"></a>Commutateurs  
 /t:`templatename`  
 Facultatif. Spécifie le type de fichier à créer.  
  
 La syntaxe de l’argument /t:`templatename` reflète les informations de la boîte de dialogue Nouveau fichier. Entrez le nom de la catégorie suivi d’une barre oblique inverse (`\`) et du nom du modèle, et placez la chaîne entière entre guillemets.  
  
 Par exemple, pour créer un fichier source [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], entrez les informations suivantes pour l’argument /t:`templatename`.  
  
```  
/t:"Visual C++\C++ File (.cpp)"  
```  
  
 L’exemple ci-dessus indique que le modèle de fichier C++ se trouve sous la catégorie Visual C++ dans la boîte de dialogue **Nouveau fichier**.  
  
 /e:`editorname`  
 Facultatif. Nom de l’éditeur dans lequel le fichier doit être ouvert. Si l’argument est spécifié, mais qu’aucun nom d’éditeur n’est fourni, la boîte de dialogue **Ouvrir avec** s’affiche.  
  
 La syntaxe de l’argument /e:`editorname` utilise les noms d’éditeur tels qu’ils apparaissent dans la boîte de dialogue Ouvrir avec, entre guillemets.  
  
 Par exemple, pour ouvrir un fichier dans l’éditeur de code source, entrez les informations suivantes pour l’argument /e:`editorname`.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple crée une page web « test1.htm » et l’ouvre dans l’éditeur de code source.  
  
```  
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Fenêtre Exécution](../../ide/reference/immediate-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commande Visual Studio](../../ide/reference/visual-studio-command-aliases.md)