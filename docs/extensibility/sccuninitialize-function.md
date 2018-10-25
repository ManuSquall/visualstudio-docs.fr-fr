---
title: Fonction SccUninitialize | Microsoft Docs
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
ms.openlocfilehash: e9d992428dd6358cee2b6a46efc0816e7840c449
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948029"
---
# <a name="sccuninitialize-function"></a>Fonction SccUninitialize
Cette fonction nettoie les allocations ou des connexions ouvertes créées par un appel précédent à la [SccInitialize](../extensibility/sccinitialize-function.md) en préparation pour arrêter le plug-in de contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] Le pointeur vers la structure de contexte de plug-in de contrôle de source créé dans le [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Le nettoyage s’est terminé correctement.|  
  
## <a name="remarks"></a>Notes  
 Le plug-in de contrôle de code source est chargé pour la préparation d’être arrêté et de libération de mémoire que le plug-in a allouée pour la structure de contexte. La fonction est appelée une fois pour chaque instance donnée d’un plug-in. Un appel à la [SccInitialize](../extensibility/sccinitialize-function.md) précède cet appel. Aucun projet n’est toujours ne possible d’ouvrir au moment de l’appel à `SccUninitialize`.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API de plug-in de contrôle de source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)