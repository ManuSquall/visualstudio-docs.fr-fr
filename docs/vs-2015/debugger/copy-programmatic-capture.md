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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ec5c95a2419e465f93f7d11045672de2f1b0174
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293187"
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



