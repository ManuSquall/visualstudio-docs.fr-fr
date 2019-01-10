---
title: Init | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06594b749b5d92781f6c3389ca6f5f9395c98c75
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827245"
---
# <a name="init"></a>Init
Prépare le composant dans l’application de graphics diagnostics pour capturer et enregistrer des informations graphiques dans un fichier journal de graphisme activement.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
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
 [UnInit](init.md)