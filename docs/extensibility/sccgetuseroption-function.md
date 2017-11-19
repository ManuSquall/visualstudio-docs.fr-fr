---
title: Fonction de SccGetUserOption | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGetUserOption
helpviewer_keywords: SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ebd59cfada6064d40fe48df3cba4eaac3c3293b5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="sccgetuseroption-function"></a>SccGetUserOption (fonction)
Cette fonction récupère les diverses options spécifiques à l’utilisateur.  
  
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
 [in] Le pointeur de contexte plug-in de contrôle de code source.  
  
 nOption  
 [in] Option de récupération (pour les options possibles, consultez la section Notes).  
  
 lpVal  
 [out] Valeur associée d’option.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Option a été récupérée avec succès.|  
|SCC_E_OPNOTSUPPORTED|Option n’est pas prise en charge.|  
|SCC_E_NONSPECIFICERROR|Une erreur non spécifiée s'est produite.|  
  
## <a name="remarks"></a>Remarques  
 Les options suivantes sont prises en charge par cette commande :  
  
|Option de l’utilisateur|Description|  
|-----------------|-----------------|  
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Détermine si l’utilisateur souhaite extraire la version locale de fichiers. `lpVal`est affecté `SCC_USEROPT_COLV_YES` (l’utilisateur souhaite extraire des fichiers locaux) ou `SCC_USEROPT_COLV_NO`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [Codes d’erreur](../extensibility/error-codes.md)