---
title: Sélectionner le type de code, boîte de dialogue | Microsoft Docs
ms.date: 06/12/2020
ms.topic: reference
f1_keywords:
- vs.debug.selectengines
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- debugging [Visual Studio], engine selection
- debugger, engine selection
- debugging engine selection dialog box
no-loc:
- Blazor WebAssembly
ms.assetid: 932269fe-94e3-43cb-8931-078f31afd177
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6fefcea57b97ad3b31e4d10330756565c005184
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2020
ms.locfileid: "88248771"
---
# <a name="select-code-type-dialog-box"></a>Sélectionner le type de code, boîte de dialogue

Pour ouvrir cette boîte de dialogue, ouvrez la boîte de dialogue **Attacher au processus**, puis cliquez sur le bouton **Sélectionner**.

**Déterminer automatiquement le type de code à déboguer** Le débogueur approprié sera sélectionné en fonction du genre de code en cours d’exécution.

**Déboguez ces types de code :** Dans la liste fournie, choisissez le ou les types de code que vous souhaitez déboguer. Cela peut être utile lors de [la résolution d’un problème d’attachement](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#BKMK_Troubleshoot_attach_errors). Cette option limite la détection uniquement aux types de code que vous souhaitez déboguer.

::: moniker range=">=vs-2019"
- Blazor WebAssembly -Côté client Blazor WebAssembly
- GPU-Software Emulator-code C++ s’exécutant sur un émulateur de logiciel GPU
- JavaScript (chrome)-JavaScript s’exécutant dans Chrome
- JavaScript (Microsoft Edge-chrome)-JavaScript s’exécutant dans Microsoft Edge basé sur le chrome pour Windows 10
- Le débogueur JavaScript CDP (v3) : protocole chrome DevTools version 3, utilisé pour le débogage dans un client CDP
- Géré (CoreCLR)-.NET Core
- Managé (compilation native)-code C++/CLR
- Géré (v 3.5, v 3.0, v 2.0)-.NET Framework du code pour .NET Framework 2,0 et versions ultérieures (jusqu’à 3,5)
- Managé (v. 4.6, v 4.5, v 4.0)-.NET Framework du code pour .NET Framework 4,0 et versions ultérieures
- Natif-C/C++
- Node.js le débogage-Code hébergé par le runtime Node.js
- Python-python 
- Script : spécifie le débogueur de script général pour JavaScript. Utilisez des options plus restrictives si elles s’appliquent à votre scénario, par exemple JavaScript (chrome).
- T-SQL-Transact-SQL
- Unity-Unity
- Mode de compatibilité managée : spécifie le débogueur hérité pour le code managé, à utiliser en général dans le débogage en mode mixte avec le code C++/CLR (permet la modification et la poursuite du mode mixte) ou pour prendre en charge les extensions ciblant le débogueur hérité. Dans la plupart des scénarios de débogage en mode mixte, sélectionnez **natif** et les types de code **managé** appropriés au lieu de mode de compatibilité managé.
::: moniker-end

Pour la plupart des scénarios, l’attachement de plusieurs débogueurs dans la même session de débogage n’est pas pris en charge. Vous pourrez peut-être effectuer cette opération à l’aide d’une seconde instance de Visual Studio.

## <a name="see-also"></a>Voir aussi
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Joindre aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
