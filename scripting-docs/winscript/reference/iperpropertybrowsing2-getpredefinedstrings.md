---
title: 'IPerPropertyBrowsing2 :: GetPredefinedStrings | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55ade724dd9ee5d59feb9d04c5b525ca839a9cec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576770"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Permet à l’appelant de remplir une zone de liste avec un tableau compté de pointeurs de chaîne qui représentent les valeurs potentielles de cette propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dispid`  
 dans Identificateur de dispatch de la propriété pour laquelle l’appelant demande la liste de chaînes.  
  
 `pCaStrings`  
 à Pointeur vers une structure de tableau compté, allouée par l’appelant, qui contient le nombre d’éléments et l’adresse d’un tableau alloué par méthode de pointeurs de chaîne. Si la méthode échoue, aucune mémoire n’est allouée et le contenu de la structure n’est pas défini.  
  
 `pCaCookies`  
 à Pointeur vers la structure de tableau compté, allouée par l’appelant, qui contient le nombre d’éléments et l’adresse d’un tableau alloué par méthode de DWORDs. Si la méthode échoue, aucune mémoire n’est allouée et le contenu de la structure n’est pas défini.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un `HRESULT` valide, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)