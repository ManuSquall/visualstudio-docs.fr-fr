---
title: Script actif, constantes, énumérations et Codes d’erreur | Documents Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb4165a5471c8e79827f0f7605cef575e82bab75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641569"
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Script actif, constantes, énumérations et codes d'erreur
Cette section décrit les énumérations et les codes d’erreur utilisés dans les moteurs de scripts Windows.  
  
## <a name="constants"></a>Constantes  
  
|Constante|Description|  
|--------------|-----------------|  
|[Constantes SCRIPTTHREADID](../../winscript/reference/scriptthreadid-constants.md)|Spécifie le type de thread.|  
  
## <a name="properties"></a>Propriétés  
  
|Propriété|Description|  
|--------------|-----------------|  
|[Propriété SCRIPTPROP_HOSTKEEPALIVE](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Permet de spécifier si le moteur de script doit être conservé entièrement fonctionnel, s’il existe des références en attente.|  
  
## <a name="enumerations"></a>Énumérations  
  
|Énumération|Description|  
|-----------------|-----------------|  
|[Énumération SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md)|Le type de garbage collection à effectuer.|  
|[Énumération SCRIPTLANGUAGEVERSION](../../winscript/reference/scriptlanguageversion-enumeration.md)|Spécifie le possible des versions de script.|  
|[Énumération SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md)|Spécifie l’état d’un moteur de script.|  
|||  
|[Énumération SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md)|Spécifie l’état d’un thread dans un moteur de script.|  
|[Énumération SCRIPTTRACEINFO](../../winscript/reference/scripttraceinfo-enumeration.md)|Représente l’événement de script qui est tracée. Utilisé dans le [iactivescriptsitetraceinfo::sendscripttraceinfo, méthode](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[Énumération SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md)|Représente la façon dont le contrôle d’interface utilisateur doit-elle être traité.|  
|[Énumération SCRIPTUICITEM](../../winscript/reference/scriptuicitem-enumeration.md)|Représente le type d’élément d’interface utilisateur. Utilisé dans le [iactivescriptsiteuicontrol::getuibehavior, méthode](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Codes d'erreur  
  
|Code d'erreur|Description|  
|----------------|-----------------|  
|[Code d’erreur SCRIPT_E_PROPAGATE](../../winscript/reference/script-e-propagate-error-code.md)|Une erreur de script est propagée à l’appelant, qui peut être dans un autre thread.|  
|[Code d’erreur SCRIPT_E_RECORDED](../../winscript/reference/script-e-recorded-error-code.md)|Une erreur a été passée entre le moteur de script et l’hôte.|  
|[Code d’erreur SCRIPT_E_REPORTED](../../winscript/reference/script-e-reported-error-code.md)|Le moteur de script a signalé une exception non gérée à l’hôte.|  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de script actives](../../winscript/reference/active-script-interfaces.md)