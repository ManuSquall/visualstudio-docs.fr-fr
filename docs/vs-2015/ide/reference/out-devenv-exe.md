---
title: -Out (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4edcdf6da73c3f4c4ee9d221d7bbaef8e520c5e3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504273"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [-Out (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/out-devenv-exe).  
  
  
Spécifie un fichier pour stocker et afficher les erreurs qui se produisent quand vous exécutez, générez, regénérez ou déployez une solution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>Arguments  
 `FileName`  
 Obligatoire. Chemin et nom du fichier où seront enregistrées les erreurs rencontrées au cours de la génération d’un exécutable.  
  
## <a name="remarks"></a>Notes  
 Si un nom de fichier qui n’existe pas est spécifié, le fichier est créé automatiquement. Si le fichier existe déjà, les résultats sont ajoutés au contenu existant du fichier.  
  
 Les erreurs de build de ligne de commande sont affichées dans la fenêtre **Commande** et dans la vue Générateur de solutions de la fenêtre **Sortie**. Cette option s’avère utile si vous exécutez des générations sans assistance et que vous devez afficher les résultats.  
  
## <a name="example"></a>Exemple  
 Cet exemple exécute `MySolution` et écrit les erreurs dans le fichier `MyErrorLog.txt`.  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commutateurs de la ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)



