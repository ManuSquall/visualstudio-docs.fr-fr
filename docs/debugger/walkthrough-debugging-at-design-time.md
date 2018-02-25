---
title: "Débogage au moment du Design - Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 02/21/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 33e0210023de05047957e7fbf55a8f970fda19d9
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="debug-at-design-time-in-visual-studio"></a>Débogage au moment du Design dans Visual Studio

Dans certains scénarios, vous souhaiterez déboguer du code lors de la conception de temps au lieu de pendant l’exécution de l’application. Ce faire, vous pouvez utiliser la **exécution** fenêtre. Si vous souhaitez déboguer du code XAML qui interagit avec un autre code, tel que le code de liaison de données, vous pouvez utiliser **déboguer** > **attacher au processus** à cet effet.
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>Débogage au moment du design à l’aide de la fenêtre exécution  

Vous pouvez utiliser Visual Studio **exécution** fenêtre pour exécuter une fonction ou une sous-routine pendant que votre application n’est pas en cours d’exécution. Si la fonction ou la sous-routine contient un point d’arrêt, Visual Studio interrompt l’exécution au point approprié. Vous pouvez ensuite utiliser les fenêtres du débogueur pour examiner l’état de votre programme. Cette fonctionnalité est appelée débogage au moment du design.  

L’exemple suivant est en Visual Basic, mais la **exécution** fenêtre est également pris en charge dans les applications c# et C++.
  
1.  Collez le code suivant dans une application console Visual Basic :  
  
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
  
5.  Sur le **déboguer** menu, cliquez sur **continuer**et vérifiez que vous êtes toujours en mode Création.  
  
6.  Tapez la commande suivante dans le **exécution** fenêtre : `?MyFunction<enter>`  
  
7.  Tapez la commande suivante dans le **exécution** fenêtre : `?MySub<enter>`  
  
8.  Vérifiez que vous atteignez le point d’arrêt et examinez la valeur de la variable statique `i` dans les **variables locales** fenêtre. Il doit avoir la valeur 3.  
  
9. Vérifiez que la pile des appels est exacte.  
  
10. Sur le **déboguer** menu, cliquez sur **continuer**et vérifiez que vous êtes toujours en mode Création.  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>Débogage au moment du design du concepteur XAML

Il peut être utile déboguer le code-behind à partir du concepteur XAML dans certains scénarios de liaison de données déclarative.

1. Dans votre projet, ajoutez une nouvelle page XAML, tel que *temp.xaml*. Renseigner la nouvelle page XAML. 

1. Compilez votre solution.

1. Ouvrez *temp.xaml*, ce qui charge le concepteur (*UwpSurface.exe* dans une application UWP, ou *XDesProc.exe*) afin que vous pouvez attacher à celui-ci dans les étapes ultérieures. 

1. Ouvrez une nouvelle instance de Visual Studio. Dans la nouvelle instance, ouvrez le **attacher au processus** boîte de dialogue (**déboguer** > **attacher au processus**), définissez la **attacher à** champ au type de code approprié, tel que **le Code managé (CoreCLR)** ou le type de code correct en fonction de votre version de .NET. Sélectionnez le processus de concepteur approprié dans la liste, choisissez **attacher**.

    Pour la plateforme Windows universelle projets ciblant générer 16299 ou ci-dessus, le processus du concepteur est *UwpSurface.exe*. Pour WPF ou les versions antérieures à 16299 de plateforme Windows universelle, le processus de concepteur est *XDesProc.exe*.

1. Alors qu’attaché au processus, basculez vers votre projet, ouvrez le code-behind dans lequel vous voulez déboguer et définir un point d’arrêt.

1. Enfin, ouvrez la page qui contient le code XAML qui inclut la liaison de données.

    Par exemple, vous pouvez définir un point d’arrêt dans le code de convertisseur de type pour le code XAML suivant, qui lie un contrôle TextBlock au moment du design.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Lors du chargement de la page, le point d’arrêt est atteint.
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Principes de base du débogueur](../debugger/debugger-basics.md)
