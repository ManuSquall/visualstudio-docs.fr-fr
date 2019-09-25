---
title: Débogage de code natif | Microsoft Docs
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
ms.openlocfilehash: 8115d16b64096af343adb918ba4855d9655d4df0
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211147"
---
# <a name="debugging-native-code"></a>Débogage du code natif
Cette section décrit des techniques et des problèmes de débogage courants pour les applications natives. Les techniques décrites dans cette section sont des techniques avancées. Pour savoir comment utiliser le débogueur Visual Studio, consultez [tout d’abord le débogueur](../debugger/debugger-feature-tour.md).

## <a name="in-this-section"></a>Dans cette section
 [Guide pratique pour Le code](../debugger/how-to-debug-optimized-code.md) optimisé de débogage donne des conseils sur le débogage du code optimisé, en particulier sur la raison pour laquelle vous devez déboguer une version non optimisée de votre programme, des paramètres d’optimisation par défaut pour les configurations Debug et Release, ainsi que des conseils pour rechercher les bogues qui ne sont que apparaissent dans le code optimisé (activation de l’optimisation dans une configuration de build Debug).

 [DebugBreak et __debugbreak](../debugger/debugbreak-and-debugbreak.md) Décrit la fonction `DebugBreak` Win32 et fournit un lien vers sa rubrique de référence dans le kit de développement logiciel (SDK) de plateforme. Décrit également l'objet intrinsèque `__debugbreak`.

 [C/C++ assertions](../debugger/c-cpp-assertions.md) aborde les instructions d’assertion, leur fonctionnement, les avantages de leur utilisation (interception des erreurs de logique, vérification des résultats d’une opération et test des conditions d' `_DEBUG`erreur), leur interaction avec et les types d’assertions pris en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]charge dans.

 [Guide pratique pour Déboguer le code](../debugger/how-to-debug-inline-assembly-code.md) assembleur inline fournit des instructions succinctes sur l’utilisation de la fenêtre Code machine pour afficher les instructions de l’assembly et la fenêtre registres pour afficher le contenu du Registre et fournit des liens vers des rubriques relatives à ces fenêtres.

 [Techniques de débogage MFC](../debugger/mfc-debugging-techniques.md) Vous renvoie à des techniques de débogage pour les programmes MFC, notamment : afxDebugBreak, la macro TRACE, la détection des fuites de mémoire dans MFC, les assertions MFC et la réduction de la taille des versions Debug MFC.

 [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md) Fournit des liens vers les techniques de débogage pour la bibliothèque Runtime C, notamment l’utilisation de la bibliothèque de débogage CRT, les macros pour la création de rapports, les différences entre malloc et _ malloc_dbg, l’écriture de fonctions de raccordement de débogage et le tas de débogage CRT.

 [FAQ sur le débogage du code natif](../debugger/debugging-native-code-faqs.md) Fournit des réponses aux questions fréquemment posées sur le débogage des programmes visuels C++

 [Débogage com et ActiveX](../debugger/com-and-activex-debugging.md) Fournit des informations sur le débogage des applications COM et ActiveX, y compris les outils que vous pouvez utiliser pour le débogage COM et ActiveX.

 [Guide pratique pour Déboguer le](../debugger/how-to-debug-injected-code.md) code injecté fournit des conseils sur le débogage du code qui utilise des attributs. Les instructions concernent le mode d'activation de l'annotation de la source, le mode d'affichage du code injecté et le mode d'affichage du code machine au point d'exécution en cours.

 [Procédure pas à pas : Débogage d’une application](../debugger/walkthrough-debugging-a-parallel-application.md) parallèle décrit comment utiliser les fenêtres d’outils **tâches parallèles** et **Piles parallèles** pour déboguer une application parallèle.

## <a name="related-sections"></a>Rubriques connexes
 [Types C++ de projets visuels](../debugger/debugging-preparation-visual-cpp-project-types.md) fournit des liens vers des rubriques qui décrivent comment déboguer les types de C++ projets natifs créés par les modèles de projet visuel.

 [Débogage de projets dll](../debugger/debugging-dll-projects.md) Fournit des informations sur la façon de déboguer des DLL natives et managées.

 [Tout d’abord, examinez le débogueur](../debugger/debugger-feature-tour.md) Fournit des liens vers les sections de plus grande taille de la documentation sur le débogage. Les informations comprennent les nouveautés du débogueur, les paramètres et la préparation, les points d'arrêt, la gestion des exceptions, la fonctionnalité Modifier &amp; Continuer, le débogage de code managé, le débogage de code natif, le débogage SQL et les références relatives à l'interface utilisateur.

## <a name="see-also"></a>Voir aussi

- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage dans Visual Studio](../debugger/index.yml)