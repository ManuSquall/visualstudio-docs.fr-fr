---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 36b003f4890b16a7b69f7f66f8b0ef83a0ade7ac
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2018
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
Supprime les commandes et l’interface utilisateur des commandes associées au complément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Arguments  
 `AddIn`  
 Facultative. Nom de commande du complément.  
  
## <a name="remarks"></a>Notes  
 Par défaut, le nom de commande du complément est égal à *\<nom_solution_complément>*.Connect*.\<nom_solution_complément>* et s’affiche dans Connect.cs en tant que paramètre `commandName` de la méthode `Exec`. Vous pouvez également vérifier le nom de la commande en tapant les premières lettres du nom du complément dans la fenêtre Commandes de Visual Studio, puis en utilisant Intellisense pour compléter la saisie.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant démarre Visual Studio et empêche le complément `MyAddin` de s’exécuter au démarrage.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)   
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)