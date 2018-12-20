---
title: CvCreateMarkerSeriesWithCodePageA, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c25877a3ab54f70207103a2c909163807b4c2e4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740143"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA, fonction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



