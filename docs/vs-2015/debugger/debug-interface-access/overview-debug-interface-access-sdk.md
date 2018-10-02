---
title: Vue d’ensemble (SDK Debug Interface Access) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8de5b25b1ece8c4523ba222a97f1107d2275ba3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47502067"
---
# <a name="overview-debug-interface-access-sdk"></a>Vue d’ensemble (Kit de développement logiciel Debug Interface Access)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [vue d’ensemble (Debug Interface Access SDK)](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/overview-debug-interface-access-sdk).  
  
Utilisez le SDK de DIA pour accéder aux informations de débogage de Microsoft. Le SDK de DIA fournit qu'une COM en fonction d’ensemble d’API qui élimine la nécessité de réécrire votre code chaque fois que Microsoft modifie le format des informations de débogage. Le DIA SDK vous permet également de lire à partir d’un ensemble sélectionné de versions précédentes d’informations de débogage, situés dans des fichiers .pdb et .dbg générés par [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 5.0 et versions ultérieures.  
  
 Chaque interface dans le SDK DIA représente un autre objet COM, sauf cas contraire. Interfaces supplémentaires et donc des objets supplémentaires, sont créés au moyen de requêtes explicites, tel que [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) ou [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), et non en appelant `QueryInterface` sur les pointeurs d’interface existante.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)



