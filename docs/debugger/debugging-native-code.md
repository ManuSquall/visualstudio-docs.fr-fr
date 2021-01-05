---
title: Débogage de code natif | Microsoft Docs
description: Découvrez les problèmes de débogage courants et les techniques de haut niveau pour les applications natives dans Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4fee3044e4eaa1e7dd3549923082f9b843951b28
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728315"
---
# <a name="debugging-native-code"></a>Débogage du code natif
Cette section décrit des techniques et des problèmes de débogage courants pour les applications natives. Les techniques décrites dans cette section sont des techniques avancées. Pour savoir comment utiliser le débogueur Visual Studio, consultez [tout d’abord le débogueur](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>Dans cette section
 [Comment : déboguer le code optimisé](../debugger/how-to-debug-optimized-code.md) Donne des conseils sur le débogage de code optimisé, en particulier sur la raison pour laquelle vous devez déboguer une version non optimisée de votre programme, les paramètres d’optimisation par défaut pour les configurations Debug et Release, ainsi que des conseils pour rechercher des bogues qui apparaissent uniquement dans le code optimisé (activation de l’optimisation dans une configuration de build Debug).

 [DebugBreak et __debugbreak](../debugger/debugbreak-and-debugbreak.md) Décrit la `DebugBreak` fonction Win32 et fournit un lien vers sa rubrique de référence dans le kit de développement logiciel (SDK) de plateforme. Décrit également l'objet intrinsèque `__debugbreak`.

 [Assertions C/C++](../debugger/c-cpp-assertions.md) Décrit les instructions d’assertion, leur fonctionnement, les avantages de leur utilisation (interception des erreurs de logique, vérification des résultats d’une opération et test des conditions d’erreur), leur interaction avec `_DEBUG` et les types d’assertions prises en charge dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 [Comment : déboguer du code assembleur inline](../debugger/how-to-debug-inline-assembly-code.md) Fournit des instructions succinctes sur l’utilisation de la fenêtre Code machine pour afficher les instructions de l’assembly et la fenêtre registres pour afficher le contenu du Registre et fournit des liens vers des rubriques relatives à ces fenêtres.

 [Techniques de débogage MFC](../debugger/mfc-debugging-techniques.md) Vous renvoie à des techniques de débogage pour les programmes MFC, notamment : afxDebugBreak, la macro TRACE, la détection des fuites de mémoire dans MFC, les assertions MFC et la réduction de la taille des versions Debug MFC.

 [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md) Fournit des liens vers les techniques de débogage pour la bibliothèque C Run-Time, notamment l’utilisation de la bibliothèque de débogage CRT, les macros pour la création de rapports, les différences entre malloc et _malloc_dbg, l’écriture de fonctions de raccordement de débogage et le tas de débogage CRT.

 [FAQ sur le débogage du code natif](../debugger/debugging-native-code-faqs.md) Fournit des réponses aux questions fréquemment posées sur le débogage des programmes C++

 [Débogage com et ActiveX](../debugger/com-and-activex-debugging.md) Fournit des informations sur le débogage des applications COM et ActiveX, y compris les outils que vous pouvez utiliser pour le débogage COM et ActiveX.

 [Comment : déboguer du code injecté](../debugger/how-to-debug-injected-code.md) Fournit des instructions sur le débogage du code qui utilise des attributs. Les instructions concernent le mode d'activation de l'annotation de la source, le mode d'affichage du code injecté et le mode d'affichage du code machine au point d'exécution en cours.

 [Procédure pas à pas : débogage d’une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md) Décrit comment utiliser les fenêtres d’outils **tâches parallèles** et **Piles parallèles** pour déboguer une application parallèle.

## <a name="related-sections"></a>Sections connexes
 [Préparer le débogage de projets C++](../debugger/debugging-preparation-visual-cpp-project-types.md) Fournit des liens vers des rubriques qui décrivent comment déboguer les types de projets natifs créés par les modèles de projet C++.

 [Débogage de projets dll](../debugger/debugging-dll-projects.md) Fournit des informations sur la façon de déboguer des DLL natives et managées.

 [Tout d’abord, examinez le débogueur](../debugger/debugger-feature-tour.md) Fournit des liens vers les sections de plus grande taille de la documentation sur le débogage. Les informations comprennent les nouveautés du débogueur, les paramètres et la préparation, les points d'arrêt, la gestion des exceptions, la fonctionnalité Modifier &amp; Continuer, le débogage de code managé, le débogage de code natif, le débogage SQL et les références relatives à l'interface utilisateur.

## <a name="see-also"></a>Voir aussi

- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage dans Visual Studio](../debugger/index.yml)