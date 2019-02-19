---
title: WriteAllTLogs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- WriteAllTLogs
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3d5e51a674a075b265aa6ec2550f4e8cf4207c5d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804752"
---
# <a name="writealltlogs"></a>WriteAllTLogs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Écrit les journaux de suivi pour tous les threads et tous les contextes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `intermediateDirectory`  
 Répertoire où stocker le journal de suivi.  
  
 [in] `tlogRootName`  
 Nom racine du nom du fichier journal.  
  
## <a name="return-value"></a>Valeur de retour  
 [HRESULT](<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) avec le bit [SUCCEEDED](<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) défini si le contexte de suivi a été créé.  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** FileTracker.h  
  
## <a name="see-also"></a>Voir aussi  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)
