---
title: Afficher la source, commande | Microsoft Docs
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
ms.openlocfilehash: ff216ddd8943ea971669c6ebb1c7c0306b02160f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171975"
---
# <a name="list-source-command"></a>Afficher la source, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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



