---
title: marker_series::write_alert, méthode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a8d6909ee08984d0bff57f993538957b8958dcf2
ms.sourcegitcommit: 269b55b413d2c82e6aa56c6ab8e53da7926fb2e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35237365"
---
# <a name="markerserieswritealert-method"></a>marker_series::write_alert, méthode
Écrit une alerte dans le fichier de trace du visualiseur concurrentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `_Format`  
 Chaîne de mise en forme composite contenant du texte associé à zéro, un ou plusieurs éléments de mise en forme qui correspondent aux objets de la liste d’arguments.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** *cvmarkersobj.h*  
  
 **Espace de noms** : Concurrency::diagnostic  
  
## <a name="see-also"></a>Voir aussi  
 [marker_series, classe](../profiling/marker-series-class.md)