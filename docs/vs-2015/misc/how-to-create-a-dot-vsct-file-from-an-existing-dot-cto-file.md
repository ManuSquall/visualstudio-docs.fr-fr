---
title: 'Comment : créer un. Fichier VSCT d’un existant. Fichier de directeur technique | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: douge
ms.openlocfilehash: e77ebf34cd56cee80040009cff3ebb2fee9befac
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590599"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Comment : créer un fichier .Vsct à partir d’un fichier .Cto existant
Vous pouvez créer un fichier .vsct XML à partir d’un fichier .cto binaire existant. Cela vous permet de tirer parti du nouveau format de compilateur de la table de commande. Ce processus fonctionne même si le fichier .cto a été compilé à partir d’un fichier .ctc. Vous pouvez modifier et compiler le fichier .vsct dans un autre fichier .cto.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Pour créer un fichier .vsct à partir d’un fichier .cto  
  
1.  Obtenez des copies du fichier .cto et de son fichier .ctsym correspondant.  
  
2.  Placez les fichiers dans le même répertoire que le compilateur vsct.exe.  
  
3.  À l’invite de commandes Visual Studio, accédez au répertoire qui contient les fichiers .cto et .ctsym.  
  
4.  Type **vsct.exe** _ctofilename_**.cto** _vsctfilename_**.vsct-s**  _symfilename_**.ctsym**.  
  
     `ctofilename` est le nom du fichier .cto, `vsctfilename` est le nom du fichier vsct que vous souhaitez créer, et `symfilename` est le nom du fichier .ctsym.  
  
     Ce processus crée un fichier de compilateur de la table de commande XML .vsct. Vous pouvez modifier et compiler le fichier avec vsct.exe, le compilateur vsct, comme vous le feriez pour tout autre fichier .vsct.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer un. Fichier VSCT](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)