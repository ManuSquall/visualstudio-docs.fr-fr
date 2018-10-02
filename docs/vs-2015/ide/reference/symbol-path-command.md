---
title: Chemin d’accès aux symboles, commande | Microsoft Docs
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
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b21a745177722160b100d0bbad770c3a74c40ca3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494884"
---
# <a name="symbol-path-command"></a>Chemin d’accès aux symboles, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [chemin d’accès aux symboles, commande](https://docs.microsoft.com/visualstudio/ide/reference/symbol-path-command).  
  
  
Définit la liste des répertoires où le débogueur recherche des symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Arguments  
 `pathname`  
 Facultatif. Liste de chemins délimités par des points-virgules dans laquelle le débogueur doit rechercher des symboles.  
  
## <a name="remarks"></a>Notes  
 Si aucun `pathname` n’est spécifié, la commande répertorie les chemins des symboles actuels.  
  
## <a name="example"></a>Exemple  
 Cet exemple ajoute deux chemins à la liste des répertoires de symboles.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple affiche une liste de chemins des symboles actuels délimités par des points-virgules.  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)



