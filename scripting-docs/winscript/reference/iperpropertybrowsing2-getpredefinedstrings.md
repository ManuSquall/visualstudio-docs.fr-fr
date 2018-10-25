---
title: IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a60225e69a04399a3ff0160291b84e9f3fda513c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915959"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
Permet à l’appelant à remplir une zone de liste avec un tableau compté de pointeurs de chaîne qui représentent les valeurs possibles pour cette propriété.  
  
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
 [out] Pointeur vers une structure de tableau alloué par l’appelant, compté qui contient le nombre d’éléments et l’adresse d’un tableau alloué à la méthode de pointeurs de chaîne. Si la méthode échoue, aucune mémoire est allouée, et le contenu de la structure n’est pas défini.  
  
 `pCaCookies`  
 [out] Pointeur vers la structure de tableau alloué par l’appelant, compté qui contient le nombre d’éléments et l’adresse d’un tableau alloué à la méthode de valeurs de type DWORD. Si la méthode échoue, aucune mémoire est allouée, et le contenu de la structure n’est pas défini.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une liste valide `HRESULT`, généralement `S_OK`.  
  
## <a name="see-also"></a>Voir aussi  
 [Interface 1 IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)