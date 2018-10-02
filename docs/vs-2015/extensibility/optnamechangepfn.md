---
title: OPTNAMECHANGEPFN | Microsoft Docs
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
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f729e00805fa1c73fe1e64197788dd31f2a2a41d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492908"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [OPTNAMECHANGEPFN](https://docs.microsoft.com/visualstudio/extensibility/optnamechangepfn).  
  
Il s’agit d’une fonction de rappel spécifiée dans un appel à la [SccSetOption](../extensibility/sccsetoption-function.md) (à l’aide d’option `SCC_OPT_NAMECHANGEPFN`) et est utilisé pour communiquer les modifications de nom apportées par le contrôle de code source plug-in à l’IDE.  
  
## <a name="signature"></a>Signature  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 pvCallerData  
 [in] Valeur de l’utilisateur spécifié dans un appel précédent à la [SccSetOption](../extensibility/sccsetoption-function.md) (à l’aide d’option `SCC_OPT_USERDATA`).  
  
 pszOldName  
 [in] Le nom d’origine du fichier.  
  
 pszNewName  
 [in] Le nom du fichier a été renommé.  
  
## <a name="return-value"></a>Valeur de retour  
 Aucun  
  
## <a name="remarks"></a>Notes  
 Si un fichier est renommé pendant une opération de contrôle de code source, le plug-in de contrôle de code source peut avertir l’IDE du changement de nom via ce rappel.  
  
 Si l’IDE ne prend pas en charge ce rappel, il n’appelle pas la [SccSetOption](../extensibility/sccsetoption-function.md) à le spécifier. Si le plug-in ne prend pas en charge ce rappel, elle retournera `SCC_E_OPNOTSUPPORTED` à partir de la `SccSetOption` lors de l’IDE tente de définir le rappel de fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)

