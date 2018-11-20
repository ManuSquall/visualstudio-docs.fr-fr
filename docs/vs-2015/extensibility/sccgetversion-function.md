---
title: Fonction SccGetVersion | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16a21ab75c8390f0bb5ff5f016f2bf5b8d04c3a3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779084"
---
# <a name="sccgetversion-function"></a>Fonction SccGetVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette fonction obtient le numéro de version de l’API de plug-in de contrôle de Source pris en charge par le plug-in de contrôle de code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="return-value"></a>Valeur de retour  
 Un `LONG` type de données qui contient le numéro de version de l’API de plug-in de contrôle de Source pris en charge :  
  
|WORD|Description|  
|----------|-----------------|  
|HIWORD|Version principale|  
|LOWORD|Version mineure|  
  
## <a name="remarks"></a>Notes  
 Par exemple, si un plug-in de contrôle de code source prend en charge la version 1.3 de l’API de plug-in de contrôle de Source, cette fonction retournait 0x0103.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’API du plug-in de contrôle de code source](../extensibility/source-control-plug-in-api-functions.md)

