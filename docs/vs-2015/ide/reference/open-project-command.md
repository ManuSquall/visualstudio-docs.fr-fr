---
title: Ouvrir un projet, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 916ea8435571efc01f38e408d4fc2d4563c16f1c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54753483"
---
# <a name="open-project-command"></a>Ouvrir un projet, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Ouvre un projet existant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Obligatoire. Chemin complet et nom de fichier du projet à ouvrir.  
  
 La syntaxe de l’argument `filename` nécessite que les chemins contenant des espaces utilisent des guillemets.  
  
## <a name="remarks"></a>Remarques  
 La saisie semi-automatique tente de deviner le chemin et le nom de fichier à mesure que vous tapez.  
  
 Cette commande n’est pas disponible lors du débogage.  
  
## <a name="example"></a>Exemple  
 Cet exemple ouvre le projet [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Test1.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
