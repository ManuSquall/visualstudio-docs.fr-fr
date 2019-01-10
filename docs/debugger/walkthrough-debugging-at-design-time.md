---
title: Déboguer au moment du design | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
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
ms.openlocfilehash: c367176a6e05b394449fbd78dabc0e863b43c2b5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960010"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Déboguer au moment du design dans Visual Studio (C#, C++, Visual Basic, F#)

Pour déboguer le code au moment du design au lieu de lors d’une application est en cours d’exécution, vous pouvez utiliser la **immédiat** fenêtre. 

Pour déboguer le code XAML derrière une application à partir du concepteur XAML, tel que le code de liaison de données, vous pouvez utiliser **déboguer** > **attacher au processus**.
  
## <a name="use-the-immediate-window"></a>Utiliser la fenêtre exécution  

Vous pouvez utiliser Visual Studio **immédiat** fenêtre pour exécuter une fonction ou une sous-routine sans exécuter votre application. Si la fonction ou une sous-routine contient un point d’arrêt, Visual Studio s’arrête au point d’arrêt. Vous pouvez ensuite utiliser les fenêtres du débogueur pour examiner l’état de votre programme. Cette fonctionnalité est appelée *débogage au moment du design*.  

L’exemple suivant est en Visual Basic. Vous pouvez également utiliser le **immédiat** fenêtre au moment du design dans C#, F#et les applications C++.

1. Collez le code suivant dans une application de console Visual Basic vide :  
   
   ```vb  
   Module Module1
   
       Sub Main()
           MySub()
       End Sub
   
       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function
   
       Sub MySub()
           MyFunction()
   
       End Sub
   End Module
   ```  
   
1. Définissez un point d’arrêt sur la ligne **End Function**.  
   
1. Ouvrez le **immédiat** en sélectionnant **déboguer** > **Windows** > **immédiat**. Type `?MyFunction` dans la fenêtre, puis appuyez sur **entrée**.   
   
   Le point d’arrêt est atteint et la valeur de **MyFunction** dans le **variables locales** fenêtre est **1**. Vous pouvez examiner la pile des appels et les autres fenêtres de débogage pendant que l’application est en mode arrêt. 
   
1. Sélectionnez **continuer** sur la barre d’outils de Visual Studio. L’application se termine, et **1** est retourné dans le **immédiat** fenêtre. Vérifiez que vous êtes toujours en mode de conception.  
   
1. Type `?MyFunction` dans le **immédiat** fenêtre à nouveau, puis appuyez sur **entrée**. Le point d’arrêt est atteint et la valeur de **MyFunction** dans le **variables locales** fenêtre est **2**. 
   
1. Sans sélectionner **continuer**, type `?MySub()` dans le **immédiat** fenêtre, puis appuyez sur **entrée**. Le point d’arrêt est atteint et la valeur de **MyFunction** dans le **variables locales** fenêtre est **3**. Vous pouvez examiner l’état de l’application pendant que l’application est en mode arrêt. 
   
1. Sélectionnez **continuer**. Le point d’arrêt est atteint à nouveau et la valeur de **MyFunction** dans le **variables locales** fenêtre est désormais **2**. Le **immédiat** fenêtre retourne **Expression a été évaluée et n’a aucune valeur**.
   
1. Sélectionnez **continuer** à nouveau. L’application se termine, et **2** est retourné dans le **immédiat** fenêtre. Assurez-vous que vous êtes toujours en mode de conception.
   
1. Pour effacer le contenu de la **immédiat** fenêtre, avec le bouton droit dans la fenêtre et sélectionnez **Effacer tout**. 

## <a name="attach-to-an-app-from-the-xaml-designer"></a>Attacher à une application à partir du concepteur XAML

Dans certains scénarios de liaison de données déclarative, il peut vous aider à déboguer le code-behind dans le concepteur XAML.

1. Dans le projet de Visual Studio, ajoutez une nouvelle page XAML, tel que *temp.xaml*. La nouvelle page XAML laissez vide. 
   
1. Générez la solution.
   
1. Ouvrez *temp.xaml*, ce qui charge le concepteur XAML, *XDesProc.exe*, ou *UwpSurface.exe* dans une application UWP. 
   
1. Ouvrez une nouvelle instance de Visual Studio. Dans la nouvelle instance, sélectionnez **déboguer** > **attacher au processus**. 
   
1. Dans le **attacher au processus** boîte de dialogue, sélectionnez le Concepteur de traiter à partir de la **processus disponibles** liste.
   
   Pour UWP projets ciblant Windows build 16299 ou version ultérieure, le processus du concepteur est *UwpSurface.exe*. Pour les versions antérieures à 16299 WPF ou UWP, le processus du concepteur est *XDesProc.exe*.
   
1. Assurez-vous que le **attacher à** champ est défini sur le type de code approprié pour votre version de .NET, tel que **du Code managé (CoreCLR)**. 
   
1. Sélectionnez **attacher**.
   
1. Même si attaché au processus, basculez vers l’autre instance de Visual Studio et définissez des points d’arrêt dans lequel vous souhaitez déboguer le code-behind de votre application.
   
   Par exemple, vous pouvez définir un point d’arrêt dans le code de convertisseur de type pour le XAML suivant, qui lie un bloc de texte au moment du design.
   
    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Lorsque la page se charge, le point d’arrêt est atteint.
  
## <a name="see-also"></a>Voir aussi  
 [Tout d’abord examiner le débogueur](../debugger/debugger-feature-tour.md) [sécurité du débogueur](../debugger/debugger-security.md)   