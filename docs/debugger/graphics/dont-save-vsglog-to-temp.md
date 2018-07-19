---
title: DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs
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
ms.openlocfilehash: 82726226e4ea26db0dd2cb8e37e32f9daa1869b9
ms.sourcegitcommit: 80f9daba96ff76ad7e228eb8716df3abfd115bc3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37433091"
---
# <a name="dontsavevsglogtotemp"></a>DONT_SAVE_VSGLOG_TO_TEMP
Définit par sa présence si le fichier journal graphique est enregistré dans le répertoire des fichiers temporaires de l'utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## <a name="value"></a>Value  
 Un symbole de préprocesseur qui détermine si du fichier journal des graphiques par sa présence ou l’absence est enregistré dans le répertoire des fichiers temporaires de l’utilisateur. Si ce symbole est défini, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire actif de l’application capturée, soit un chemin d’accès absolu ; sinon, le nom de fichier défini par `VSG_DEFAULT_RUN_FILENAME` est relatif au répertoire des fichiers temporaires de l’utilisateur et ne peut pas être un chemin d’accès absolu.  
  
## <a name="remarks"></a>Notes  
 En fonction des privilèges de l’utilisateur, le fichier journal de graphisme n’est peut-être pas pu être enregistrés dans un emplacement arbitraire. Nous recommandons que vous préférez enregistrer des journaux de graphisme au répertoire des fichiers temporaires de l’utilisateur ou un autre emplacement correct, si vous ne savez pas si l’emplacement que vous choisiriez peut être écrites dans par l’utilisateur.  
  
 Pour empêcher le fichier journal de graphisme ne sont pas enregistrées dans le répertoire de fichiers temporaires, vous devez défini `DONT_SAVE_VSGLOG_TO_TEMP` avant d’inclure `vsgcapture.h`.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment enregistrer le fichier journal de graphisme à un chemin d’accès absolu sur l’ordinateur hôte.  
  
```cpp
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)
