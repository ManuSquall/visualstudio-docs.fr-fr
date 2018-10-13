---
title: marker_series::write_flag, méthode | Microsoft Docs
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
- cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a5e44b0f544f5f1dc0c27fb11e865baa5881662
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49249637"
---
# <a name="markerserieswriteflag-method"></a>marker_series::write_flag, méthode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Écrit un indicateur dans le fichier de trace du visualiseur concurrentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void write_flag(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `_Format`  
 Chaîne de mise en forme composite contenant du texte associé à zéro, un ou plusieurs éléments de mise en forme qui correspondent aux objets de la liste d’arguments.  
  
 `_Importance`  
 Niveau d’importance.  
  
 `_Category`  
 Catégorie.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête** : cvmarkersobj.h  
  
 **Espace de noms** : Concurrency::diagnostic  
  
## <a name="see-also"></a>Voir aussi  
 [marker_series, classe](../profiling/marker-series-class.md)



