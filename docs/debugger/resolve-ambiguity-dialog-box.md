---
title: Résoudre une ambiguïté, boîte de dialogue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.Disambig
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a31d217f8dc492468a894f78f10a4f7656677521
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945065"
---
# <a name="resolve-ambiguity-dialog-box"></a>Résoudre une ambiguïté (boîte de dialogue)
La boîte de dialogue `Resolve Ambiguity` s'ouvre lorsque le débogueur ne parvient pas à choisir l'emplacement à afficher. Par exemple, si vous utilisez les modèles C++, vous pouvez créer plusieurs fonctions à partir d'un seul modèle de fonction. Si le débogueur s'arrête à l'emplacement d'une source dans le modèle et si vous choisissez `Go To Disassembly`, le débogueur a plusieurs options. Chaque fonction créée à partir du modèle possède son propre code machine et le débogueur ne sait pas celui que vous souhaitez afficher. La boîte de dialogue `Resolve Ambiguity` vous permet de sélectionner l'emplacement de votre choix dans une liste de tous les emplacements correspondants.  
  
 `Choose the specific location`  
 Répertorie tous les emplacements correspondant à votre commande.  
  
 `Address`  
 Affiche les adresses mémoire de chaque fonction.  
  
 `Function`  
 Affiche le nom de chaque fonction.  
  
 `Module`  
 Affiche le module (EXE ou DLL) contenant le code objet de la fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions dans le débogueur](../debugger/expressions-in-the-debugger.md)