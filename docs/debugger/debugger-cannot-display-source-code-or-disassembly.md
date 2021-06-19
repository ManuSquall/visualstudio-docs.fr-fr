---
title: Le débogueur ne peut pas afficher le code source ou le code machine
description: Consultez les raisons du message « le débogueur ne peut pas afficher le code source ou le code machine pour l’emplacement actuel où l’exécution s’est arrêtée ».
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bac2f04ab77e34186a4f0ee202fa8d16f6e45e38
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387344"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Le débogueur ne parvient pas à afficher le code source ou le code machine
Cette erreur affiche le message suivant :

 Le débogueur ne peut pas afficher le code source ou code machine de l'emplacement actuel où l'exécution s'est arrêtée.

 Ce message d'erreur peut s'afficher pour plusieurs raisons :

- Vous avez peut-être atteint un point d'arrêt à un emplacement sans code source pendant le débogage d'un langage ne prenant pas en charge le code machine. Ouvrez la fenêtre **points d’arrêt** , localisez le point d’arrêt, puis supprimez-le.

- Si vous déboguez un script, vous avez peut-être atteint un point d'arrêt alors que votre programme n'avait pas de threads. Sélectionnez **Pas à pas** ou **Continuer** dans le menu **Déboguer** pour reprendre le débogage.

- Le débogueur n'a peut-être pas pu lire les informations de pile, de thread, de Registre et autres informations de contexte à partir du programme que vous déboguez pour des raisons de sécurité. Cela risque surtout de se produire si vous déboguez une application Web et que vous ne disposez pas des autorisations adéquates pour accéder au répertoire virtuel. Vous devez alors définir la sécurité du répertoire virtuel sur Anonyme, puis recommencer.

## <a name="see-also"></a>Voir aussi
- [Débogage dans Visual Studio](../debugger/index.yml)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)
- [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)