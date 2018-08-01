---
title: WriteContextTLogs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a01dbd11411204affa082bfa0772530662657853
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230797"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
Écrit des fichiers journaux pour le contexte actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `intermediateDirectory`  
 Répertoire où stocker le journal de suivi.  
  
 [in] `tlogRootName`  
 Nom racine du nom du fichier journal.  
  
## <a name="return-value"></a>Valeur de retour  
 **HRESULT** avec le bit **SUCCEEDED** défini si le contexte de suivi a été créé.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** *FileTracker.h*  
  
## <a name="see-also"></a>Voir aussi  
 [WriteAllTLogs](../msbuild/writealltlogs.md)