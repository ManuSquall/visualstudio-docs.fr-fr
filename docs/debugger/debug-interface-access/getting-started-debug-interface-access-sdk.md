---
title: Mise en route (SDK Debug Interface Access) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 24dc53efe0b7e30d2b585519d0ca0a8c070791d3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031201"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Mise en route (Kit de développement logiciel de Debug Interface Access)
Le Debug Interface Access (DIA) SDK vous fournit avec documentation pédagogique et un exemple qui illustre comment utiliser l’API de DIA. Utilisez les méthodes et interfaces dans le SDK DIA pour développer des applications personnalisées qui ouvrent les fichiers .pdb et .dbg et de rechercher leur contenu pour les symboles, les valeurs, les attributs, les adresses et les autres informations de débogage. Ce SDK fournit également des tables de référence pour les propriétés associées aux symboles utilisés dans les applications C++.  
  
 Pour mieux utiliser le DIA SDK, vous devez être familiarisé avec les éléments suivants :  
  
- Langage de programmation C++  
  
- Programmation COM.  
  
- Environnement de développement intégré Visual Studio (IDE) pour compiler les exemples  
  
  Le SDK DIA est normalement installé avec Visual Studio et son emplacement par défaut est *[lecteur]* \Program Files\Microsoft 9.0\DIA Visual Studio SDK. Dans le cadre de l’installation, msdia90.dll, qui implémente le DIA SDK, est automatiquement enregistré tout ce que vous devez effectuer pour l’utiliser consiste donc à inclure `dia2.h` dans votre programme et un lien vers `diaguids.lib`.  
  
  En-tête : include\dia2.h  
  
  Bibliothèque : lib\diaguids.lib  
  
  DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Passe en revue l’architecture de base de DIA.  
  
 [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Fournit des instructions détaillées sur l’utilisation de l’API DIA pour interroger un fichier .pdb.  
  
## <a name="see-also"></a>Voir aussi  
 [SDK Debug Interface Access](../../debugger/debug-interface-access/debug-interface-access-sdk.md)