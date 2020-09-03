---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 449c6c1ecdb0644b9b52b6ec12ce867dc34d66c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156098"
---
# <a name="dont_save_vsglog_to_temp"></a>DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Définit par sa présence si le fichier journal graphique est enregistré dans le répertoire des fichiers temporaires de l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Valeur  
 Symbole de préprocesseur dont la présence ou l’absence détermine si le fichier journal de graphisme est enregistré dans le répertoire des fichiers temporaires de l’utilisateur. Si ce symbole est défini, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire actif de l’application capturée, ou est un chemin d’accès absolu ; sinon, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire de fichiers temporaires de l’utilisateur et ne peut pas être un chemin d’accès absolu.  
  
## <a name="remarks"></a>Notes  
 En fonction des privilèges de l’utilisateur, il se peut que le fichier journal de graphisme ne puisse pas être enregistré dans un emplacement arbitraire. Nous vous recommandons d’enregistrer les journaux de graphisme dans le répertoire des fichiers temporaires de l’utilisateur, ou un autre emplacement connu, si vous ne savez pas si l’utilisateur peut écrire l’emplacement que vous choisissez.  
  
 Pour empêcher l’enregistrement du fichier journal de graphisme dans le répertoire de fichiers temporaires, vous devez définir `DONT_SAVE_VSGLOG_TO_TEMP` avant d’inclure `vsgcapture.h` .  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment enregistrer le fichier journal de graphisme dans un chemin d’accès absolu sur l’ordinateur hôte.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
