---
title: CvWriteFlag, fonction | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvWriteFlagExVA
- cvmarkers/CvWriteFlagExW
- cvmarkers/CvWriteFlagExVW
- cvmarkers/CvWriteFlagExA
helpviewer_keywords:
- CvWriteFlagExW method
- CvWriteFlagExVA method
- CvWriteFlagExA method
- CvWriteFlagExVW method
ms.assetid: ee9da1e2-7b34-4cba-81e2-215d25d32e4d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bea5e2acea9a89c5a3b2fdfba441530a74ad8515
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177739"
---
# <a name="cvwriteflag-function"></a>CvWriteFlag, fonction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Écrit un indicateur dans le fichier de trace du visualiseur concurrentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CvWriteFlagExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteFlagExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `argList`  
 Liste d'arguments.  
  
 `category`  
 Catégorie.  
  
 `level`  
 Niveau d’importance.  
  
 `pMarkerSeries`  
 Contexte valide de la série de marqueurs. Ne peut pas avoir la valeur NULL.  
  
 `pMessage`  
 Chaîne de format de message. Ne peut pas avoir la valeur NULL.  
  
## <a name="return-value"></a>Valeur renvoyée  
 S_OK lorsque le message est correctement écrit. Code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête** : cvmarkers.h  
  
 **Unicode** : CvWriteFlagExW, CvWriteFlagExVW  
  
 <strong>ANSI</strong> : CvWriteFlagExA, CvWriteFlagExVA  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)
