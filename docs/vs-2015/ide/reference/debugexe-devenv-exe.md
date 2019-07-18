---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ac542ded884e922028c6cbc16447fb2a3241613b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193808"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ouvre le fichier exécutable spécifié à déboguer.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Devenv /debugexe ExecutableFile  
```  
  
## <a name="arguments"></a>Arguments  
 `ExecutableFile`  
 Obligatoire. Chemin et nom d’un fichier .exe.  
  
 Si le fichier .exe est introuvable ou n’existe pas, aucun avertissement ni erreur ne s’affiche et [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] démarre normalement.  
  
## <a name="remarks"></a>Remarques  
 Toute chaîne qui suit le paramètre `ExecutableFile` est passée à ce fichier comme argument.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant ouvre le fichier `MyApplication.exe` pour débogage.  
  
```  
Devenv.exe /debugexe MyApplication.exe  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
