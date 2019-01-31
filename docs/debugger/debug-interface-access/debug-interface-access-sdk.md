---
title: SDK Debug Interface Access | Microsoft Docs
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 161934d30c7cd4ecb9d2658e7dac12e46049be1a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932296"
---
# <a name="debug-interface-access-sdk"></a>Kit de développement logiciel de Debug Interface Access

Le Microsoft Debug Interface Access Kit de développement logiciel (DIA SDK) fournit l’accès aux informations stockées dans des fichiers de base de données (.pdb) de programme générés par les outils de post-compilation Microsoft de débogage. Étant donné que le format du fichier .pdb généré par les outils de post-compilation subit une révision constante, exposant le format est peu pratique. À l’aide de l’API DIA, vous pouvez développer des applications qui recherchent et parcourir les informations de débogage stockées dans un fichier .pdb. De telles applications pourraient, par exemple, signaler des informations sur la pile back de trace et analyser les données de performances.

## <a name="in-this-section"></a>Dans cette section

[Prise en main](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
Donne une vue d’ensemble du SDK DIA fonctionnalités et spécifie où le DIA SDK est installé, ainsi que les fichiers de bibliothèque et un en-tête requis.

[Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
Fournit des instructions sur l’utilisation de l’API DIA pour interroger le fichier .pdb.

[Symboles et étiquettes de symbole](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
Explique comment les balises symbols et symbol sont utilisés dans l’API de DIA.

[Référence](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
Contient les interfaces, méthodes, énumérations et structures de l’API de DIA.

[Dia2dump, exemple](../../debugger/debug-interface-access/dia2dump-sample.md)  
Illustre l’utilisation de l’API DIA pour rechercher et parcourir des informations de débogage.
