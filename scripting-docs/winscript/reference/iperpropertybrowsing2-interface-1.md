---
title: IPerPropertyBrowsing2 (Interface) 1 | Documents Microsoft
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
ms.openlocfilehash: 75a0a7ef30bca2205789a63ea577808c11582791
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728389"
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2 (Interface) 1
Accès les informations contenues dans les pages de propriétés offertes par un objet.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
  
|Méthode|Description|  
|------------|-----------------|  
|`GetDisplayString`|Retourne une chaîne de texte qui décrit la propriété spécifiée.|  
|`MapPropertyToPage`|Retourne le CLSID de la page de propriétés qui permet la manipulation de la propriété spécifiée.|  
|`GetPredefinedStrings`|Retourne un tableau de nombres de chaînes (`LPOLESTR` pointeurs) qui répertorie les descriptions des valeurs autorisées acceptant la propriété spécifiée.|  
|`SetPredefinedValue`|Définit la valeur de la propriété la valeur prédéfinie identifié par le jeton`dwCookie.`|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : dbgprop.h