---
title: Prise en main (kit de développement logiciel de debug interface Access) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a93225b4bd4180a9ce3389911c2c15d0dbef52ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468601"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Mise en route (Kit de développement logiciel de Debug Interface Access)
Le kit de développement logiciel (SDK) debug interface Access (DIA) fournit une documentation pédagogique et un exemple qui illustre l’utilisation de l’API DIA. Utilisez les interfaces et les méthodes dans le kit de développement logiciel (SDK) DIA pour développer des applications personnalisées qui ouvrent les fichiers. pdb et. dbg et recherchent dans leur contenu des symboles, des valeurs, des attributs, des adresses et d’autres informations de débogage. Ce kit de développement logiciel (SDK) fournit également des tables de référence pour les propriétés associées aux symboles trouvés dans les applications C++.

 Pour optimiser l’utilisation du kit de développement logiciel (SDK) DIA, vous devez être familiarisé avec les éléments suivants :

- Langage de programmation C++

- Programmation COM

- Environnement de développement intégré (IDE) Visual Studio pour la compilation des exemples

  Le kit de développement DIA SDK est normalement installé avec Visual Studio et son emplacement par défaut est *[lecteur]* \Program Files\Microsoft Visual Studio 9.0 \ dia SDK. Dans le cadre de l’installation, le msdia90.dll, qui implémente le kit de développement logiciel (SDK) DIA, est inscrit automatiquement. par conséquent, tout ce que vous devez faire pour l’utiliser consiste à inclure `dia2.h` dans votre programme et à établir un lien vers `diaguids.lib` .

  En-tête : include\dia2.h

  Bibliothèque : lib\diaguids.lib

  DLL: bin\msdia80.dll

  IDL: idl\dia2.idl

## <a name="in-this-section"></a>Dans cette section

[Vue d'ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)

Passe en revue l’architecture de base de DIA.

[Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

Fournit des instructions pas à pas sur l’utilisation de l’API DIA pour interroger un fichier. pdb.

## <a name="see-also"></a>Voir aussi

- [SDK Debug Interface Access](../../debugger/debug-interface-access/debug-interface-access-sdk.md)