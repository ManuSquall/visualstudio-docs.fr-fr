---
title: Débogueur du nuanceur HLSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.shaderviewer
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bef6c5a742c4bf6acc15a6326190686e46fef79b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410184"
---
# <a name="hlsl-shader-debugger"></a>Débogueur du nuanceur HLSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogueur HLSL de Visual Studio Graphics Analyzer vous aide à comprendre comment votre code de nuanceur HLSL s'exécute dans les conditions réelles de fonctionnement de votre application.  
  
 Il se présente comme suit :  
  
 ![Débogage à l’aide du langage HLSL Regardez et pile des appels. ](../debugger/media/gfx-diag-demo-hlsl-debugger-orientation.png "gfx_diag_demo_hlsl_debugger_orientation")  
  
## <a name="understanding-the-hlsl-debugger"></a>Présentation du débogueur HLSL  
 Le débogueur HLSL peut vous aider à comprendre les problèmes qui surviennent dans votre code de nuanceur. Le débogage du code HLSL dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ressemble au débogage du code écrit dans un autre langage, par exemple, C++, C# ou Visual Basic. Vous pouvez examiner le contenu des variables, définir des points d'arrêt, parcourir le code, et remonter la pile d'appels, comme lorsque vous déboguez d'autres langages.  
  
 Toutefois, comme les GPU atteignent des performances élevées via l'exécution du code de nuanceur sur des centaines de threads simultanément, le débogueur HLSL est conçu pour collaborer avec les autres outils Graphics Analyzer pour afficher toutes ces informations et en faciliter le décryptage. Graphics Analyzer recrée les frames capturés en utilisant les informations stockées dans un journal de graphisme. Le débogueur HLSL ne contrôle pas l'exécution du GPU en temps réel quand il exécute le code d'un nuanceur. Dans la mesure où un journal de graphisme contient suffisamment d'informations pour recréer une partie de la sortie, et où Graphics Analysis fournit des outils permettant de désigner exactement le pixel et l'événement précis où se produit une erreur, le débogueur HLSL doit simplement simuler le thread nuanceur qui vous intéresse. Cela signifie que le travail du nuanceur peut être simulé sur l'UC, où les mécanismes internes sont affichés en plein écran. Cela permet au débogueur HLSL de bénéficier d'une expérience de débogage similaire à celle de l'UC.  
  
 Toutefois, le débogueur HLSL est actuellement limité comme suit :  
  
- Le débogueur HLSL ne prend pas en charge l'option Modifier &amp; Continuer. Toutefois, vous pouvez apporter des changements à vos nuanceurs et régénérer ensuite le frame pour voir les résultats.  
  
- Il est impossible de déboguer une application et son code de nuanceur simultanément. Toutefois, vous pouvez les alterner.  
  
- Vous pouvez ajouter des variables et des registres à la fenêtre Espion, mais les expressions ne sont pas prises en charge.  
  
  Néanmoins, le débogueur HLSL offre une expérience de débogage meilleure et plus similaire à celle de l'UC.  
  
## <a name="hlsl-shader-edit--apply"></a>Modification et application du nuanceur HLSL  
 Le débogueur du nuanceur HLSL ne prend pas en charge Modifier & Continuer de la même manière que le débogueur de CPU, car le modèle d'exécution du GPU n'autorise pas l'annulation de l'état du nuanceur. À la place, le débogueur HLSL prend en charge Modifier & Appliquer, ce qui vous permet de changer les fichiers sources HLSL, puis de choisir **Appliquer** pour régénérer le frame et voir le résultat de vos changements. Votre code de nuanceur modifié est stocké dans un fichier distinct pour préserver l’intégrité du fichier de source HLSL d’origine de votre projet, mais lorsque vous êtes satisfait de vos modifications, vous pouvez choisir **copier dans...** Pour copier les modifications dans votre projet. À l’aide de cette fonctionnalité, vous pouvez rapidement itérer le code du nuanceur qui contient des erreurs, et éliminer les étapes coûteuses de régénération et de capture dans votre flux de travail de débogage HLSL.  
  
## <a name="hlsl-disassembly"></a>Code machine HLSL  
 Le débogueur du nuanceur HLSL fournit une liste d'assemblys du nuanceur HLSL à droite de la liste de codes source HLSL.  
  
## <a name="debugging-hlsl-code"></a>Débogage du code HLSL  
 Vous pouvez accéder au débogueur HLSL à partir de la fenêtre Étapes de canalisation ou Historique des pixels.  
  
#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pipeline-stages-window"></a>Pour démarrer le débogueur HLSL à partir de la fenêtre Étapes de canalisation Graphics  
  
1. Dans la fenêtre **Étapes de canalisation Graphics**, recherchez l’étape de pipeline associée au nuanceur que vous souhaitez déboguer.  
  
2. Sous le titre de l’étape de pipeline, choisissez **Démarrer le débogage**, qui apparaît sous la forme d’une petite flèche verte.  
  
    > [!NOTE]
    > Ce point d'entrée dans le débogueur HLSL débogue uniquement le premier thread nuanceur pour l'étape correspondante, c'est-à-dire le premier vertex ou le premier pixel qui est traité. Vous pouvez utiliser la fonctionnalité Historique des pixels pour accéder à d'autres threads de ces étapes du nuanceur.  
  
#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pixel-history"></a>Pour démarrer le débogueur HLSL de l'historique des pixels Graphics  
  
1. Dans la fenêtre **Historique des pixels Graphics**, développez l’appel de dessin associé au nuanceur que vous souhaitez déboguer. Chaque appel de dessin peut correspondre à plusieurs primitives.  
  
2. Dans les détails de l’appel de dessin, développez une primitive dont la contribution de couleur résultante indique un bogue dans son code shader. Si plusieurs primitives indiquent un bogue, choisissez la première afin d'éviter une accumulation d'erreurs pouvant rendre le diagnostic du problème plus difficile.  
  
3. Dans les détails de primitives, choisissez de déboguer le **Nuanceur de sommets** ou le **Nuanceur de pixels**. Déboguez le nuanceur de sommets lorsque vous suspectez que le nuanceur de pixels est correct mais qu'il génère une proportion incorrecte de couleur car le nuanceur de sommets lui passe des constantes incorrectes. Sinon, déboguez le nuanceur de pixels.  
  
    À droite du nuanceur choisi, choisissez **Démarrer le débogage**, qui apparaît sous la forme d’une petite flèche verte.  
  
   > [!NOTE]
   > Ce point d'entrée dans le débogueur HLSL débogue soit le thread nuanceur de pixels qui correspond à l'appel de dessin choisi, à la primitive, et au pixel que vous avez choisis, soit les threads de nuanceur de sommets dont les résultats sont interpolés par l'appel de dessin, la primitive, et le pixel que vous avez choisis. Dans le cas des nuanceurs de sommets, vous pouvez affiner davantage le point d’entrée à un sommet spécifique en développant les détails du nuanceur de sommets.  
  
   Pour obtenir des exemples sur la façon d’utiliser le débogueur HLSL pour déboguer les erreurs de nuanceur, consultez [exemples](../debugger/graphics-diagnostics-examples.md) ou les procédures pas à pas liées dans la section Voir aussi.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : objets manquants en raison de Vertex Shader](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Procédure pas à pas : débogage des erreurs de rendu dues à l’ombrage](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)   
 [Procédure pas à pas : utilisation de Graphics Diagnostics pour déboguer un nuanceur de calcul](../debugger/walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)
