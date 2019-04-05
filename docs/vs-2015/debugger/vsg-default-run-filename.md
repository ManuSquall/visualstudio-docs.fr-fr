---
title: VSG_DEFAULT_RUN_FILENAME | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ea549d2f-c857-458c-93c7-bc5a2d11d15d
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2980d34028c58a6abadb2df21bf22c8d37cda6e0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938421"
---
# <a name="vsgdefaultrunfilename"></a>VSG_DEFAULT_RUN_FILENAME
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Définit le nom de fichier par défaut du fichier journal graphique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
#define VSG_DEFAULT_FILENAME filename  
```  
  
#### <a name="parameters"></a>Paramètres  
 `filename`  
 Le nom de fichier donné par défaut pour le fichier journal de graphisme lorsque les informations graphiques sont capturées par programmation.  
  
## <a name="value"></a>Value  
 Une chaîne littérale qui représente le nom de fichier des graphiques de fichier journal. Par défaut, L"default.vsglog ».  
  
```cpp  
#define VSG_DEFAULT_FILENAME L"default.vsglog"  
```  
  
## <a name="remarks"></a>Notes  
 Si le symbole de préprocesseur `DONT_SAVE_VSGLOG_TO_TEMP` est défini, puis le nom de fichier est relatif au répertoire en cours de l’application capturée, ou est un chemin d’accès absolu ; sinon, il est relatif au répertoire des fichiers temporaires de l’utilisateur et ne peut pas être un chemin d’accès absolu.  
  
 Pour modifier le nom de fichier défini, vous devez redéfinir avant d’inclure `vsgcapture.h` dans votre programme.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment modifier le nom de fichier du fichier de capture par défaut :  
  
```cpp  
// Redefine the default capture filename before including vsgcapture.h  
#define VSG_DEFAULT_FILENAME L"capture.vsglog"  
  
#include <vsgcapture.h>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)
