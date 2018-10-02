---
title: CvWriteFlag, fonction | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f23935231628687900231da344d51c432944114b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506902"
---
# <a name="cvwriteflag-function"></a>CvWriteFlag, fonction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [cvwriteflag, fonction](https://docs.microsoft.com/visualstudio/profiling/cvwriteflag-function).  
  
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
 Liste d’arguments.  
  
 `category`  
 Catégorie.  
  
 `level`  
 Niveau d’importance.  
  
 `pMarkerSeries`  
 Contexte valide de la série de marqueurs. Ne peut pas être Null.  
  
 `pMessage`  
 Chaîne de format de message. Ne peut pas être Null.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK lorsque le message est correctement écrit. Code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête** : cvmarkers.h  
  
 **Unicode** : CvWriteFlagExW, CvWriteFlagExVW  
  
 **ANSI** : CvWriteFlagExA, CvWriteFlagExVA  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)



