---
title: Copier (Capture par programmation) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca2d6afc3a5693896c17e49ccb07b5152d906d43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776146"
---
# <a name="copy-programmatic-capture"></a>Copier (capture par programmation)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Copie le contenu du fichier journal (.vsglog) tracé actif dans un nouveau fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szNewVSGLog`  
 Le nom de fichier du nouveau fichier journal graphics.  
  
## <a name="remarks"></a>Notes  
 Pour copier les informations graphiques dans un nouveau fichier, doit déjà avoir capturé des informations graphiques ; Sinon, rien ne se produit.



