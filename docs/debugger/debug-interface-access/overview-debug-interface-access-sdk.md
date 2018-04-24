---
title: Vue d’ensemble (Debug Interface Access SDK) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 807690edaf5626e3ec007a005717622592c14ce9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="overview-debug-interface-access-sdk"></a>Vue d’ensemble (Kit de développement logiciel Debug Interface Access)
Le SDK DIA permet d’accéder aux informations de débogage Microsoft. Le SDK DIA fournit une COM ensemble d’API qui élimine le besoin de réécrire votre code chaque fois que Microsoft modifie le format des informations de débogage. Le SDK DIA vous permet également de lire à partir d’un ensemble de versions précédentes des informations de débogage, situés dans des fichiers .pdb et .dbg générés par [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 5.0 et version ultérieure.  
  
 Chaque interface dans le SDK DIA représente un autre objet COM, sauf cas contraire. Autres interfaces et donc des objets supplémentaires, sont créés au moyen des requêtes explicites, tels que [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) ou [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), plutôt qu’en appelant `QueryInterface` sur les pointeurs d’interface existant.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)