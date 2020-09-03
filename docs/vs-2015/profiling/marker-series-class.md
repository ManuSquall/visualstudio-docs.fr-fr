---
title: marker_series, classe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cb199d74ade593d0bc8318c27bc96ffbf70e4dcf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194934"
---
# <a name="marker_series-class"></a>marker_series, classe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Représente un canal série d’événements générés par un fournisseur unique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class marker_series;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[marker_series::marker_series, constructeur](../profiling/marker-series-marker-series-constructor.md)|Initialise une nouvelle instance de la classe `marker_series`.|  
|[marker_series::~marker_series, destructeur](../profiling/marker-series-tilde-marker-series-destructor.md)|Détruit l’objet marker_series et libère toutes les ressources allouées.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[marker_series::is_enabled, méthode](../profiling/marker-series-is-enabled-method.md)|Détermine si une session a activé le fournisseur.|  
|[marker_series::write_alert, méthode](../profiling/marker-series-write-alert-method.md)|Écrit une alerte dans le fichier de trace du visualiseur concurrentiel.|  
|[marker_series::write_flag, méthode](../profiling/marker-series-write-flag-method.md)|Écrit un indicateur dans le fichier de trace du visualiseur concurrentiel.|  
|[marker_series::write_message, méthode](../profiling/marker-series-write-message-method.md)|Écrit un message dans le fichier de trace du visualiseur concurrentiel.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `marker_series`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête** : cvmarkersobj.h  
  
 **Espace de noms** : Concurrency::diagnostic  
  
## <a name="see-also"></a>Voir aussi  
 [Espace de noms diagnostic](../profiling/diagnostic-namespace.md)
