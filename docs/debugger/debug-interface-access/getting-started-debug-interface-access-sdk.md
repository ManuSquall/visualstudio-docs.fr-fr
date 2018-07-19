---
title: Prise en main (Debug Interface Access SDK) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1fdfe560f22374c0b46305d096bea32a784babe6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457899"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Mise en route (Kit de développement logiciel de Debug Interface Access)
Le Debug Interface Access (DIA) SDK vous fournit les instruction documentation et un exemple qui illustre l’utilisation de l’API de DIA. Utilisez les méthodes et interfaces dans le SDK DIA pour développer des applications personnalisées qui ouvrent les fichiers .pdb et .dbg et de rechercher leur contenu pour les symboles, les valeurs, les attributs, les adresses et les autres informations de débogage. Ce kit fournit également des tables de référence pour les propriétés associées aux symboles dans les applications C++.  
  
 Pour mieux utiliser la DIA SDK, vous devez connaître les éléments suivants :  
  
-   Langage de programmation C++  
  
-   Programmation COM.  
  
-   Environnement de développement intégré Visual Studio (IDE) pour compiler les exemples  
  
 Le SDK DIA est normalement installé avec Visual Studio et son emplacement par défaut est *[lecteur]* \Program Files\Microsoft 9.0\DIA de Visual Studio SDK. Dans le cadre de l’installation, le msdia90.dll, qui implémente le DIA SDK, est enregistré automatiquement tout ce dont vous devez faire pour utiliser consiste donc à inclure `dia2.h` dans votre programme et un lien vers `diaguids.lib`.  
  
 En-tête : include\dia2.h  
  
 Bibliothèque : lib\diaguids.lib  
  
 DLL : bin\msdia80.dll  
  
 IDL : idl\dia2.idl  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d’ensemble](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Passe en revue l’architecture de base de DIA.  
  
 [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Fournit des instructions détaillées sur l’utilisation de l’API DIA pour interroger un fichier .pdb.  
  
## <a name="see-also"></a>Voir aussi  
 [SDK Debug Interface Access](../../debugger/debug-interface-access/debug-interface-access-sdk.md)