---
title: CvIsEnabled, fonction | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ba30f3ab75504c0115b8a881f2014910f3b9fd0b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770996"
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
  
## <a name="requirements"></a>Spécifications  
 **En-tête** : cvmarkers.h  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la bibliothèque C++](../profiling/cpp-library-reference.md)
