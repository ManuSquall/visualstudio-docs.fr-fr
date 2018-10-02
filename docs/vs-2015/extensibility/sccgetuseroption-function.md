---
title: Fonction SccGetUserOption | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 567dbf987887d203a811a1dc965ecd4a472d5641
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505859"
---
# <a name="sccgetuseroption-function"></a>Fonction SccGetUserOption
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [fonction SccGetUserOption](https://docs.microsoft.com/visualstudio/extensibility/sccgetuseroption-function).  
  
Cette fonction récupère une variété d’options spécifiques à l’utilisateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccGetUserOption(  
   LPVOID pContext,  
   LONG nOption,  
   LPLONG lpVal  
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

