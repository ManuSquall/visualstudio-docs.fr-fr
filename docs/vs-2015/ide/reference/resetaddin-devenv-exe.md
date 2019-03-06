---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1400e61487a7ad052d5a516019e76149e8e3d31e
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54755052"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Supprime les commandes et l’interface utilisateur des commandes associées au complément.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Arguments  
 `AddIn`  
 Optionnel. Nom de commande du complément.  
  
## <a name="remarks"></a>Remarques  
 Par défaut, le nom de commande du complément est égal à *\<nom_solution_complément>*.Connect<em>.\<nom_solution_complément></em> et s’affiche dans Connect.cs en tant que paramètre `commandName` de la méthode `Exec`. Vous pouvez également vérifier le nom de la commande en tapant les premières lettres du nom du complément dans la fenêtre Commandes de Visual Studio, puis en utilisant Intellisense pour compléter la saisie.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant démarre Visual Studio et empêche le complément `MyAddin` de s’exécuter au démarrage.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
