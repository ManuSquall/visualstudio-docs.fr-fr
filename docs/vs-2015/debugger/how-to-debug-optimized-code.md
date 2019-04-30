---
title: 'Procédure : Déboguer le Code optimisé | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- breakpoints, in optimized code
- debugging [C++], optimized code
- optimization, debug builds
- debug builds, optimizing
- optimized code, debugging
ms.assetid: fc8eeeb8-6629-4c9b-99f7-2016aee81dff
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 529fd979912d1743967109a11933140b482c2caf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435723"
---
# <a name="how-to-debug-optimized-code"></a>Procédure : déboguer du code optimisé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!NOTE]
> L’option de compilateur [/Zo (Améliorer le débogage optimisé)](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) (introduite dans Visual Studio Update 3) génère des informations de débogage plus détaillées pour le code optimisé (projets qui ne sont pas générés avec l’option de compilateur **/Od**. Consultez [Options /O (Optimiser le code)](http://msdn.microsoft.com/library/77997af9-5555-4b3d-aa57-6615b27d4d5d)). Cela inclut la prise en charge améliorée pour le débogage des variables locales et des fonctions inline.  
>   
> [Modifier et continuer](../debugger/edit-and-continue-visual-csharp.md) est désactivé quand l’option de compilateur **/Zo** est utilisée.  
  
 Lorsque le compilateur optimise le code, il repositionne et réorganise les instructions. Il permet ainsi d'obtenir un code compilé plus efficace. En raison de cette réorganisation, le débogueur ne peut pas toujours identifier le code source qui correspond à un jeu d'instructions.  
  
 L'optimisation peut affecter :  
  
- Les variables locales, qui peuvent être supprimées par l'optimiseur ou être déplacées vers des emplacements que le débogueur ne comprend pas.  
  
- Des positions à l'intérieur d'une fonction, qui sont modifiées lorsque l'optimiseur fusionne des blocs de code.  
  
- Les noms de fonctions pour les trames de la pile des appels, qui peuvent être erronés si l’optimiseur fusionne deux fonctions.  
  
  Les trames qui s'affichent sur la pile des appels sont presque toujours correctes, à condition toutefois que vous ayez des symboles pour toutes les trames. Les trames de la pile des appels seront incorrectes en cas d'altération de la pile, ou si certaines fonctions sont écrites en langage assembleur, ou encore s'il y a des trames de système d'exploitation sans correspondance avec les symboles figurant dans la pile des appels.  
  
  Les variables globales et statiques s'affichent toujours correctement. C'est également le cas pour les dispositions de structures. Si un pointeur désigne une structure et que la valeur de ce pointeur est correcte, chaque variable membre de la structure affichera la valeur correcte.  
  
  En raison de ces limitations, vous devez effectuer le débogage en utilisant si possible une version non optimisée de votre programme. Par défaut, l’optimisation est désactivée dans la configuration Debug d’un programme Visual C++ et activée dans la configuration Release.  
  
  Mais un bogue peut apparaître uniquement dans une version optimisée d'un programme. Dans ce cas, vous devez déboguer le code optimisé.  
  
### <a name="to-turn-on-optimization-in-a-debug-build-configuration"></a>Pour activer l'optimisation dans une configuration de build Debug  
  
1. Lorsque vous créez un projet, sélectionnez la cible `Win32 Debug`. Utilisez la cible `Win32``Debug` jusqu’à ce que votre programme soit entièrement débogué et que vous soyez prêt à générer une cible `Win32 Release`. Le compilateur n'optimise pas la cible `Win32 Debug`.  
  
2. Sélectionnez le projet dans l’Explorateur de solutions.  
  
3. Dans le menu **vue**, cliquez sur **Pages de propriétés**.  
  
4. Dans la boîte de dialogue **Pages de propriétés**, vérifiez que `Debug` est sélectionné dans la liste déroulante **Configuration**.  
  
5. Dans la vue Dossiers sur le côté gauche, sélectionnez le dossier **C/C++**.  
  
6. Sous le dossier **C++**, sélectionnez `Optimization`.  
  
7. Dans la liste des propriétés affichée à droite, recherchez `Optimization`. Le paramètre en regard de la propriété indique probablement `Disabled (`[/Od](http://msdn.microsoft.com/library/b1ac31b7-e086-4eeb-be5e-488f7513f5f5)`)`. Sélectionnez une des autres options (`Minimum Size``(`[/O1](http://msdn.microsoft.com/library/2d1423f5-53d9-44da-8908-b33a351656c2)`)`, `Maximum Speed``(`[/O2](http://msdn.microsoft.com/library/2d1423f5-53d9-44da-8908-b33a351656c2)`)`, `Full Optimization``(`[/Ox](http://msdn.microsoft.com/library/3ad7c30b-c615-428c-b1d0-2e024f81c760)`)` ou `Custom`).  
  
8. Si vous avez choisi l'option `Custom` pour `Optimization`, vous pouvez maintenant définir des options pour l'une des autres propriétés affichées dans la liste des propriétés.  
  
9. Sélectionnez les propriétés de Configuration, C/C++, nœud de ligne de commande de la page de propriétés de projet et ajoutez `(` [/Zo](http://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) `)` à la **des Options supplémentaires** zone de texte.  
  
    > [!WARNING]
    > `/Zo` nécessite Visual Studio 2013 Update 3 ou une version ultérieure.  
    >   
    >  Ajouter `/Zo` désactive [Modifier & Continuer](../debugger/edit-and-continue-visual-csharp.md).  
  
   Quand vous déboguez du code optimisé, examinez la fenêtre **Code Machine** pour voir quelles instructions sont réellement créées et exécutées. Lorsque vous définissez des points d'arrêt, n'oubliez pas qu'ils peuvent se déplacer avec les instructions. Considérons par exemple le code suivant :  
  
```  
for (x=0; x<10; x++)  
```  
  
 Supposons que vous définissez un point d'arrêt sur cette ligne. Vous pouvez supposer que le point d'arrêt sera atteint 10 fois ; mais si le code est optimisé, il ne sera atteint qu'une seule fois. Cela est dû au fait que la première instruction affecte la valeur 0 à `x`. Le compilateur reconnaît que l'opération doit être effectuée une seule fois et la sort de la boucle. Le point d'arrêt est déplacé en même temps. Les instructions qui comparent et incrémentent `x` restent à l'intérieur de la boucle. Quand vous affichez la fenêtre **Code Machine**, l’[unité de progression](http://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) est automatiquement définie sur Instruction pour un contrôle renforcé, ce qui est utile quand vous exécutez le code optimisé pas à pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code natif](../debugger/debugging-native-code.md)
