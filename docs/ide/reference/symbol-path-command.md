---
title: "Chemin d’accès aux symboles, commande | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d446779e4f84bf19e965393f9fa1142c7e4e166a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="symbol-path-command"></a>Chemin d’accès aux symboles, commande
Définit la liste des répertoires où le débogueur recherche des symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Arguments  
 `pathname`  
 Facultatif. Liste de chemins délimités par des points-virgules dans laquelle le débogueur doit rechercher des symboles.  
  
## <a name="remarks"></a>Remarques  
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