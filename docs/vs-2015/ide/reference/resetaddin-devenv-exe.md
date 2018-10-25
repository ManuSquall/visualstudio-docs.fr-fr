---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1b53a30845ca4b20372fb5a6e3552f31f3c1b60
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950522"
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
 Facultatif. Nom de commande du complément.  
  
## <a name="remarks"></a>Notes  
 Par défaut, le nom de commande du complément est égal à *\<nom_solution_complément>*.Connect<em>.\<nom_solution_complément></em> et s’affiche dans Connect.cs en tant que paramètre `commandName` de la méthode `Exec`. Vous pouvez également vérifier le nom de la commande en tapant les premières lettres du nom du complément dans la fenêtre Commandes de Visual Studio, puis en utilisant Intellisense pour compléter la saisie.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant démarre Visual Studio et empêche le complément `MyAddin` de s’exécuter au démarrage.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)



