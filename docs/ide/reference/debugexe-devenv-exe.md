---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8f50bfd0fa5b0f9303bc6256078a30da6e1c0575
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
Ouvre le fichier exécutable spécifié à déboguer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Arguments  
 `ExecutableFile`  
 Obligatoire. Chemin et nom d’un fichier .exe.  
  
 Si le fichier .exe est introuvable ou n’existe pas, aucun avertissement ni erreur ne s’affiche et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] démarre normalement.  
  
## <a name="remarks"></a>Notes  
 Toute chaîne qui suit le paramètre `ExecutableFile` est passée à ce fichier comme argument.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant ouvre le fichier `MyApplication.exe` pour débogage.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)