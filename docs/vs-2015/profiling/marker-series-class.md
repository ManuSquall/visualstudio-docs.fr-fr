---
title: marker_series, classe | Microsoft Docs
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
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 18967d9f89f701dd02feb70670147db3f1275978
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493745"
---
# <a name="markerseries-class"></a>marker_series, classe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [marker_series, classe](https://docs.microsoft.com/visualstudio/profiling/marker-series-class).  
  
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
 [diagnostic, espace de noms](../profiling/diagnostic-namespace.md)



