---
title: Débogueur ne peut pas afficher le Code Source ou code machine | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ce4460aecb634523de02f2e3f6929b206b415e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186497"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Le débogueur ne parvient pas à afficher le code source ou le code machine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette erreur affiche le message suivant :  
  
 Le débogueur ne peut pas afficher le code source ou code machine de l'emplacement actuel où l'exécution s'est arrêtée.  
  
 Ce message d'erreur peut s'afficher pour plusieurs raisons :  
  
- Vous avez peut-être atteint un point d'arrêt à un emplacement sans code source pendant le débogage d'un langage ne prenant pas en charge le code machine. Ouvrez le **des points d’arrêt** fenêtre, recherchez le point d’arrêt et le supprimer.  
  
- Si vous déboguez un script, vous avez peut-être atteint un point d'arrêt alors que votre programme n'avait pas de threads. Sélectionnez **Pas à pas** ou **Continuer** dans le menu **Déboguer** pour reprendre le débogage.  
  
- Le débogueur n'a peut-être pas pu lire les informations de pile, de thread, de Registre et autres informations de contexte à partir du programme que vous déboguez pour des raisons de sécurité. Cela risque surtout de se produire si vous déboguez une application Web et que vous ne disposez pas des autorisations adéquates pour accéder au répertoire virtuel. Vous devez alors définir la sécurité du répertoire virtuel sur Anonyme, puis recommencer.  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base du débogueur](../debugger/debugger-basics.md)   
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)
