---
title: marker_series, classe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series class
ms.assetid: b8445ed0-c512-4f92-b6b4-3d05c044f939
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 155d47f6764e754a1093cbcf884368c80d709a2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575915"
---
# <a name="markerseries-class"></a>marker_series, classe
Représente un canal série d’événements générés par un fournisseur unique.

## <a name="syntax"></a>Syntaxe

```cpp
class marker_series;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Name|Description|
|----------|-----------------|
|[marker_series::marker_series, constructeur](../profiling/marker-series-marker-series-constructor.md)|Initialise une nouvelle instance de la classe `marker_series`.|
|[marker_series::~marker_series, destructeur](../profiling/marker-series-tilde-marker-series-destructor.md)|Détruit l’objet marker_series et libère toutes les ressources allouées.|

### <a name="public-methods"></a>Méthodes publiques

|Name|Description|
|----------|-----------------|
|[marker_series::is_enabled, méthode](../profiling/marker-series-is-enabled-method.md)|Détermine si une session a activé le fournisseur.|
|[marker_series::write_alert, méthode](../profiling/marker-series-write-alert-method.md)|Écrit une alerte dans le fichier de trace du visualiseur concurrentiel.|
|[marker_series::write_flag, méthode](../profiling/marker-series-write-flag-method.md)|Écrit un indicateur dans le fichier de trace du visualiseur concurrentiel.|
|[marker_series::write_message, méthode](../profiling/marker-series-write-message-method.md)|Écrit un message dans le fichier de trace du visualiseur concurrentiel.|

## <a name="inheritance-hierarchy"></a>Hiérarchie d’héritage
 `marker_series`

## <a name="requirements"></a>Spécifications
 **En-tête :** *cvmarkersobj.h*

 **Espace de noms :** Concurrency::diagnostic

## <a name="see-also"></a>Voir aussi
- [diagnostic, espace de noms](../profiling/diagnostic-namespace.md)