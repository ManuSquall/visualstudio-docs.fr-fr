---
title: CvInitProvider, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 78b7fbb6480f0793b1641159cd3f06c471907603
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750101"
---
# <a name="cvinitprovider-function"></a>CvInitProvider, fonction
Initialise le fournisseur de marqueurs. Doit être appelée avant toute autre fonction du kit SDK du visualiseur concurrentiel.  
  
## <a name="syntax"></a>Syntaxe  
  
```C  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pGuid`  
 GUID du fournisseur. Ne peut pas être Null.  
  
 `ppProvider`  
 Adresse d’une variable de sortie qui doit stocker le contexte du fournisseur. Ne peut pas être Null.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK lorsque le fournisseur est correctement initialisé, ou code d’erreur en cas d’erreur. Utilisez les macros SUCCEEDED/FAILED pour vérifier la condition d’erreur.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** *cvmarkers.h*  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)