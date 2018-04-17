---
title: Copier (Capture par programmation) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a658f458b6f2dac48ad19f60e2491ad9d6e94406
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="copy-programmatic-capture"></a>Copier (capture par programmation)
Copie le contenu du fichier journal (.vsglog) graphique actif dans un nouveau fichier.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szNewVSGLog`  
 Le nom de fichier du nouveau fichier journal de graphiques.  
  
## <a name="remarks"></a>Notes  
 Pour copier les informations graphiques dans un nouveau fichier, doit déjà avoir capturé des informations graphiques ; Sinon, rien ne se produit.