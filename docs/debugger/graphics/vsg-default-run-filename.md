---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af34aed1ed99e1d8e51e594a514286caa7adf748
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979918"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
Définit le nom de fichier par défaut du fichier journal graphique.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Paramètres  
 `filename`  
 Le nom de fichier donné par défaut pour le fichier journal de graphisme lorsque les informations graphiques sont capturées par programmation.  
  
## <a name="value"></a>Value  
 Une chaîne littérale qui représente le nom de fichier des graphiques de fichier journal. Par défaut, L"default.vsglog ».  
  
```C++  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Remarques  
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