---
title: VSG_DEFAULT_RUN_FILENAME | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f7fe31b96911329089174772094784c0d0f3371c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
Définit le nom de fichier par défaut du fichier journal graphique.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Paramètres  
 `filename`  
 Le nom de fichier attribué par défaut pour le fichier journal de graphisme lorsque les informations graphiques sont capturées par programme.  
  
## <a name="value"></a>Value  
 Fichier journal d’une chaîne littérale qui représente le nom de fichier de graphiques. Par défaut, L"default.vsglog ».  
  
```C++  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Notes  
 Si le symbole de préprocesseur `DONT_SAVE_VSGLOG_TO_TEMP` est défini, puis le nom de fichier est relatif au répertoire en cours de l’application capturée, ou est un chemin d’accès absolu ; sinon, il est relatif au répertoire des fichiers temporaires de l’utilisateur et ne peut pas être un chemin d’accès absolu.  
  
 Pour modifier le nom de fichier défini, vous devez redéfinir avant d’inclure `vsgcapture.h` dans votre programme.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment modifier le nom de fichier du fichier de capture par défaut :  
  
```C++  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)