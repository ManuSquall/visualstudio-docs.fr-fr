---
title: SccUninitialize fonction) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcb0b3a6718cc90db6f7176c823ccccbbfc05f9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190851"
---
# <a name="sccuninitialize-function"></a>Fonction SccUninitialize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction nettoie toutes les allocations ou les connexions ouvertes créées par un appel précédent à [SccInitialize](../extensibility/sccinitialize-function.md) en préparation de l’arrêt du plug-in de contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
SCCRTN SccUninitialize (  
   LPVOID pvContext  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 dans Pointeur vers la structure de contexte du plug-in de contrôle de code source créée dans [SccInitialize](../extensibility/sccinitialize-function.md).  
  
## <a name="return-value"></a>Valeur renvoyée  
 L’implémentation du plug-in de contrôle de code source de cette fonction est supposée retourner l’une des valeurs suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|SCC_OK|Le nettoyage s’est terminé correctement.|  
  
## <a name="remarks"></a>Notes  
 Le plug-in de contrôle de code source est responsable de la préparation de l’arrêt et de la libération de mémoire allouée par le plug-in pour la structure de contexte. La fonction est appelée une fois pour chaque instance donnée d’un plug-in. Un appel à [SccInitialize](../extensibility/sccinitialize-function.md) précède cet appel. Aucun projet ne peut encore être ouvert au moment de l’appel à `SccUninitialize` .  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de l’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)
