---
title: Déboguer au moment du Design - Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 452b4045357db12c4b4cff1a5b6e27035cf85d82
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257197"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Déboguer au moment du Design dans Visual Studio (C#, C++, Visual Basic, F#)

Dans certains scénarios, vous souhaiterez déboguer du code lors de la conception de temps au lieu de pendant l’exécution de l’application. Vous pouvez le faire à l’aide de la **immédiat** fenêtre. Si vous souhaitez déboguer du code XAML qui interagit avec un autre code, tel que le code de liaison de données, vous pouvez utiliser **déboguer** > **attacher au processus** pour ce faire.
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>Déboguer au moment du design à l’aide de la fenêtre exécution  

Vous pouvez utiliser Visual Studio **immédiat** fenêtre pour exécuter une fonction ou une sous-routine pendant que votre application n’est pas en cours d’exécution. Si la fonction ou une sous-routine contient un point d’arrêt, Visual Studio s’arrête l’exécution au point approprié. Vous pouvez ensuite utiliser les fenêtres du débogueur pour examiner l’état de votre programme. Cette fonctionnalité est appelée débogage au moment du design.  

L’exemple suivant est en Visual Basic. Utilisation de la **immédiat** fenêtre au moment du design est également pris en charge dans C#, C++, et F# applications.
  
1.  Collez le code suivant dans une application de console Visual Basic :  
  
    ```vb  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Définissez un point d’arrêt sur la ligne qui lit, `s="Add BreakPoint Here"`.  
  
3.  Ouvrez le **immédiat** fenêtre (**déboguer** > **Windows** > **immédiat**) et tapez la commande suivante dans le fenêtre : `?MyFunction<enter>`  
  
4.  Vérifiez que le point d’arrêt a été atteint et que la pile des appels est exacte.  
  
5.  Sur le **déboguer** menu, cliquez sur **continuer**et vérifiez que vous êtes toujours en mode de conception.  
  
6.  Tapez la commande suivante dans le **immédiat** fenêtre : `?MyFunction<enter>`  
  
7.  Tapez la commande suivante dans le **immédiat** fenêtre : `?MySub<enter>`  
  
8.  Vérifiez que vous atteignez le point d’arrêt et examinez la valeur de la variable statique `i` dans le **variables locales** fenêtre. Il doit avoir la valeur de 3.  
  
9. Vérifiez que la pile des appels est exacte.  
  
10. Sur le **déboguer** menu, cliquez sur **continuer**et vérifiez que vous êtes toujours en mode de conception.  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>Déboguer au moment du design à partir du concepteur XAML

Il peut être utile déboguer le code-behind à partir du concepteur XAML dans certains scénarios de liaison de données déclarative.

1. Dans votre projet, ajoutez une nouvelle page XAML, tel que *temp.xaml*. La nouvelle page XAML laissez vide. 

1. Compilez votre solution.

1. Ouvrez *temp.xaml*, ce qui charge le concepteur (*UwpSurface.exe* dans une application UWP, ou *XDesProc.exe*) afin que vous pouvez attacher à celui-ci dans les étapes ultérieures. 

1. Ouvrez une nouvelle instance de Visual Studio. Dans la nouvelle instance, ouvrez le **attacher au processus** boîte de dialogue (**déboguer** > **attacher au processus**), définissez la **attacher à** champ pour le type de code approprié, tel que **du Code managé (CoreCLR)** ou le type de code correcte en fonction de votre version de .NET. Sélectionnez le processus du concepteur correct dans la liste et choisissez **attacher**.

    Pour UWP, les projets ciblant le build 16299 ou versions ultérieures, le processus du concepteur est *UwpSurface.exe*. Pour WPF ou les versions de UWP antérieures à 16299, le processus du concepteur est *XDesProc.exe*.

1. Même si attaché au processus, basculez vers votre projet, ouvrez le code-behind où vous souhaitez déboguer et définir un point d’arrêt.

1. Enfin, ouvrez la page qui contient le code XAML qui inclut la liaison de données.

    Par exemple, vous pouvez définir un point d’arrêt dans le code de convertisseur de type pour le XAML suivant, qui lie un bloc de texte au moment du design.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Lorsque la page se charge, le point d’arrêt est atteint.
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Principes de base du débogueur](../debugger/getting-started-with-the-debugger.md)
