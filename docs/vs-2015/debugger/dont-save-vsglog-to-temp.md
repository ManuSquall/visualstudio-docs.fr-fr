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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156098"
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Définit par sa présence si le fichier journal graphique est enregistré dans le répertoire des fichiers temporaires de l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Valeur  
 Un symbole de préprocesseur qui détermine si du fichier journal des graphiques par sa présence ou l’absence est enregistré dans le répertoire des fichiers temporaires de l’utilisateur. Si ce symbole est défini, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire actif de l’application capturée, soit un chemin d’accès absolu ; sinon, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire des fichiers temporaires de l’utilisateur et ne peut pas être un chemin d’accès absolu.  
  
## <a name="remarks"></a>Notes  
 En fonction des privilèges de l’utilisateur, le fichier journal de graphisme n’est peut-être pas pu être enregistrés dans un emplacement arbitraire. Nous recommandons que vous préférez enregistrer des journaux de graphisme au répertoire des fichiers temporaires de l’utilisateur ou un autre emplacement correct, si vous ne savez pas si l’emplacement que vous choisiriez peut être écrites dans par l’utilisateur.  
  
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
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
