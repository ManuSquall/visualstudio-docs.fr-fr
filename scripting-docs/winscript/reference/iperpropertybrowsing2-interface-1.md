---
title: L’Interface 1 IPerPropertyBrowsing2 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bded7159b72fc8c1ae8408611ce858105e6734da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344024"
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2 (Interface) 1
Les accès les informations contenues dans les pages de propriétés offertes par un objet.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|`GetDisplayString`|Retourne une chaîne de texte décrivant la propriété spécifiée.|  
|`MapPropertyToPage`|Retourne le CLSID de la page de propriétés qui permet la manipulation de la propriété spécifiée.|  
|`GetPredefinedStrings`|Retourne un tableau compté de chaînes (`LPOLESTR` pointeurs) répertoriant les descriptions des valeurs autorisées capable d’accepter la propriété spécifiée.|  
|`SetPredefinedValue`|Définit la valeur de la propriété à la valeur prédéfinie identifiée par le jeton `dwCookie.`|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : dbgprop.h