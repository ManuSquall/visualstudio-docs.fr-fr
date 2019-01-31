---
title: Copier (Capture par programmation) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35558a9ad6a4e7d31103910f3fe71c0a12374c22
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042251"
---
# <a name="copy-programmatic-capture"></a>Copier (capture par programmation)
Copie le contenu du fichier journal (.vsglog) tracé actif dans un nouveau fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szNewVSGLog`  
 Le nom de fichier du nouveau fichier journal graphics.  
  
## <a name="remarks"></a>Notes  
 Pour copier les informations graphiques dans un nouveau fichier, doit déjà avoir capturé des informations graphiques ; Sinon, rien ne se produit.