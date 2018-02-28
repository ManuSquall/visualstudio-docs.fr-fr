---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e07d52eca9434acc7e54f3b35b111cf12af0a871
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Permet à l’appelant à remplir une zone de liste avec un tableau de nombres des pointeurs de chaîne qui représentent les valeurs possibles pour cette propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dispid`  
 [in] Identificateur de dispatch de la propriété pour laquelle l’appelant demande la liste de chaînes.  
  
 `pCaStrings`  
 [out] Pointeur vers une structure de tableau alloué par l’appelant, de nombres qui contient le nombre d’éléments et l’adresse d’un tableau alloué par la méthode de pointeurs de chaîne. Si la méthode échoue, aucune mémoire est allouée et le contenu de la structure n’est pas défini.  
  
 `pCaCookies`  
 [out] Pointeur vers la structure de tableau alloué par l’appelant, de nombres qui contient le nombre d’éléments et l’adresse d’un tableau alloué par la méthode de valeurs de type DWORD. Si la méthode échoue, aucune mémoire est allouée et le contenu de la structure n’est pas défini.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un élément valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)