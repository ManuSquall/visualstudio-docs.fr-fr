---
title: Ouvrir un projet, commande | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: b25ee0e6ba4dfa5c29d5a009087afb55509d0c08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263913"
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



