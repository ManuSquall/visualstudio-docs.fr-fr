---
title: Copier (Capture par programmation) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aab2b18c8c349211f4b5bd26b055d6ee5b65f0c6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990946"
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