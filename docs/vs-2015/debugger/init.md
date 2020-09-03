---
title: Init | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea9f8a24d342668b3574c3798a32c58c124aca7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185845"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prépare le composant dans l’application de Graphics Diagnostics pour capturer et enregistrer activement les informations graphiques dans un fichier journal de graphisme.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `vsgLogGetter`  
 Entité pouvant être appelée, telle qu’une fonction, un pointeur de fonction, une expression lambda ou un objet de fonction, qui prend comme paramètres la longueur d’une mémoire tampon composée de `wchar_t` et d’un pointeur vers cette mémoire tampon, et retourne `void` . Lorsqu’elle est appelée, l’entité pouvant être appelée détermine le nom du fichier qui sera utilisé pour enregistrer les informations graphiques et l’écrit dans la mémoire tampon spécifiée avant de retourner.  
  
## <a name="remarks"></a>Notes  
 La `Init` fonction est appelée automatiquement lorsqu’une instance de la `VsgDbg` classe est construite en spécifiant le `bDefaultInit` paramètre de son constructeur comme `true` ; sinon, `Init` doit être appelé explicitement pour que vous puissiez capturer et enregistrer activement les informations graphiques.  
  
 Vous pouvez finaliser et fermer le fichier journal de graphisme actif en appelant `UnInit` , puis capturer et enregistrer des informations graphiques supplémentaires dans un nouveau fichier journal de graphisme en rappelant `Init` . Vous pouvez répéter cette opération autant de fois que vous le souhaitez pour créer plusieurs fichiers journaux graphiques indépendants à l’aide de la même `VsgDbg` instance.  
  
## <a name="see-also"></a>Voir aussi  
 [UnInit](../debugger/init.md)
