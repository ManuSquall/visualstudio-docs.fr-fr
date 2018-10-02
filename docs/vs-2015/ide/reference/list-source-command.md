---
title: Afficher la source, commande | Microsoft Docs
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
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce57d39d609268e2570d588e6863eb1e8b8d3111
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503031"
---
# <a name="list-source-command"></a>Afficher la source, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [liste Source commande](https://docs.microsoft.com/visualstudio/ide/reference/list-source-command).  
  
  
Affiche les lignes de code source spécifiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## <a name="switches"></a>Commutateurs  
 /Count:`number`  
 Facultatif. Spécifie le nombre de lignes à afficher.  
  
 /Current  
 Facultatif. Affiche la ligne active.  
  
 /File:`filename`  
 Facultatif. Chemin du fichier à afficher. Si aucun nom de fichier n’est spécifié, la commande affiche le code source de la ligne de l’instruction actuelle.  
  
 /Line:`number`  
 Facultatif. Affiche un numéro de ligne spécifique.  
  
 /ShowLineNumbers:`yes|no`  
 Facultatif. Spécifie s’il faut afficher les numéros de ligne.  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 Cet exemple affiche le code source à partir de la ligne 4 du fichier Form1.vb, avec les numéros de ligne.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)



