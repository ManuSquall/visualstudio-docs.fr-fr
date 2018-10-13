---
title: Init | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a630906fa2a23a87853e8a835f155cda3ec06ecc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252393"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prépare le composant dans l’application de graphics diagnostics pour capturer et enregistrer des informations graphiques dans un fichier journal de graphisme activement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `vsgLogGetter`  
 Une entité pouvant être appelée, comme une fonction, un pointeur de fonction, un lambda ou un objet de fonction, qui prend comme paramètres de la longueur d’une mémoire tampon composée de `wchar_t` et un pointeur vers cette mémoire tampon et retourne `void`. Lorsqu’elle est appelée, l’entité pouvant être appelée détermine le nom de fichier qui sera utilisé pour enregistrer les informations graphiques et l’écrit dans la mémoire tampon spécifiée avant de retourner.  
  
## <a name="remarks"></a>Notes  
 Le `Init` fonction est appelée automatiquement lorsqu’une instance de la `VsgDbg` classe est construite en spécifiant la `bDefaultInit` paramètre de son constructeur en tant que `true`; sinon, `Init` doit être appelée explicitement avant de vous pouvez activement capturer et enregistrer des informations graphiques.  
  
 Vous pouvez finaliser et fermez l’active fichier journal de graphisme en appelant `UnInit`, puis capturer et enregistrer des informations graphiques supplémentaires à un nouveau fichier journal de graphisme en appelant `Init` à nouveau. Vous pouvez répéter cette opération autant de fois que vous souhaitez créer plusieurs graphiques indépendants des fichiers journaux à l’aide de la même `VsgDbg` instance.  
  
## <a name="see-also"></a>Voir aussi  
 [UnInit](../debugger/init.md)



