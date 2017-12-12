---
title: -Diff | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5377fedb-632a-4e86-a947-7c11c86451e7
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d38ef64a370b11c2695ea1e03d2e3ceead7cb63c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="diff"></a>/Diff
Compare deux fichiers. Les différences sont affichées dans une fenêtre spéciale de Visual Studio.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv /Diff SourceFile, TargetFile, [SourceDisplayName],[TargetDisplayName]  
```  
  
## <a name="arguments"></a>Arguments  
 `SourceFile`  
 Obligatoire. Chemin complet et nom du premier fichier à comparer.  
  
 `TargetFile`  
 Obligatoire. Chemin complet et nom du deuxième fichier à comparer.  
  
 `SourceDisplayName`  
 Facultatif. Nom d’affichage du premier fichier.  
  
 `TargetDisplayName`  
 Facultatif. Nom d’affichage du deuxième fichier.