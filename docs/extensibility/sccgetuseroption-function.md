---
title: Fonction SccGetUserOption | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15af3d1711453c17a9e88c392f451161131d5b3d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017004"
---
# <a name="sccgetuseroption-function"></a>Fonction SccGetUserOption
Cette fonction récupère une variété d’options spécifiques à l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pContext  
 [in] Le pointeur de contexte de plug-in de contrôle de code source.  
  
 nOption  
 [in] Option permettant de récupérer (consultez la section Notes pour les options possibles).  
  
 lpVal  
 [out] Valeur associée d’option.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Option a été récupérée avec succès.|  
|SCC_E_OPNOTSUPPORTED|Option n’est pas prise en charge.|  
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée s'est produite.|  
  
## <a name="remarks"></a>Notes  
 Les options suivantes sont prises en charge par cette commande :  
  
|Option de l’utilisateur|Description|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Détermine si l’utilisateur souhaite extraire la version locale de fichiers. `lpVal` est affecté `SCC_USEROPT_COLV_YES` (utilisateur souhaite extraire des fichiers locaux) ou `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Codes d’erreur](../extensibility/error-codes.md)