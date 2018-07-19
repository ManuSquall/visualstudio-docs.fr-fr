---
title: Scriptlanguageversion, énumération | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cee2966b326ca7b4c258ffdb85b6fa71d90992
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734069"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION, énumération
Spécifie le possible des versions de script.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Valeurs d’énumération  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|La version par défaut. La valeur entière est 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Les scripts de Windows version 5.7. La valeur entière est 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Les scripts de Windows version 5.8. La valeur entière est 2.|  
|SCRIPTLANGUAGEVERSION_MAX|La version maximale. La valeur entière est 255.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de script actives, énumérations et codes d’erreur](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)