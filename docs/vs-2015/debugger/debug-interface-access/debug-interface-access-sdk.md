---
title: Kit de développement logiciel Debug interface Access | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ddaea95bc879364de99c0ec01213cda30fa4e7d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197623"
---
# <a name="debug-interface-access-sdk"></a>Kit de développement logiciel de Debug Interface Access
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le kit de développement logiciel (SDK) Microsoft Debug interface Access (DIA SDK) permet d’accéder aux informations de débogage stockées dans des fichiers de base de données du programme (. pdb) générés par les outils Microsoft post-compilation. Étant donné que le format du fichier. pdb généré par les outils post-compilation subit une révision constante, l’exposition du format est irréalisable. À l’aide de l’API DIA, vous pouvez développer des applications qui recherchent et parcourent les informations de débogage stockées dans un fichier. pdb. De telles applications peuvent, par exemple, signaler les informations de trace de la pile de rapports et analyser les données de performances.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en main](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Donne une vue d’ensemble des fonctionnalités du kit de développement logiciel (SDK) DIA et spécifie l’emplacement d’installation du kit de développement DIA, ainsi que les fichiers d’en-tête et de bibliothèque requis.  
  
 [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Fournit des instructions sur l’utilisation de l’API DIA pour interroger le fichier. pdb.  
  
 [Symboles et étiquettes de symbole](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Explique comment les symboles et les balises de symboles sont utilisés dans l’API DIA.  
  
 [Référence](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Contient les interfaces, les méthodes, les énumérations et les structures de l’API DIA.  
  
 [Dia2dump, exemple](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Montre comment utiliser l’API DIA pour rechercher et parcourir les informations de débogage.  
  
 [Dia2dump.cpp, fichier source](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Code source utilisé par l' [exemple Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) pour illustrer l’API dia.
