---
title: Afficher les modules, commande | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26c2a2c07e09863c3320c3c69b8cc093bdf39466
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54790031"
---
# <a name="list-modules-command"></a>Afficher les modules, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Répertorie les modules pour le processus en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]  
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]  
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]  
```  
  
#### <a name="parameters"></a>Paramètres  
 /Address:`yes|no`  
 Optionnel. Spécifie s’il faut afficher les adresses mémoire des modules. La valeur par défaut est `yes`.  
  
 /Name:`yes|no`  
 Optionnel. Spécifie s’il faut afficher les noms des modules. La valeur par défaut est `yes`.  
  
 /Order:`yes|no`  
 Optionnel. Spécifie s’il faut afficher l’ordre des modules. La valeur par défaut est `no`.  
  
 /Path:`yes|no`  
 Optionnel. Spécifie s’il faut afficher les chemins des modules. La valeur par défaut est `yes`.  
  
 /Process:`yes|no`  
 Optionnel. Spécifie s’il faut afficher les processus des modules. La valeur par défaut est `no`.  
  
 /SymbolFile:`yes|no`  
 Optionnel. Spécifie s’il faut afficher les fichiers de symboles des modules. La valeur par défaut est `no`.  
  
 /SymbolStatus:`yes|no`  
 Optionnel. Spécifie s’il faut afficher les états des symboles des modules. La valeur par défaut est `yes`.  
  
 /Timestamp:`yes|no`  
 Optionnel. Spécifie s’il faut afficher les horodatages des modules. La valeur par défaut est `no`.  
  
 /Version:`yes|no`  
 Optionnel. Spécifie s’il faut afficher les versions des modules. La valeur par défaut est `no`.  
  
## <a name="remarks"></a>Remarques  
  
## <a name="example"></a>Exemple  
 Cet exemple répertorie les noms, les adresses et les horodatages des modules pour le processus actuel.  
  
```  
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Guide pratique pour utiliser la fenêtre Modules](../../debugger/how-to-use-the-modules-window.md)
