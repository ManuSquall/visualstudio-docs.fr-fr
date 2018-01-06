---
title: "Débogage de Code natif | Documents Microsoft"
ms.custom: 
ms.date: 04/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
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
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94f3d0cfd57f4d907bab758e52e0499b63941236
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-native-code"></a>Débogage du code natif
Cette section décrit des techniques et des problèmes de débogage courants pour les applications natives. Les techniques décrites dans cette section sont des techniques avancées. Pour plus d’informations à l’aide du débogueur Visual Studio, consultez [présentation du débogueur](../debugger/debugger-basics.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour déboguer le code optimisé](../debugger/how-to-debug-optimized-code.md)  
 Contient des conseils sur le débogage d’un code optimisé, en particulier sur les raisons pour lesquelles vous devez déboguer une version non optimisée de votre programme, sur les paramètres d’optimisation par défaut pour les configurations Debug et Release, ainsi que sur la recherche des bogues qui n’apparaissent que dans le code optimisé (activation de l’optimisation dans une configuration de build Debug).  
  
 [DebugBreak et __debugbreak](../debugger/debugbreak-and-debugbreak.md)  
 Décrit la fonction Win32 `DebugBreak` et fournit un lien vers sa rubrique de référence dans le Kit de développement Platform SDK. Décrit également l'objet intrinsèque `__debugbreak`.  
  
 [Assertions C/C++](../debugger/c-cpp-assertions.md)  
 Décrit les instructions d'assertion, leur fonctionnement, les avantages liés à leur utilisation (interception des erreurs de logique, vérification des résultats d'une opération et test des conditions d'erreur), leur interaction avec `_DEBUG` et les types d'assertions pris en charge dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Guide pratique pour déboguer du code d’assembly inline](../debugger/how-to-debug-inline-assembly-code.md)  
 Explique brièvement comment utiliser la fenêtre Code Machine pour afficher les instructions assembly et la fenêtre Registres pour afficher le contenu du Registre, et fournit des liens vers des rubriques relatives à ces fenêtres.  
  
 [Techniques de débogage de MFC](../debugger/mfc-debugging-techniques.md)  
 Vous renvoie à des techniques de débogage pour les programmes MFC, parmi lesquelles afxDebugBreak, la macro TRACE, la détection des fuites de mémoire dans les MFC, les assertions MFC et la réduction de la taille des versions Debug MFC.  
  
 [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md)  
 Vous renvoie à des techniques de débogage pour la bibliothèque Runtime C, parmi lesquelles l'utilisation de la bibliothèque de débogage CRT, les macros pour la création de rapports, les différences entre malloc et _malloc_dbg, l'écriture de fonctions de raccordement de débogage et le tas de débogage CRT.  
  
 [Forum Aux Questions sur le débogage du code natif](../debugger/debugging-native-code-faqs.md)  
 Fournit des réponses aux questions fréquemment posées sur le débogage des programmes Visual C++  
  
 [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)  
 Fournit des informations sur le débogage des applications COM et ActiveX, y compris sur les outils que vous pouvez utiliser pour le débogage COM et ActiveX.  
  
 [Guide pratique pour déboguer du code injecté](../debugger/how-to-debug-injected-code.md)  
 Explique comment déboguer du code qui utilise des attributs. Les instructions concernent le mode d'activation de l'annotation de la source, le mode d'affichage du code injecté et le mode d'affichage du code machine au point d'exécution en cours.  
  
 [Procédure pas à pas : débogage d’une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Décrit comment utiliser le **tâches parallèles** et **piles parallèles** fenêtres pour déboguer une application parallèle.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de projets Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)  
 Fournit des liens vers des rubriques qui décrivent le débogage de types de projets natifs, créés par les modèles de projet Visual C++.  

 [Débogage de projets DLL](../debugger/debugging-dll-projects.md) fournit des informations sur la façon de déboguer des DLL natives et managées.
  
 [Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)  
 Fournit des liens vers des sections plus vastes de la documentation relative au débogage. Les informations comprennent les nouveautés du débogueur, les paramètres et la préparation, les points d'arrêt, la gestion des exceptions, la fonctionnalité Modifier & Continuer, le débogage de code managé, le débogage de code natif, le débogage SQL et les références relatives à l'interface utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)  
 [Débogage dans Visual Studio](../debugger/index.md) [visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)