---
title: Interface IDebugFormatter | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugFormatter interface
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f35d1b811a017895ca40f3325bd0ac456070184f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979225"
---
# <a name="idebugformatter-interface"></a>IDebugFormatter, interface
Permet à un langage ou à un IDE de personnaliser la conversion entre des valeurs de type VARIANT ou des types VARTYPE et des chaînes.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugFormatter` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Retourne une chaîne qui représente la valeur de type VARIANT donnée.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Retourne une valeur VARIANT contenant la chaîne donnée.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Retourne une chaîne qui représente la valeur VARTYPE donnée.|