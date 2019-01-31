---
title: marker_series::write_flag, méthode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f70f6b357e8baaf721c751c57b21924afaff90e6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069775"
---
# <a name="markerserieswriteflag-method"></a>marker_series::write_flag, méthode
Écrit un indicateur dans le fichier de trace du visualiseur concurrentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** *cvmarkersobj.h*  
  
 **Espace de noms :** Concurrency::diagnostic  
  
## <a name="see-also"></a>Voir aussi  
 [marker_series, classe](../profiling/marker-series-class.md)