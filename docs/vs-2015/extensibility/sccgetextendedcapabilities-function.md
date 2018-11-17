---
title: Fonction SccGetExtendedCapabilities | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b84565713edda09c029d6565e0fdbfdfa11e7d42
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809530"
---
# <a name="sccgetextendedcapabilities-function"></a>Fonction SccGetExtendedCapabilities
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction retourne des fonctionnalités supplémentaires prises en charge par le plug-in de contrôle de code source.  
  
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
 [in] Le pointeur de contexte de plug-in de contrôle de code source.  
  
 lSccExCaps  
 [in] Un indicateur qui spécifie une fonctionnalité étendue pour laquelle effectuer un test (voir le tableau de Code de fonctionnalité étendue dans [indicateurs de capacité](../extensibility/capability-flags.md) pour les indicateurs possibles).  
  
 pbSupported  
 [out] Retourne zéro (`TRUE`) si la fonctionnalité spécifiée est prise en charge ; sinon, retourne la valeur zéro (`FALSE`).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Opération de fonctionnalité de récupération s’est terminée correctement.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Erreur inconnue ou non spécifiée s’est produite.|  
  
## <a name="remarks"></a>Notes  
 Cette méthode est appelée à la demande ; Autrement dit, quand une fonctionnalité doit être testée, cette méthode est appelée pour déterminer si la prise en charge de fonctionnalité. Seul l’indicateur à la fois est spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Codes d’erreur](../extensibility/error-codes.md)   
 [Indicateurs de capacité](../extensibility/capability-flags.md)

