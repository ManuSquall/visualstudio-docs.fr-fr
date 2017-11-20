---
title: Fonction de SccUninitialize | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccUninitialize
helpviewer_keywords: SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 434987489feccd5f576e04d69afbb4b39e1dc754
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="sccuninitialize-function"></a>SccUninitialize (fonction)
Cette fonction nettoie toutes les allocations ou les connexions ouvertes créées par un appel précédent à la [SccInitialize](../extensibility/sccinitialize-function.md) en préparation de l’arrêt du plug-in de contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] Le pointeur vers la structure de contexte plug-in de contrôle de code source est créé dans le [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Le nettoyage s’est terminé correctement.|  
  
## <a name="remarks"></a>Remarques  
 Le plug-in de contrôle de code source est chargé pour la préparation de s’arrêter et de la libération de mémoire que le plug-in a alloué pour la structure de contexte. La fonction est appelée une fois pour chaque instance donnée d’un plug-in. Un appel à la [SccInitialize](../extensibility/sccinitialize-function.md) précède cet appel. Aucun projet ne peut toujours être ouvert au moment de l’appel à `SccUninitialize`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)