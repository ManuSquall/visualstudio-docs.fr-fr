---
title: Débogage du Code natif | Microsoft Docs
ms.date: 04/11/2017
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging native code
- debugging [C++], native code
- debugging [Visual Studio], native code
- native code, debugging
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 5a7cf0b150c45037941010bf7e611f4bc21252c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62851908"
---
# <a name="debugging-native-code"></a>Débogage du code natif
Cette section décrit des techniques et des problèmes de débogage courants pour les applications natives. Les techniques décrites dans cette section sont des techniques avancées. Pour plus d’informations à l’aide du débogueur Visual Studio, consultez [tout d’abord examiner le débogueur](../debugger/debugger-feature-tour.md)).

## <a name="in-this-section"></a>Dans cette section
 [Guide pratique pour Déboguer du Code optimisé](../debugger/how-to-debug-optimized-code.md) donne des conseils pour le débogage de code optimisé, en particulier, raison pour laquelle vous devez déboguer une version non optimisée de votre programme, les paramètres d’optimisation par défaut pour les configurations Debug et Release et des conseils pour rechercher les bogues qui uniquement apparaissent dans le code optimisé (activation de l’optimisation dans une configuration de build Debug).

 [DebugBreak et __debugbreak](../debugger/debugbreak-and-debugbreak.md) décrit Win32 `DebugBreak` fonction et fournit un lien vers sa rubrique de référence dans le kit Platform SDK. Décrit également l'objet intrinsèque `__debugbreak`.

 [C /C++ Assertions](../debugger/c-cpp-assertions.md) décrit les instructions d’assertion, leur fonctionnement, les avantages de leur utilisation (interception erreurs de logique, vérification des résultats d’une opération et test des conditions d’erreur), leur interaction avec `_DEBUG`et les types de assertions pris en charge dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

 [Guide pratique pour Déboguer le Code assembleur Inline](../debugger/how-to-debug-inline-assembly-code.md) fournit de brèves instructions sur l’utilisation de la fenêtre code machine pour afficher les instructions d’assembly et la fenêtre registres pour afficher le contenu du Registre et fournit des liens vers des rubriques relatives à ces fenêtres.

 [Techniques de débogage MFC](../debugger/mfc-debugging-techniques.md) vous renvoie à des techniques de débogage pour les programmes MFC, notamment : afxDebugBreak, la macro TRACE, la détection de mémoire les fuites dans MFC, MFC assertions, et réduire la taille de débogage MFC génère.

 [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md) vous renvoie à des techniques de débogage pour la bibliothèque Runtime C, notamment à l’aide de la bibliothèque de débogage CRT, les macros pour la création de rapports, les différences entre malloc et _malloc_dbg, l’écriture de fonctions de raccordement de débogage et le tas de débogage CRT.

 [Forum aux questions sur Code natif de débogage](../debugger/debugging-native-code-faqs.md) fournit des réponses aux questions fréquemment posées sur le débogage Visual C++ programmes

 [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md) fournit des informations sur le débogage des applications COM et ActiveX, y compris les outils que vous pouvez utiliser pour COM et ActiveX de débogage.

 [Guide pratique pour Déboguer le Code injecté](../debugger/how-to-debug-injected-code.md) fournit des conseils sur le débogage du code qui utilise des attributs. Les instructions concernent le mode d'activation de l'annotation de la source, le mode d'affichage du code injecté et le mode d'affichage du code machine au point d'exécution en cours.

 [Procédure pas à pas : Débogage d’une Application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md) explique comment utiliser le **tâches parallèles** et **piles parallèles** outil windows pour déboguer une application parallèle.

## <a name="related-sections"></a>Rubriques connexes
 [Visual C++ Types de projets](../debugger/debugging-preparation-visual-cpp-project-types.md) fournit des liens vers des rubriques qui décrivent comment déboguer les types de projet natif créés par l’élément visuel C++ modèles de projet.

 [Débogage de projets DLL](../debugger/debugging-dll-projects.md) fournit des informations sur la façon de déboguer des DLL natives et managées.

 [Tout d’abord examiner le débogueur](../debugger/debugger-feature-tour.md) fournit des liens vers des sections plus vastes de la documentation relative au débogage. Les informations comprennent les nouveautés du débogueur, les paramètres et la préparation, les points d'arrêt, la gestion des exceptions, la fonctionnalité Modifier &amp; Continuer, le débogage de code managé, le débogage de code natif, le débogage SQL et les références relatives à l'interface utilisateur.

## <a name="see-also"></a>Voir aussi

- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage dans Visual Studio](../debugger/index.md)