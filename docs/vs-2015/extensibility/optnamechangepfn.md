---
title: OPTNAMECHANGEPFN | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4969dff811b6517c0274a35884703a9dc0c693cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194101"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il s’agit d’une fonction de rappel spécifiée dans un appel à [SccSetOption](../extensibility/sccsetoption-function.md) (option using `SCC_OPT_NAMECHANGEPFN` ) et est utilisée pour communiquer les modifications de nom apportées par le plug-in de contrôle de code source à l’IDE.  
  
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
 dans Valeur utilisateur spécifiée dans un appel précédent à [SccSetOption](../extensibility/sccsetoption-function.md) (option using `SCC_OPT_USERDATA` ).  
  
 pszOldName  
 dans Nom d’origine du fichier.  
  
 pszNewName  
 dans Nom du fichier dans lequel le fichier a été renommé.  
  
## <a name="return-value"></a>Valeur renvoyée  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 Si un fichier est renommé pendant une opération de contrôle de code source, le plug-in de contrôle de code source peut notifier l’IDE du changement de nom par le biais de ce rappel.  
  
 Si l’IDE ne prend pas en charge ce rappel, il n’appellera pas le [SccSetOption](../extensibility/sccsetoption-function.md) pour le spécifier. Si le plug-in ne prend pas en charge ce rappel, il retourne `SCC_E_OPNOTSUPPORTED` la `SccSetOption` fonction lorsque l’IDE tente de définir le rappel.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de rappel implémentées par l’IDE](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
