---
title: Fonction de SccUninitialize | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 41cb6b5cec0e0d9bb4c90cc284009ab7fc693912
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Le nettoyage s’est terminé correctement.|  
  
## <a name="remarks"></a>Notes  
 Le plug-in de contrôle de code source est chargé pour la préparation de s’arrêter et de la libération de mémoire que le plug-in a alloué pour la structure de contexte. La fonction est appelée une fois pour chaque instance donnée d’un plug-in. Un appel à la [SccInitialize](../extensibility/sccinitialize-function.md) précède cet appel. Aucun projet ne peut toujours être ouvert au moment de l’appel à `SccUninitialize`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)