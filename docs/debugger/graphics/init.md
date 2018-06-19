---
title: Init | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0436384e0af816475590ab84dc645848113f5ab7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476196"
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
 Une entité pouvant être appelée, comme une fonction, pointeur fonction, lambda ou objet de fonction, qui prend comme paramètres de la longueur d’une mémoire tampon composée de `wchar_t` et un pointeur vers cette mémoire tampon et retourne `void`. Lorsqu’elle est appelée, l’entité peut être appelée détermine le nom de fichier qui doit servir à enregistrer les informations graphiques et l’écrit dans la mémoire tampon spécifiée avant de retourner.  
  
## <a name="remarks"></a>Notes  
 Le `Init` fonction est appelée automatiquement lorsqu’une instance de la `VsgDbg` classe est créée en spécifiant le `bDefaultInit` de son constructeur en tant que paramètre de `true`; sinon, `Init` doit être appelé explicitement avant pouvez activement capturer et enregistrer des informations graphiques.  
  
 Vous pouvez finaliser et fermez actives du journal des graphiques fichier en appelant `UnInit`, puis capturer et enregistrer des informations graphiques supplémentaires dans un nouveau fichier journal de graphiques en appelant `Init` à nouveau. Vous pouvez répéter cette opération autant de fois que vous souhaitez créer plusieurs graphiques indépendants des fichiers journaux à l’aide de la même `VsgDbg` instance.  
  
## <a name="see-also"></a>Voir aussi  
 [UnInit](init.md)