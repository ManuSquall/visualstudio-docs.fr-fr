---
title: IDebugFormatter (Interface) | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 97f95aa1ecb91f6caca187939a79a6f09cd2108f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729169"
---
# <a name="idebugformatter-interface"></a>IDebugFormatter, interface
Permet à un langage ou un IDE pour personnaliser la conversion entre les valeurs de type VARIANT ou types VARTYPE et les chaînes.  
  
 Outre les méthodes héritées de `IUnknown`, le `IDebugFormatter` interface expose les méthodes suivantes.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Retourne une chaîne qui représente la valeur de type VARIANT donnée.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Retourne une valeur VARIANT contenant la chaîne donnée.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Retourne une chaîne qui représente la valeur VARTYPE spécifiée.|