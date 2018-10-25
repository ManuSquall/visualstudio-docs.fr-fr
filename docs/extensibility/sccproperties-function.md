---
title: Fonction SccProperties | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f8067464802899ce8966d63d702679d216b6377
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875970"
---
# <a name="sccproperties-function"></a>Fonction SccProperties
Cette fonction affiche les propriétés de contrôle de source d’un fichier ou un projet.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 pvContext  
 [in] La structure de contexte de plug-in de contrôle de source.  
  
 hWnd  
 [in] Handle vers la fenêtre de l’IDE que le plug-in de contrôle de code source peut utiliser en tant que parent pour les boîtes de dialogue qu’il fournit.  
  
 lpFileName  
 [in] Le nom de chemin d’accès complet du fichier ou du projet.  
  
## <a name="return-value"></a>Valeur de retour  
 L’implémentation de plug-in de contrôle de source de cette fonction est censée retourner l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Les propriétés ont été correctement affichées.|  
|SCC_I_RELOADFILE|Le système de contrôle de version a modifié les propriétés de fichier, afin de l’IDE doit recharger ce fichier.|  
|SCC_E_PROJNOTOPEN|Le projet spécifié n’a pas été ouvert dans le contrôle de code source.|  
|SCC_E_NOTAUTHORIZED|L’utilisateur n’est pas autorisé à afficher les propriétés de ce fichier ou le projet.|  
|SCC_E_FILENOTCONTROLLED|Le fichier spécifié ou le projet n’est pas sous contrôle de code source.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Une erreur inconnue ou générale s’est produite.|  
  
## <a name="remarks"></a>Notes  
 Le plug-in de contrôle de code source affiche les propriétés dans sa propre boîte de dialogue.  
  
 Les propriétés sont définies par le plug-in de contrôle de code source et peuvent différer des plug-in pour le plug-in. Si le plug-in permet à l’utilisateur modifier les propriétés de contrôle de source d’un fichier, elle doit retourner `SCC_I_RELOAD` pour signaler l’IDE que ce fichier ou le projet doit être rechargé.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)