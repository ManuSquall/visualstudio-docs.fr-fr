---
title: Fonction de SccGetExtendedCapabilities | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: c0331979eaae065730dab5d5daf0e226844d5e7a
ms.lasthandoff: 02/22/2017

---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities (fonction)
Cette fonction renvoie des fonctionnalités supplémentaires prises en charge par le plug-in de contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte plug-in de contrôle de code source.  
  
 lSccExCaps  
 [in] Indicateur spécifiant une fonctionnalité étendue pour laquelle effectuer un test (voir le tableau de Code de fonctionnalité étendue de [indicateurs](../extensibility/capability-flags.md) pour les indicateurs possibles).  
  
 pbSupported  
 [out] Renvoie une valeur non zéro (`TRUE`) si la fonctionnalité spécifiée est prise en charge ; sinon, retourne zéro (`FALSE`).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée renvoyer une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|L’opération de fonctionnalité get s’est terminée correctement.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Erreur inconnue ou non spécifiée s’est produite.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée à la demande ; Autrement dit, lorsqu’une fonctionnalité doit être testé, cette méthode est appelée pour déterminer si prise en charge de la capacité. Seul indicateur à la fois est spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Codes d’erreur](../extensibility/error-codes.md)   
 [Indicateurs de capacité](../extensibility/capability-flags.md)
