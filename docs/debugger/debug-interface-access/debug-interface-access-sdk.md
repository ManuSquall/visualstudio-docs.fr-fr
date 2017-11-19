---
title: Debug Interface Access SDK | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e404f0b893453fa319d5c4df97319f8e77720805
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="debug-interface-access-sdk"></a>Kit de développement logiciel de Debug Interface Access
Le Microsoft Debug Interface Access Kit de développement logiciel (DIA SDK) donne accès aux informations de débogage stockées dans les fichiers de base de données (.pdb) de programme générés par les outils de post-compilation Microsoft. Étant donné que le format du fichier .pdb généré par les outils de post-compilation subit une révision constante, exposant le format s’avère impossible. À l’aide de l’API DIA, vous pouvez développer des applications qui recherchent et parcourir les informations de débogage stockées dans un fichier .pdb. De telles applications pourraient, par exemple, consigner des informations de suivi inverse de pile et analyser les données de performances.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Donne une vue d’ensemble du SDK DIA fonctionnalités et indique où le DIA SDK est installé, ainsi que les fichiers de bibliothèque et un en-tête requis.  
  
 [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Fournit des instructions sur l’utilisation de l’API DIA pour interroger le fichier .pdb.  
  
 [Symboles et étiquettes de symbole](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Explique comment les étiquettes symbols et symbol sont utilisées dans l’API de DIA.  
  
 [Référence](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Contient les interfaces, méthodes, énumérations et structures de l’API de DIA.  
  
 [Dia2dump, exemple](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Montre comment utiliser l’API DIA pour rechercher et parcourir des informations de débogage.  
  
 [Dia2dump.cpp, fichier source](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Code utilisé par la source [Dia2dump exemple](../../debugger/debug-interface-access/dia2dump-sample.md) pour illustrer l’API DIA.