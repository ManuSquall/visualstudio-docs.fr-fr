---
title: Ouvrir un projet, commande | Microsoft Docs
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
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c8f70d5605f4ee47171992e3a94c145cbdc8785
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493192"
---
# <a name="open-project-command"></a>Ouvrir un projet, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [commande Ouvrir de projet](https://docs.microsoft.com/visualstudio/ide/reference/open-project-command).  
  
  
Ouvre un projet existant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Obligatoire. Chemin complet et nom de fichier du projet à ouvrir.  
  
 La syntaxe de l’argument `filename` nécessite que les chemins contenant des espaces utilisent des guillemets.  
  
## <a name="remarks"></a>Notes  
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
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



