---
title: Afficher la source, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: e0a4a8482dc1c2c66a45902f2f3382b179b46b13
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662840"
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
 Optionnel. Spécifie le nombre de lignes à afficher.  
  
 /Current  
 Optionnel. Affiche la ligne active.  
  
 /File:`filename`  
 Optionnel. Chemin du fichier à afficher. Si aucun nom de fichier n’est spécifié, la commande affiche le code source de la ligne de l’instruction actuelle.  
  
 /Line:`number`  
 Optionnel. Affiche un numéro de ligne spécifique.  
  
 /ShowLineNumbers:`yes|no`  
 Optionnel. Spécifie s’il faut afficher les numéros de ligne.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="example"></a>Exemple  
 Cet exemple affiche le code source à partir de la ligne 4 du fichier Form1.vb, avec les numéros de ligne.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)
