---
title: Init | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61c3d580c4e9e0362629d70c23e0b918fe698429
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54983454"
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
  
## <a name="remarks"></a>Remarques  
 Le `Init` fonction est appelée automatiquement lorsqu’une instance de la `VsgDbg` classe est construite en spécifiant la `bDefaultInit` paramètre de son constructeur en tant que `true`; sinon, `Init` doit être appelée explicitement avant de vous pouvez activement capturer et enregistrer des informations graphiques.  
  
 Vous pouvez finaliser et fermez l’active fichier journal de graphisme en appelant `UnInit`, puis capturer et enregistrer des informations graphiques supplémentaires à un nouveau fichier journal de graphisme en appelant `Init` à nouveau. Vous pouvez répéter cette opération autant de fois que vous souhaitez créer plusieurs graphiques indépendants des fichiers journaux à l’aide de la même `VsgDbg` instance.  
  
## <a name="see-also"></a>Voir aussi  
 [UnInit](init.md)