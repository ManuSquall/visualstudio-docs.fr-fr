---
title: Énumération SCRIPTLANGUAGEVERSION | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 58aa904a-e3ed-41c6-82d6-e91c8279a792
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 802a9f31cc7e3497c5e5fc54395d988552f75e84
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574362"
---
# <a name="scriptlanguageversion-enumeration"></a>SCRIPTLANGUAGEVERSION, énumération
Spécifie les versions de script possibles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum tagSCRIPTLANGUAGEVERSION{    SCRIPTLANGUAGEVERSION_DEFAULT = 0,    SCRIPTLANGUAGEVERSION_5_7  = 1,    SCRIPTLANGUAGEVERSION_5_8  = 2,    SCRIPTLANGUAGEVERSION_MAX  = 255} SCRIPTLANGUAGEVERSION ;  
```  
  
## <a name="enumeration-values"></a>Valeurs d’énumération  
  
|||  
|-|-|  
|SCRIPTLANGUAGEVERSION_DEFAULT|Version par défaut. La valeur entière est 0.|  
|SCRIPTLANGUAGEVERSION_5_7|Windows Scripting version 5,7. La valeur entière est 1.|  
|SCRIPTLANGUAGEVERSION_5_8|Windows Scripting version 5,8. La valeur entière est 2.|  
|SCRIPTLANGUAGEVERSION_MAX|Version maximale. La valeur entière est 255.|  
  
## <a name="see-also"></a>Voir aussi  
 [Constantes de script actives, énumérations et codes d’erreur](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)