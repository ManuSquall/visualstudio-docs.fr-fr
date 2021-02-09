---
title: Déboguer le code injecté | Microsoft Docs
description: 'Découvrez deux façons dont Visual Studio permet d’afficher le code injecté : 1) dans la fenêtre Code machine ; 2) dans un fichier source qui a à la fois le code injecté et le code d’origine.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c776303d22ad7f0b48a5f7c5361750f70c1ce6b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913232"
---
# <a name="how-to-debug-injected-code"></a>Comment : déboguer du code injecté

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

L'utilisation d'attributs peut simplifier considérablement la programmation en C++. Pour plus d’informations, consultez [concepts](/cpp/windows/attributed-programming-concepts). Certains attributs sont interprétés directement par le compilateur. D'autres injectent du code dans la source du programme, code qui est ensuite traité par le compilateur. Ce code injecté simplifie la programmation en réduisant la quantité de code à écrire. Parfois, cependant, un bogue peut provoquer un échec de l'application pendant l'exécution du code injecté. Dans ce cas, vous voudrez probablement examiner le code injecté. Visual Studio vous permet de visualiser le code injecté de deux façons :

- Vous pouvez l’afficher dans la fenêtre **Code Machine**.

- Avec [/Fx](/cpp/build/reference/fx-merge-injected-code), vous pouvez créer un fichier source fusionné contenant le code d’origine et le code injecté.

La fenêtre **Code Machine** affiche les instructions en langage assembleur qui correspondent au code source et au code injecté par des attributs. En outre, la fenêtre code **machine** peut afficher l’annotation de code source.

## <a name="to-turn-on-source-annotation"></a>Pour activer l'annotation de la source

- Cliquez avec le bouton droit sur la fenêtre **Code Machine** puis, dans le menu contextuel, cliquez sur **Afficher le code source**.

     Si vous connaissez l’emplacement d’un attribut dans une fenêtre source, vous pouvez utiliser le menu contextuel pour rechercher le code injecté dans la fenêtre **Code Machine**.

## <a name="to-view-injected-code"></a>Pour afficher le code injecté

1. Assurez-vous que le débogueur est en mode arrêt.

2. Dans une fenêtre de code source, placez le curseur devant l'attribut dont vous voulez afficher le code injecté.

3. Cliquez avec le bouton droit puis, dans le menu contextuel, cliquez sur **Atteindre le code Machine**.

     Si l’emplacement de l’attribut est situé à proximité du point d’exécution en cours, vous pouvez sélectionner la fenêtre **Code Machine** dans le menu **Déboguer**.

## <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Pour afficher le code machine au point d'exécution en cours

1. Assurez-vous que le débogueur est en mode arrêt.

2. Dans le menu **Déboguer**, choisissez **Fenêtres**, puis cliquez sur **Code Machine**.

## <a name="see-also"></a>Voir aussi

- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage du code natif](../debugger/debugging-native-code.md)