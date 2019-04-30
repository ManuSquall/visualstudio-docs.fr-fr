---
title: Interface ICanHandleException | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ICanHandleException interface
ms.assetid: 32df7f81-557d-40cf-a844-06a6eaa292f3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 363a52cfeb409d293ba3589b9d869bbc4fdf5918
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991346"
---
# <a name="icanhandleexception-interface"></a>ICanHandleException, interface
Permet à l’appelant d’un moteur de script pour spécifier quelles exceptions l’appelant handles.  
  
## <a name="methods"></a>Méthodes  
 Outre les méthodes héritées de `IUnknown`, le `ICanHandleException` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[ICanHandleException::CanHandleException](../../winscript/reference/icanhandleexception-canhandleexception.md)|Détermine si l’appelant du moteur de script peut gérer une exception spécifiée.|