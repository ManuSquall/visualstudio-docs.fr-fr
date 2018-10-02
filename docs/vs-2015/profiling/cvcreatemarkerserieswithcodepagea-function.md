---
title: CvCreateMarkerSeriesWithCodePageA, fonction | Microsoft Docs
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
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3716cb41da056590a7978e49f4672d25b1bbdaae
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503503"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA, fonction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [cvcreatemarkerserieswithcodepagea, fonction](https://docs.microsoft.com/visualstudio/profiling/cvcreatemarkerserieswithcodepagea-function).  
  
Crée des séries de marqueurs pour un fournisseur donné et une page de codes spécifiée. Cette fonction peut être utilisée pour spécifier explicitement la page de codes pour le texte écrit par les fonctions ANSI API de marqueur. Il peut être utile de définir la page de codes lorsque la trace est capturée puis analysée sur plusieurs ordinateurs ayant des langues et des paramètres régionaux différents. Par défaut, c’est la page de codes retournée par la fonction GetACP() qui est utilisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pProvider`  
 Objet fournisseur précédemment initialisé par CvInitProvider. Ne peut pas être Null.  
  
 `pSeriesName`  
 Nom de la série de marqueurs. Ne peut pas être Null, mais une chaîne vide est acceptée.  
  
 `nTextCodePage`  
 Page de codes valide.  
  
 `ppMarkerSeries`  
 Adresse d’une variable de sortie qui doit stocker le contexte de la série de marqueurs. Ne peut pas être Null.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK lorsque la série de marqueurs est correctement créée, ou code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête** : cvmarkers.h  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)



