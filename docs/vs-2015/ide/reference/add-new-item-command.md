---
title: Ajouter un nouvel élément, commande | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8f380a11440ed413871d2c80603148aa7cc77390
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505231"
---
# <a name="add-new-item-command"></a>Ajouter un nouvel élément, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Ajouter nouvel élément, commande](https://docs.microsoft.com/visualstudio/ide/reference/add-new-item-command).  
  
  
Ajoute un nouvel élément de solution, par exemple un fichier .htm, .css ou .txt, ou un jeu de frames, à la solution actuelle et l’ouvre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Facultatif. Chemin et nom de fichier de l’élément à ajouter à la solution.  
  
## <a name="switches"></a>Commutateurs  
 /t: `templatename`  
 Facultatif. Spécifie le type de fichier à créer. Si aucun nom de modèle n’est indiqué, un fichier texte est créé par défaut.  
  
 La syntaxe de l’argument /t:`templatename` reflète les informations de la boîte de dialogue **Ajouter un nouvel élément de solution**. Vous devez entrer la catégorie complète suivie du type de fichier, en séparant le nom de catégorie et le type de fichier par une barre oblique inverse (`\`) et en mettant toute la chaîne entre guillemets.  
  
 Par exemple, pour créer un fichier texte, entrez les informations suivantes pour l’argument /t:`templatename`.  
  
```  
/t:"General\Style Sheet"  
```  
  
 /e: `editorname`  
 Facultatif. Nom de l’éditeur dans lequel le fichier doit être ouvert. Si l’argument est spécifié, mais qu’aucun nom d’éditeur n’est fourni, la boîte de dialogue **Ouvrir avec** s’affiche.  
  
 La syntaxe de l’argument /e:`editorname` utilise les noms d’éditeur tels qu’ils apparaissent dans la **boîte de dialogue Ouvrir avec**, entre guillemets.  
  
 Par exemple, pour ouvrir une feuille de style dans l’éditeur de code source, entrez les informations suivantes pour l’argument /e:`editorname`.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple ajoute un nouvel élément de solution, MyHTMLpg, à la solution actuelle.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



