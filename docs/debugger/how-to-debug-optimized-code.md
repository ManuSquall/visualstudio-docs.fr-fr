---
title: 'Comment : déboguer le Code optimisé | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9610f71a197c47521e2139d40aff1afde6a8a894
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31478078"
---
# <a name="how-to-debug-optimized-code"></a>Comment : déboguer le code optimisé
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
> [!NOTE]
>  Le [/Zo (améliorer le débogage optimisé)](/cpp/build/reference/zo-enhance-optimized-debugging)option du compilateur (introduite dans Visual Studio Update 3) génère des informations de débogage pour le code optimisé (projets qui ne sont pas générés avec le **/Od** option du compilateur. Consultez [/O (optimiser le Code), Options](/cpp/build/reference/o-options-optimize-code)). Cela inclut la prise en charge améliorée pour le débogage des variables locales et des fonctions inline.  
>   
>  [Modifier & Continuer](../debugger/edit-and-continue-visual-csharp.md) est désactivé lorsque le **/Zo** option de compilateur est utilisée.  
  
 Lorsque le compilateur optimise le code, il repositionne et réorganise les instructions. Il permet ainsi d'obtenir un code compilé plus efficace. En raison de cette réorganisation, le débogueur ne peut pas toujours identifier le code source qui correspond à un jeu d'instructions.  
  
 L'optimisation peut affecter :  
  
-   Les variables locales, qui peuvent être supprimées par l'optimiseur ou être déplacées vers des emplacements que le débogueur ne comprend pas.  
  
-   Des positions à l'intérieur d'une fonction, qui sont modifiées lorsque l'optimiseur fusionne des blocs de code.  
  
-   Les noms de fonctions pour les trames de la pile des appels, qui peuvent être erronés si l'optimiseur fusionne deux fonctions.  
  
 Les trames qui s'affichent sur la pile des appels sont presque toujours correctes, à condition toutefois que vous ayez des symboles pour toutes les trames. Les trames de la pile des appels seront incorrectes en cas d'altération de la pile, ou si certaines fonctions sont écrites en langage assembleur, ou encore s'il y a des trames de système d'exploitation sans correspondance avec les symboles figurant dans la pile des appels.  
  
 Les variables globales et statiques s'affichent toujours correctement. C'est également le cas pour les dispositions de structures. Si un pointeur désigne une structure et que la valeur de ce pointeur est correcte, chaque variable membre de la structure affichera la valeur correcte.  
  
 En raison de ces limitations, vous devez effectuer le débogage en utilisant si possible une version non optimisée de votre programme. Par défaut, l'optimisation est désactivée dans la configuration Debug d'un programme Visual C++ et activée dans la configuration Release.  
  
 Mais un bogue peut apparaître uniquement dans une version optimisée d'un programme. Dans ce cas, vous devez déboguer le code optimisé.  
  
### <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Pour activer l'optimisation dans une configuration de build Debug  
  
1.  Lorsque vous créez un projet, sélectionnez la cible `Win32 Debug`. Utilisez le `Win32``Debug` cible jusqu'à ce que votre programme soit entièrement débogué et que vous êtes prêt à générer un `Win32 Release` cible. Le compilateur n'optimise pas la cible `Win32 Debug`.  
  
2.  Sélectionnez le projet dans l’Explorateur de solutions.  
  
3.  Sur le **vue** menu, cliquez sur **Pages de propriétés**.  
  
4.  Dans le **Pages de propriétés** boîte de dialogue zone, assurez-vous que `Debug` est sélectionné dans le **Configuration** liste déroulante.  
  
5.  Dans l’affichage des dossiers sur la gauche, sélectionnez le **C/C++** dossier.  
  
6.  Sous le **C++** dossier, sélectionnez `Optimization`.  
  
7.  Dans la liste des propriétés affichée à droite, recherchez `Optimization`. Le paramètre en regard de cette propriété indique probablement `Disabled (` [/Od](/cpp/build/reference/od-disable-debug)`)`. Choisissez une des autres options (`Minimum Size``(`[/O1](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Maximum Speed``(` [/O2](/cpp/build/reference/o1-o2-minimize-size-maximize-speed)`)`, `Full Optimization``(` [/Ox](/cpp/build/reference/ox-full-optimization) `)`, ou `Custom`).  
  
8.  Si vous avez choisi l'option `Custom` pour `Optimization`, vous pouvez maintenant définir des options pour l'une des autres propriétés affichées dans la liste des propriétés.  
  
9. Sélectionnez les propriétés de configuration, C/C++, nœud de la ligne de commande de la page de propriétés de projet et ajoutez `(` [/Zo](/cpp/build/reference/zo-enhance-optimized-debugging) `)` à la **des Options supplémentaires** zone de texte.  
  
    > [!WARNING]
    >  `/Zo` nécessite Visual Studio 2013 Update 3 ou une version ultérieure.  
    >   
    >  Ajout de `/Zo` désactivera [Modifier & Continuer](../debugger/edit-and-continue-visual-csharp.md).  
  
 Lorsque vous déboguez un code optimisé, utilisez le **code machine** fenêtre pour voir quelles instructions sont réellement créées et exécutées. Lorsque vous définissez des points d'arrêt, n'oubliez pas qu'ils peuvent se déplacer avec les instructions. Considérons par exemple le code suivant :  
  
```  
for (x=0; x<10; x++)  
```  
  
 Supposons que vous définissez un point d'arrêt sur cette ligne. Vous pouvez supposer que le point d'arrêt sera atteint 10 fois ; mais si le code est optimisé, il ne sera atteint qu'une seule fois. Cela est dû au fait que la première instruction affecte la valeur 0 à `x`. Le compilateur reconnaît que l'opération doit être effectuée une seule fois et la sort de la boucle. Le point d'arrêt est déplacé en même temps. Les instructions qui comparent et incrémentent `x` restent à l'intérieur de la boucle. Lorsque vous affichez la **code machine** fenêtre, le [unité d’étape](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9) est automatiquement définie sur Instruction pour un contrôle renforcé, ce qui est utile lorsque vous parcourez le code optimisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)