---
title: IDiaFrameData::get_program | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc770db5f5cf16d9870e05ada01e235206b94078
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idiaframedatagetprogram"></a>IDiaFrameData::get_program
Récupère la chaîne de programme qui est utilisée pour calculer le Registre défini avant l’appel à la fonction actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRetVal`  
 [out] Retourne la chaîne de programme.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si cette propriété n’est pas pris en charge. Sinon, retourne un code d'erreur.  
  
## <a name="remarks"></a>Notes  
 La chaîne de programme est une séquence de macros qui est interprétée afin d’établir le prologue. Par exemple, un frame de pile classique peut utiliser la chaîne de programme `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`. Le format est la notation polonaise inverse, dans lequel les opérateurs de suivent les opérandes. `T0` représente une variable temporaire sur la pile. Cet exemple effectue les étapes suivantes :  
  
1.  Déplacer le contenu du Registre `ebp` à `T0`.  
  
2.  Ajouter `4` à la valeur de `T0` à produire une adresse, obtenir la valeur de cette adresse et stockez la valeur de Registre `eip`.  
  
3.  Obtenir la valeur de l’adresse stockée dans `T0` et enregistrer cette valeur dans le Registre `ebp`.  
  
4.  Ajouter `8` à la valeur de `T0` et enregistrer cette valeur dans le Registre `esp`.  
  
 Notez que la chaîne du programme est spécifique au processeur et à la convention d’appel défini pour la fonction représentée par le frame de pile actuel.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)