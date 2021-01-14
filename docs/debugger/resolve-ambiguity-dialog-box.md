---
title: Résoudre l’ambiguïté, boîte de dialogue | Microsoft Docs
description: Consultez la boîte de dialogue résoudre l’ambiguïté de Visual Studio, qui apparaît lorsque le débogueur ne peut pas choisir l’emplacement à afficher.
ms.custom: SEO-VS-2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6f7156a43bc8c5c60415680b4380600e9e695cc
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205604"
---
# <a name="resolve-ambiguity-dialog-box"></a>Résoudre une ambiguïté (boîte de dialogue)
La boîte de dialogue `Resolve Ambiguity` s'ouvre lorsque le débogueur ne parvient pas à choisir l'emplacement à afficher. Par exemple, si vous utilisez les modèles C++, vous pouvez créer plusieurs fonctions à partir d'un seul modèle de fonction. Si le débogueur s'arrête à l'emplacement d'une source dans le modèle et si vous choisissez `Go To Disassembly`, le débogueur a plusieurs options. Chaque fonction créée à partir du modèle possède son propre code machine et le débogueur ne sait pas celui que vous souhaitez afficher. La boîte de dialogue `Resolve Ambiguity` vous permet de sélectionner l'emplacement de votre choix dans une liste de tous les emplacements correspondants.

 `Choose the specific location` Répertorie tous les emplacements correspondant à votre commande.

 `Address` Affiche les adresses mémoire de chaque fonction.

 `Function` Affiche le nom de chaque fonction.

 `Module` Affiche le module (EXE ou DLL) contenant le code objet de la fonction.

## <a name="see-also"></a>Voir aussi
- [Expressions dans le débogueur](../debugger/expressions-in-the-debugger.md)