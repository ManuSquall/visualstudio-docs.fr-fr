---
title: Fonction SccUninitialize | Microsoft Docs
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
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f81bb0cd478320b7fa6b5faee28e79ad1dcb0642
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736254"
---
# <a name="sccuninitialize-function"></a>Fonction SccUninitialize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction nettoie les allocations ou des connexions ouvertes créées par un appel précédent à la [SccInitialize](../extensibility/sccinitialize-function.md) en préparation pour arrêter le plug-in de contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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

