---
title: Chemin d’accès aux symboles, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 27c4c8ac23e2524245107d9052642350e9db09d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68163271"
---
# <a name="symbol-path-command"></a>Chemin d’accès aux symboles, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Définit la liste des répertoires où le débogueur recherche des symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Arguments  
 `pathname`  
 facultatif. Liste de chemins délimités par des points-virgules dans laquelle le débogueur doit rechercher des symboles.  
  
## <a name="remarks"></a>Remarques  
 Si aucun `pathname` n’est spécifié, la commande répertorie les chemins des symboles actuels.  
  
## <a name="example"></a>Exemples  
 Cet exemple ajoute deux chemins à la liste des répertoires de symboles.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>Exemples  
 Cet exemple affiche une liste de chemins des symboles actuels délimités par des points-virgules.  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
