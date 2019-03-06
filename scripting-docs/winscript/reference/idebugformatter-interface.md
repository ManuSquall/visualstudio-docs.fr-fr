---
title: Interface IDebugFormatter | Microsoft Docs
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
ms.openlocfilehash: 353a85ab51252c92086fa478d95b2e29ab3db62d
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348033"
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