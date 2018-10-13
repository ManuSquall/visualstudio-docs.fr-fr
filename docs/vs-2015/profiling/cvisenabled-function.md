---
title: CvIsEnabled, fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4349d42309482622ae57ba27bb3e675bbdd6a403
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222467"
---
# <a name="cvisenabled-function"></a>CvIsEnabled, fonction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Détermine si une session a activé le fournisseur ETW spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `category`  
 Catégorie.  
  
 `level`  
 Niveau d’importance.  
  
 `pProvider`  
 Objet fournisseur valide. Ne peut pas être Null.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si le fournisseur est activé. S_FALSE si le fournisseur est désactivé. Code d’erreur en cas d’erreur. Utilisez la macro FAILED pour vérifier la condition d’erreur, puis recherchez S_OK/S_FALSE.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête** : cvmarkers.h  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)



