---
title: DONT_SAVE_VSGLOG_TO_TEMP | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b70ddf2933b8bd2d96db1636612cb35a6a759a1a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Définit par sa présence si le fichier journal graphique est enregistré dans le répertoire des fichiers temporaires de l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Value  
 Un symbole de préprocesseur qui, par sa présence ou l’absence, détermine si les graphiques le fichier journal est enregistré dans le répertoire des fichiers temporaires de l’utilisateur. Si ce symbole est défini, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire en cours de l’application capturée, ou est un chemin d’accès absolu ; sinon, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire des fichiers temporaires de l’utilisateur et ne peut pas être chemin d’accès absolu.  
  
## <a name="remarks"></a>Notes  
 En fonction des privilèges de l’utilisateur, le fichier journal de graphisme n’est peut-être pas en mesure d’être enregistré dans un emplacement arbitraire. Nous recommandons que vous préférez enregistrer des journaux de graphisme à un répertoire de fichiers temporaires de l’utilisateur ou un autre emplacement vérifié, si vous ne savez pas si l’emplacement que vous choisissez n’est possible par l’utilisateur.  
  
 Pour empêcher le fichier journal de graphisme ne sont pas enregistrées dans le répertoire de fichiers temporaires, vous devez défini `DONT_SAVE_VSGLOG_TO_TEMP` avant d’inclure `vsgcapture.h`.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment enregistrer le fichier journal de graphisme à un chemin d’accès absolu sur l’ordinateur hôte.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)